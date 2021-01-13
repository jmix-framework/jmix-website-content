## 重点内容

Jmix 是 CUBA 平台的新名称，也是一个重要的发行版。它目前处于预览阶段，我们计划 2021 年二季度发布稳定版。
主要特性：

-   基于 Spring Boot
-   分解为独立的模块(数据、安全、审计等)
-   新的数据模型定义方式
-   基于 Liquibase 的 DB 更新机制
-   充分利用 Spring Boot 的部署功能，更好地与云环境集成

将来的 UI 开发主要基于 ReactJS 框架，但是我们会保留基于 Vaadin 的 UI 作为备选方案。

CUBA 平台会得到很长时间的支持，同时我们也通过兼容 API 的方式提供 CUBA 到 Jmix 的迁移路径。

访问 [jmix.io](https://www.jmix.io/) 了解 Jmix。在专门的[论坛分类](https://forum.cuba-platform.cn/c/jmix/)讨论 Jmix。

<a href="http://jmix.io" class="button">获取 jmix.io</a> <a href="https://forum.cuba-platform.cn/c/jmix/" class="button forum" style="background: #6c5ce7!important; margin-left:30px;">欢迎讨论</a>

## 介绍

CUBA 始于 2008 年，此后经历了几个非常重要的阶段。最初，它是一个内部框架，文档匮乏、只提供很少的 API。只用于 Haulmont 公司内部，使公司能够更快地开发业务应用程序。

2015 年，CUBA 使用一个专有许可在世界范围内发布。那年我们只获得了很少几个用户 - 这相当尴尬。很明显，许可策略应该切换到开源。

2016 - 2017 年是非常富有成效的两年，我们获得了广泛的社区支持。这是一个很大的转变，我们找到了正确的方法。

2018 - 2019 年，我们将文档和 API 提升到了一个新的层次，提供了清晰的 API、完善的文档。同时将 CUBA Studio 迁移到 IntelliJ。所有这些变化带来了更大的社区和更多的反馈。现在，我们处在下一个重要变化的起点。让我们深入了解一下 2021 年会发生什么。

## 新版本目标

我们计划在 CUBA 平台的下一个版本中达到以下目标：

1. 使开发人员的体验更接近当下流行的框架。CUBA 平台使用 Spring，但如今 Spring Boot 几乎征服了整个世界。新的框架也在出现 - Micronaut 、Quarkus。它们都具有相似的核心理念：通过 .properties 或 .yaml 简化配置、广泛使用注解以及简单的插件接入和配置。我们希望 CUBA 为开发人员提供类似的体验。

2. 不重复造轮子。自 2008 年以来，已经发展出了许多新的库和工具，现在它们已经很成熟，可以用于企业级应用程序。因此，我们想用经过实践检验的库替换一些自定义 CUBA 的模块，比如数据库迁移系统。

3. 给 CUBA 应用程序瘦身。使用 CUBA 创建应用程序时，会引入一些不必要的功能，比如数据审计功能，如果你的项目用不到，但它又是核心框架的组成部分，我们不能将其排除。这会给数据库带来不必要的表、在服务器上启动额外的服务。因此，能按需加载一些功能会更好。

4. 另外一个最重要的目标 - 舒适的开发体验和开发速度。

我们要聊的第一件事情...

## 名称

“CUBA 代表什么?” - 这个问题已经被问了无数次。坦白地说，这是在 2008 年我们开发 CUBA 平台时随意选择的一个包名，只是因为它不长也不短。如果你深入探索一下 CUBA 源码, 你会发现多个类似的包名：“chile” 和 “bali”。

在 2021 年我们要发布一个新重大版本，框架的名称将会改变。从 "CUBA" 变为 “Jmix”。 这个名称解释起来更简单：“J” 表示 “Java”，“mix” 表示多种技术和框架混合在一个应用程序。这样就少了很多问题，在全球范围不会再与著名的岛屿名、国家名（古巴）混淆。在中国不会和中国大学生篮球联赛混淆，这很重要，如果你在百度上搜索 CUBA ，你会发现前几页全是关于篮球的链接，我们的框架再棒、内容再好，也很难排到第一页。

实际上，Jmix 是保留了熟悉的 API 和开发方法的下一个主要 CUBA 版本。它仍然是同一套便捷的工具和代码生成器。

但是重命名是很重要的一件事情，它也表示其中包含了重要的变化...

## 基础架构

广义上讲，在 CUBA 时代我们重复了一些 Spring Boot 做的事情 。比如我们自己实现的会话存储、安全子系统、身份验证、程序部署等等。也设计了 CUBA 扩展（addon）机制，这个机制有自己封装格式、自动配置机制。 CUBA 扩展实际上相当于 Boot Starter。

当我们在 2008 年开始进行 CUBA 开发时，我们使用 “纯” Spring 作为核心技术。在 Jmix 中，我们将使用 Spring Boot 作为我们的核心技术。

使用 Spring Boot 有以下好处：

1. 开发人员经验。现在几乎每个 Java 开发者都熟悉 Spring Boot。Spring Boot 的开发经验可以完全用在 Jmix 上，不需要学习新的框架，仅需要了解一些 Starter。
2. 关于 Starter，基于 Spring Boot 的核心技术允许我们在我们的框架上使用所有现有的 Starter。所以我们可以依赖已有的架构，这些架构有广泛的社区支持和完善的文档。
3. 还有一点，Spring Boot 在部署方面有非常棒的功能，包括开箱即用的容器化支持。

在提到 Spring Boot Starter 时，我们必须说说 CUBA 扩展。我们来看看...

![text]({{strapiUrl}}/uploads/c1a763a2f95443c1821b4275b7e4eea3.png)

## 模块化

很多次，有开发人员向我们抱怨，只创建一个空 CUBA 应用程序，没有一行业务逻辑代码，即使这样，也会应用程序也会创建大量表，并且带有一些从来用不到的功能。

在 CUBA 7 中，我们开始将一些核心功能提取为独立的扩展。基本上，CUBA 是一个 API 集合，这种方式为模块化处理提供了足够的灵活性。

从 Jmix 开始，你可以独立地使用框架功能，比如安全、审计等。现在所有的功能都是以 Spring Boot Starter 的形式提供。比如 CUBA 中的数据审计功能，在 Jmix 中是一个独立的模块。这个模块又被分为 Core 和 UI 模块。这意味着你可以使用整个模块作为数据审计引擎，也可以只使用 Core 模块，然后用自己实现的 UI 代替内置的。

一些功能使用 Spring Boot 提供的功能代替了，比如 healthcheck 使用 Spring Boot actuator 替换 (见 “不重复造轮子” 章节)。

Jmxix 提供了超过 20 个 Starter 。下面是一些 Starter 和依赖关系：

<table>
<tbody>
<tr>
<td>
<p><strong>功能</strong></p>
</td>
<td>
<p><strong>Starter</strong></p>
</td>
<td>
<p><strong>依赖</strong></p>
</td>
</tr>
<tr>
<td>
<p>Entity log</p>
</td>
<td>
<p>Audit</p>
</td>
<td>
<p>Data</p>
</td>
</tr>
<tr>
<td>
<p>File storage</p>
</td>
<td>
<p>Core</p>
</td>
<td>&nbsp;</td>
</tr>
<tr>
<td>
<p>User settings</p>
</td>
<td>
<p>UI Persistence</p>
</td>
<td>
<p>Data</p>
</td>
</tr>
<tr>
<td>
<p>Table presentations</p>
</td>
<td>
<p>UI Persistence</p>
</td>
<td>
<p>Data</p>
</td>
</tr>
<tr>
<td>
<p>Entity log</p>
</td>
<td>
<p>Audit UI</p>
</td>
<td>
<p>Audit, UI</p>
</td>
</tr>
<tr>
<td>
<p>Config properties stored in DB</p>
</td>
<td>
<p>Core</p>
</td>
<td>&nbsp;</td>
</tr>
<tr>
<td>
<p>Restore deleted entities</p>
</td>
<td>
<p>Data tools</p>
</td>
<td>
<p>Data, UI</p>
</td>
</tr>
<tr>
<td>
<p>User sessions</p>
</td>
<td>
<p>Core</p>
</td>
<td>&nbsp;</td>
</tr>
<tr>
<td>
<p>Dynamic attributes</p>
</td>
<td>
<p>Dynamic attributes</p>
</td>
<td>
<p>Data, UI</p>
</td>
</tr>
<tr>
<td>
<p>Entity Snapshots</p>
</td>
<td>
<p>Audit</p>
</td>
<td>
<p>Data</p>
</td>
</tr>
<tr>
<td>
<p>Related entities</p>
</td>
<td>
<p>Advanced Data Operations</p>
</td>
<td>
<p>Data, UI</p>
</td>
</tr>
<tr>
<td>
<p>Bulk editor</p>
</td>
<td>
<p>Advanced Data Operations</p>
</td>
<td>
<p>Data, UI</p>
</td>
</tr>
</tbody>
</table>

你可以看到几乎所有的 Jmix 模块都依赖 “data” Starter。这不奇怪，因为 CUBA 平台最强大的部分是...

## 数据访问层

我们会对这块进行大量修改，在保留 CUBA 最好的部分的同时引入一些新功能， 以进一步提升生产力。

CUBA 的数据模型几乎完美，但是有一点瑕疵：缺少一点灵活性。比如，如果你需要软删除，你不得不实现合适的接口（或继承 `BaseEntity` 实体）并在相应的表中添加指定名称的列。如果你使用 `StandardEntity` 类，所有的主键都必须存储在名称为 `id` 的列中。

这导致了在开发新数据模型时有一些限制。在基于已有数据库开发时也会产生一些问题。比如使用 CUBA 迁移遗留系统到现代化框架时就会遇到很多问题。

在 Jmix 中，实体模型变地更加灵活。你不再需要继承 StandardEntity 类或实现指定的实体接口。只需要使用 `@JmixEntity` 注解实体类。

我们决定放弃使用接口的方式指定实体功能，使用通用注解来代替。比如我们使用 JPA 的 `@Version` 注解来 Spring Boot 的 `@CreatedBy` 注解来代替 `Versioned` 和 `Creatable` 接口。

这种方式可以使代码意图更加明显 - 你通过查看代码就能知道实体支持哪些功能

```
@JmixEntity
@Table(name = "CONTACT")
@Entity(name = "Contact")
public class Contact {

   @Id
   @GeneratedValue(strategy = GenerationType.IDENTITY)
   @Column(name = "ID", nullable = false)
   private Long id;

   @Version
   @Column(name = "VERSION", nullable = false)
   private Integer version;

   @InstanceName
   @NotNull
   @Column(name = "NAME", nullable = false, unique = true)
   private String name;

   @LastModifiedBy
   @Column(name = "LAST_MODIFIED_BY")
   private String lastModifiedBy;

   @Temporal(TemporalType.TIMESTAMP)
   @LastModifiedDate
   @Column(name = "LAST_MODIFIED_DATE")
   private Date lastModifiedDate;

```

“CUBA 视图” 现在称为 “获取计划（Fetch Plans）”。新的名称更能体现出它的作用。

Jmix 的数据访问层现在支持引用属性的自动延迟加载。因此，即使现在不使用获取计划过滤本地属性也不再会遇到之前令人懊恼的 “UnfetchedAttributeException” 异常了。

另外一个重要的变化是数据库的生成和更新处理机制。我们决定使用 Linquibase 代替我们自己实现的 DB 更新引擎。Spring Boot 负责执行数据库更新脚本。这是 “不重复造轮子” 的又一个案例，我们使用 java 生态中成熟的框架。

Liquibase 可以生成与具体 DB 无关的更新脚本，因此，如果你开发一个产品或 Jmix 扩展，你将不需要对每种支持的数据库生成更新脚本。Liquibase 会根据具体的 JDBC 驱动来生成合适的更新脚本。当然，也允许开发人员自定义特定数据库的脚本。嗯，这太棒了，尤其是对于扩展开发人员，这能节省很多时间，避免很多问题。

当然，我们保留了 CUBA 魔法中的精华。当你修改了实体，Jmix Studio 会自动生成 Liquibase 脚本来响应变化。

在我们谈论 CUBA 时我们还会考虑什么？当然是框架的高级功能...

## 安全

Jmix 安全是一个独立的模块。现在你可以选择是否使用 CUBA 安全引擎，或者使用其它的安全机制。

我们重构了我们的安全引擎。现在它与 spring-security 紧密集成。为了简化开发人员的工作并且践行 “不重复造轮子” 的理念，我们使用 “标准” 框架替换了我们自定义的引擎，“标准” 框架意味着有丰富的文档和熟悉它的开发者。相关的数据模型也相应做了修改 - 在 Jmix 中我们使用 Spring Security 中的类，比如 UserDetails 和 SessionRegistry。所以对于 CUBA 用户，一开始你可能会有点陌生的感觉。

角色也有变化 - 我们合并了角色和访问组以简化安全管理。另外，我们添加了 “聚合角色”，它是一种由其它角色组合而来的角色 - 有很多用户请求实现这个功能。

Spring 安全的配置和使用比较复杂，但是 Jmix 使之尽可能地易用。你可以像在 CUBA 中一样为实体、属性、界面设置访问权限以及数据库行级的安全限制。

安全模块的安装也与 CUBA 相同，只需要添加依赖到你的项目，然后 Jmix 将施展魔法，为你配置好安全设置以及用户管理 UI（如果你需要）。

除了安全，CUBA 中每个人都喜欢的另一个特性是： 简化了应用程序的开发...

## 用户界面

后台界面（也称为通用 UI）保持不变。基于组件的 UI 是 CUBA 的重要组成部分，我们计划在 Jmix 中继续对其进行支持，包括界面生成器、IDE 中的 UI 编辑器等。我们也添加了新组件，例如独立的分页组件、响应式网格布局。唯一的区别是，由于 Jmix 的架构变化，现在可以将通用 UI 完全从应用程序中排除。

请注意，Jmix 应用程序是单层的; 不再有 "core-web" 的区分。这种方式更符合现代化的架构方式。如果要分离，你可以通过实现两个 Jmix 应用程序并创建用于通信的 REST API 来实现。在这种情况下，UI 将不依赖于数据模型，你可以传递 DTO 以便在前端显示数据或在后端处理数据。

当我们为框架的新版本做规划时，不能忽略 JS UI 框架的发展。因此，我们开始在 CUBA 7 中开发了 ReactJS 客户端生成器（即 front-end 模块），在 Jmix 我们会继续这项工作。JS 框架通常具有比较陡峭的学习曲线，因此我们的目标是使 Jmix 中 ReactJS UI 的开发体验接近于通用 UI 的开发。

我们引入了 TypeScript SDK，并开发了一组可用于 UI 开发的自定义 ReactJS 组件。前端模块依赖于 CUBA 开发人员熟悉的通用 REST API。IDE 支持生成基本的 ReactJS UI。

目前，开发人员可以使用我们的组件来生成熟悉的 “浏览界面（browser）”和 “编辑界面（editor）”。后续我们会在 Studio 中添加更多组件来简化 ReactJS UI 的开发。

现在我们已经讨论了 Jmix 中几乎所有的主要变化，但是还需要介绍...

![text]({{strapiUrl}}/uploads/9b0dd8c1ff404e01aa0d9e90b1729b2e.png)

## 部署

CUBA 有两种部署格式：WAR 和 UberJar，有两个部署选项：单点 app 部署或分模块部署（core+web...）。

Jmix 将使用 Spring Boot 构建插件来部署应用程序。这意味着，可以用可执行的 Jar 或可部署的 WAR（也能作为单独应用运行）的方式运行 Jmix 应用。

但是最具吸引力的是容器化。现在你不需要自己创建 Docker 文件来创建应用程序镜像，在 Jmix 中这个功能开箱即用。另外，你也可以创建分层 jar 以使 Docker 镜像更高效。除此之外，也支持云原生 buildpacks。

因此，Jmix 应用程序将可以使用最先进的技术在现代云环境中进行部署。

变化如此多，该如何...

## 从 CUBA 迁移到 Jmix

我们要强调的第一件事：我们不会放弃 CUBA。7.3 版将提供长期支持，免费支持的周期是五年。之后，再提供五年时间的商业支持。因此，CUBA 框架至少可以使用 10 年。

目前 Jmix 处于预览阶段，我们将在一段时间内对其进行打磨、优化，使之稳定，然后正式发布可用于生产环境的稳定版本。暂定于 2021 年第二季度发布。但是，如果你打算开始使用 CUBA，请先了解一下 Jmix。它现在足够稳定，可以用于概念验证目的的开发。请注意，你几乎可以使用 Spring Boot 生态中的所有资源。

为了提供向后兼容，我们引入了 jmix-cuba 模块。该模块包含 CUBA 中实现的大多数 API。因此，你无需太多修改码即可迁移到 Jmix。兼容性模块将在迁移时自动添加到你的应用程序。

大多数 CUBA 插件将逐步迁移到 Jmix 平台，包括报表、地图、业务流程。正如我们之前在 CUBA 7 中所做的那样，由于提供了一个具有相同功能的 Spring Boot Starter，因此在迁移到 Jmix 时可能会弃用某些模块。

我们对扩展（addon）的格式进行了调整，但功能保持不变。你可以使用与 CUBA 中相同技术来扩展实体和界面。对于服务的重写，你需要使用 Spring Boot 的方式 - 使用 Primary 注解标记扩展服务，框架提供的服务就会被替换。

像往常一样，在引入主要版本时（基本上，Jmix 就是 CUBA 8），可能会出现一些破坏性更改。这些更改以及解决方法将在文档中详细描述。

迁移另外一个主要部分是新的 Studio。Jmix Studio 在框架生态系统中扮演着非常重要的角色。因此，你仍然可以使用所有熟悉的设计器（实体和 UI）、快捷方式和推断（intentions）。Jmix Studio 将帮助你使用该框架创建应用程序。

## 总结

Jmix 是 CUBA 平台发展历程中的一大步。现在，你可以享受几乎所有的 Spring Boot Starter、使用最流行的 Java 框架和技术。同时，你仍然拥有 Jmix（CUBA 的后续者）所提供的所有方便且熟悉的 API 和功能，还有新 Studio 的出色开发体验。

<a href="http://jmix.io" class="button">获取 jmix.io</a> <a href="https://forum.cuba-platform.cn/c/jmix/" class="button forum" style="background: #6c5ce7!important; margin-left:30px;">欢迎讨论</a>

<style>.forum:hover, .forum:focus {box-shadow: 0 5px 20px 0 #6c5ce7;}</style>
