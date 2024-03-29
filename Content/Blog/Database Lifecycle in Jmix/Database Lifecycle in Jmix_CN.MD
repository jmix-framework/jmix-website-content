## Jmix 中的数据库生命周期

Jmix 中使用了 JPA 数据模型，因为数据库是应用程序的基石。

## 介绍

Jmix 中使用了 JPA 数据模型，因为数据库是应用程序的基石。

在软件开发方面，“如果它能用，就不要碰它” 的规则并不总是可行。软件的更改是不可避免的，数据库迁移也是如此。如果数据库更新出现错误，你可能丢失数据，而数据是业务中最具价值的东西。

在我们的框架中，使用了 JPA 来处理关系型数据库。当今，关系型数据库在企业级应用程序中被广泛使用，促使其取得巨大成功的因素主要有两点：数据一致性（在很多业务领域这很重要）以及许多类似于 Hibernate 或 EclipseLink 的高级 ORM 框架简化了应用程序开发。

对关系型数据库进行更新是一项复杂的工作，我们需要保证数据在迁移前后的一致性，但是要做到这一点并不容易。

在 [前一篇文章](https://www.jmix.cn/blog/database-lifecycle-in-jmix-migration-challenges) 中，我们对 Jmix 中的数据库迁移处理做了一个概括性介绍。在这篇文章中，我们会更深入地探讨一下数据库迁移过程的各种挑战。

## 数据库迁移的各种极端情况

在 “ [Refactoring Databases: Evolutionary Database Design](https://www.amazon.com/Refactoring-Databases-Evolutionary-paperback-Addison-Wesley/dp/0321774515/) ” 这本书中列举了超过 20 种数据库变更的案例。其中的一些非常危险，可能导致丢失数据。

当然，你可以识别出危险的重构，比如删除某些东西的操作。在 Jmix 中我们使用红色高亮显示出包含删表、删列等危险操作的数据库迁移脚本。

然而，有些数据库更新的案例看似安全，可是实际在数据模型重构时可能导致问题。

在 Jmix 中，我们使用 Liquibase 进行 DB 版本控制，所以我们在文章中将使用此工具作为参考。

## 删除表/列

虽然这个操作会直接导致数据丢失，但是你可以遵守 “do not drop, rename(不要删除，而是重命名)” 建议来避免损失。

在 “Refactoring Databases: Evolutionary Database Design”  这本书里，作者几乎总是使用 “Transition period (过渡期)” - 将数据对象保留一段时间，但不使用。如果数据库迁移失败，那么我们将有机会去修复问题。 比如，这里有一个"[删除列](https://databaserefactoring.com/RemoveColumn.html)" 的典型案例:

![text]({{strapiUrl}}/uploads/blog_img_ca57c30139.png)

## 重命名表

类重命名是一个常见的操作，但是在对数据模型类重命名时会导致 DB 表名也改变，特别是我们没有使用 `@Table` 注解指定表名时。

Liquibase 将会为此操作创建 [rename table](https://docs.liquibase.com/change-types/community/rename-table.html) 语句。这通常是无害的，虽然这个操作可能会锁住整个表。在生产环境需要格外留意这个操作，避免锁表引起应用长时间不响应。

重命名表时潜在的问题不仅是锁表，应用代码中的 SQL/JPQL 查询语句也可能受影响。我们需仔细审查这种情况，因为字符串引用比代码引用更难跟踪，即便用了 IDE。

对这种代码进行审查可以让我们避免最麻烦的错误 - 运行时异常。

## 重命名列

对于现代化的 IDE 来说，重命名类属性是一个简单的操作。如果我们没有为属性指定列名，那么这种操作可能导致重命名对应的数据库列。

与重命名表名一样，如果我们修改类属性名（即需要修改 DB 列名），那第我们必须审查所有相关的查询(SQL or JPQL) 以确保安全。

对于重命名属性操作， Liquibase 工具将生成 “rename column” 语句。大部分数据库([见 Liquibase 参考](https://docs.liquibase.com/change-types/community/rename-column.html)) 支持直接重命名列的操作。

在 Jmix 中，我们仍然生成 “drop column + add column” 的 Liquibase 变更集（changeset） 。然后，我们需要按照以下操作顺序来执行更新：

- 添加一个临时列
- 将要改名的列的数据复制到临时列
- 删除列
- 使用新列名创建列
- 从临时列将数据拷贝到新列
- 删除临时列

这有助于避免列数据丢失。


## 修改 One-To-Many 关系为使用关联表


我们先看看案例 - 我们需要存储汽车和车主信息。这是初始模型：

![text]({{strapiUrl}}/uploads/blog_img_2_6b6243fe7f.png)


一段时间后，我们发现需要记录汽车-车主关系历史。如果要存储关系历史，通常需要通过改变关系基数（cardinality）来实现。我们的模型会修改成这样：


![text]({{strapiUrl}}/uploads/blog_img_3_1f173724a3.png)

使用 Jmix Studio，改变基数比较容易，只需要在实体设计器中点几次鼠标，但是在数据库级别会产生较多更改。Jmix Studio 生成下列变更集（changeset）：

-  创建关联表
-  生成两个实体的外键

Studio 不会移除现有表中的任何外键列，这里我们需要手工处理。这个案例中， `person_id` 会保留在 `Car` 表。  

需要注意的是，Jmix 不会迁移两个实体间的已有链接信息。如果我们需要保留这这些信息，那么就需要使用 update 脚本来迁移数据。 

在使用关联表替换 many-to-one 关系时， 最终的更新集应包含下列步骤：

- 创建关联表
- 在关系表中创建两个实体的外键
- 从两个表提取数据并插入到关联表
- 从原表中删除多余的外键

这样，你就可以将实体关系历史保存到新的关联表。

## 修改数据类型

数据类型的修改非常少见，在大部分情况下，数据类型在模型设计阶段就可以确定。但是总有例外，使我们不得不做此修改。

比如，我们针对美国市场开发了一个非常好的货运跟踪系统。在美国，邮编可以使用 9 位数字（格式为：ddddd-dddd）来表示。系统运行良好，并且准备在英国也使用这套系统。但是在英国，邮编中可能包含字母，比如 “SW1 4HY”。这意味着我们不能使用数字来存储邮编，而应该使用字符串。 
 
修改类属性的数据类型不存在大的问题，因为 IDE 和编译器可以在早期检测出几乎所有问题。但是迁移数据会是一个挑战。

通常，我们不能直接将一个数据类型转换成其它类型。在 Jmix 中，我们生成两个操作：“drop column” 和 “add column” 。如果你直接应用这些操作，可能会丢失数据。要避免这个问题，可按照 "重命名列" 部分介绍的步骤来处理。

## 标记列为不允许使用 null 

这个变更不会导致数据丢失，但是如果列包含 null 值则可能导致整个数据库更新处理失败。在这种情况下，我们需要更新列并添加默认值 。

Jmix 仅为这种更改生成约束，你需要修改生成的脚本来为列中的 null　值指定默认值属性：`defaultNullValue` 。

还有一个方法，通过在变更集中设置 `validate` 属性来避免对已有数据进行检查。在使用这个方法前我们应该先确认 RDBMS 是否支持此功能。可以从 [Liquibase 文档](https://docs.liquibase.com/change-types/community/add-not-null-constraint.html) 了解更多细节。

## 添加唯一约束

给表添加约束（不允许为空、唯一约束或其它）会引入潜在的导致数据库更新处理失败的因素。问题在于很多时候我们无法对要更新的所有类型的数据库和数据集进行检查。

如果我们决定为表添加唯一约束，我们可以在 Jimx Studio 中设置对应类属性的属性或在可视化设计器中创建一个唯一索引 。

Jmix 将生成一个基本的 `addUniqueConstraint` Liquibase 变更集。如果我们没有要更新的数据库的详细信息，我们可以在变更集中添加 `validate` 属性来避免更新时的数据库约束检查。

对于一些 RDBMS ，如果我们将 `validate` 设置为　`false`，唯一约束将只应用到新创建的记录，旧数据不会被验证。如果我们将 `validate` 设置为　`true` ，如果存在非唯一数据，更新将失败。

比如，使用 [一些技巧](https://stackoverflow.com/a/42903246/3136181) 可以使 Oracle 支持此模式。但是 PostgreSQL 不支持。我们需要参考数据库文档来使用这个选项。

如果 DB 不支持延迟的约束验证，我们只能先更新数据，再应用索引。

笨拙一点的方法是，我们需要找到所有非唯一记录，然后逐个手工更新。我们需要为应用提供一个清晰的数据库迁移说明，DB 管理员应该根据这个说明来更新数据。

但如果我们想自动化一些，可以创建一个简单的 update SQL 语句，为现有数据的那些将来会用作唯一约束的列增加一个唯一的后缀。这个 SQL 语句可以添加到 liquibase 变更集中。这个方法更简单一点，但是在某些场景中更新数据也许并不是一个好方法。

所以，添加唯一约束并不是简单地执行 `ALTER TABLE` 语句，这里可能涉及到一些业务规则。我们可以使用上述方法来解决这个问题。

## 总结

数据库迁移是一个复杂的处理。即使使用现代化的工具和框架，比如 Liquibase 和 Jmix ，你也可能遇到数据丢失或应用程序运行时错误的问题。希望这篇文章能帮助你避免一些麻烦。

