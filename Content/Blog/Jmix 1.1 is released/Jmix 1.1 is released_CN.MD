summary: 
Jmix 1.1 已经发布，我们在这个版本中引入了几项重要特性：CUBA 项目迁移、Kotlin 支持和 Java 17 支持。    

# Jmix 1.1 发布!

Jmix 的下一个版本 - 1.1 -  已可下载。
在这个版本中， 我们引入多项重要特性： 

1.	CUBA 项目迁移
2.	支持 Kotlin
3.	完全支持 Java 17 

Jmix Studio 也已同步更新以支持这些新特性。

## CUBA 项目迁移

你可以将 CUBA 项目迁移到 Jmix, 有两种方式来执行迁移。

如果在 Jmix Studio 中打开 CUBA 项目，IDE 会询问你是否要迁移到 Jmix 最新版，这时你可以立即开始迁移处理。
<br>
<img src='{{strapiUrl}}/uploads/1_a69e931d8e.png'>
 
如果你想稍晚一些开始迁移，那么后续可以通过 Jmix Studio 的 `File -> New -> Jmix project from this CUBA project` 菜单来执行迁移。

<br>
<img src='{{strapiUrl}}/uploads/Screenshot_2021_10_30_at_10_36_55_2fd61a90e4.png'>
 
Studio 会自动修改项目结构以满足 Jmix 的要求。大部分的代码会保持不变，Jmix 使用 CUBA 兼容 API 来提供向后兼容性。

迁移结果和建议日志会保存到 `MigrationResult.md` 文件。这个文件包含了自动迁移结果和手动迁移建议。迁移过程不会对你的原项目进行任何更改，所以你可以安全地在项目的任何工作副本执行迁移。

你可以在从[Jmix 文档](https://docs.jmix.io/jmix/cuba/index.html) 找到更多细节说明。 

## Kotlin 支持

在 Jmix 1.1 中，我们为 Kontlin 开发人员提供了应用程序模板，同时 Jmix Studio 也对 Kotlin 提供了完全支持。
<br>
<img src='{{strapiUrl}}/uploads/Screenshot_2021_10_30_at_10_39_35_8400b34f25.png'>
 
如果你选择了基于 Kotlin 的项目模板，Jmix Studio 将基于 Kotlin 语言及其最佳实践来生成实体、服务和界面控制器。请注意：在使用 Kotlin 开发 JPA 实体时，你需要留意一些规则以避免运行时问题，比如使用开放类(open class)、以特殊的方式实现 `toString()` 方法等。 

这里有一篇关于 Kotlin 最佳实践和常见陷阱的[文章](https://www.jpa-buddy.com/blog/best-practices-and-common-pitfalls/) 。好消息是 Jmix Studio会替开发人员考虑这些问题，所以你不必过多分心。

这同样适用于 IDE 中的所有生成器和代码意图（code intentions）以帮助新手和经验丰富的 Kotlin 开发人员来优化他们的代码。


## Java 17 支持

Jmix 1.1 现在允许使用 Java 17。框架运行时已在 JDK 17 上进行了完全测试。JDK 17 是一个 LTS 版本，会有 [两年时间的免费支持](https://mreinhold.org/blog/frward-even-faster) ，同时不同 JDK 供应商会提供更长时间的付费支持，比如 Oracle 会提供至少八年时间的付费支持。这意味着 Jmix 应用程序在这段时间会有稳定的运行平台，并且 JDK 供应商会为平台提供合适的支持级别。
此外，Java 17 还提供了很多改进， 这些改进会使应用程序运行更快（得益于编译器优化和更好的垃圾回收器），使开发人员编写出更好更安全的代码（封闭类、Record 类、switch 表达式等等）。 

如果要在项目中使用 Java 17 ，只需要从 `build.gradle` 中删除 `sourceCompatibility` 行，并且确保使用 Gradle 7.2 及以上版本作为构建工具。你可以在 `gradle-wrapper.properties` 文件中修改 Gradle 版本。
<br>
<img src='{{strapiUrl}}/uploads/Screenshot_2021_10_30_at_10_42_27_d708bbcd65.png'>

当然，你也需要设置项目的 JDK 版本。
<br>
<img src='{{strapiUrl}}/uploads/Screenshot_2021_10_30_at_10_46_41_8460b0854f.png'>

现在，你可以在 Jmix 中使用最新版的 Java 了。

## Studio 改进

我们来看看最值得注意的 Jmix Studio 改进。

*新的 “注入” 对话框*，现在注入对话框中将可注入的对象按以下分类显示，对象分类更加直观、清晰：
- Project Beans -  当前项目中的 Spring Bean。
- Project Properties - 当前项目中的配置属性类。
- Infrastructure - 经常使用的框架 Bean 。 
- Other Beans - 框架和 Addon 的其它 Spring Bean 。
- Other Properties - 框架和 Addon 的所有配置属性类 。

<img src='{{strapiUrl}}/uploads/Screenshot_2021_10_30_at_20_20_03_2584c1a829.png'>

除此之外，你也可以随时使用快速过滤：键入需要的组件的名称即可减少可用对象的数量。

*新的可视化组件* ，包括 ResponsiveGridLayout、 Single- 和 Multi- Select List 。

ResponsiveGridLayout 是一个容器，其中的组件会被布局在一个栅格上，基于 Bootstrap 的 12列栅格系统。我们看看下面的代码：  

```
<window xmlns="http://jmix.io/schema/ui/window">
    <layout>
        <responsiveGridLayout stylename="demo">
            <row>
                <col>
                    <label value="1 of 2"/>
                </col>
                <col>
                    <label value="2 of 2"/>
                </col>
            </row>
            <row>
                <col>
                    <label value="1 of 3"/>
                </col>
                <col>
                    <label value="2 of 3"/>
                </col>
                <col>
                    <label value="3 of 3"/>
                </col>
            </row>
        </responsiveGridLayout>
    </layout>
</window>
```
上面的代码会渲染出以下 UI :
<br>
<img src='{{strapiUrl}}/uploads/Screenshot_2021_10_30_at_20_26_05_3cfdf0ca74.png'>

如你所见，现在你有更多的选项来计划布局。

*Select List*  在垂直滚动列表中显示一个预定义的选项列表。 SingleSelectList 只允许用户从列表中选择单个条目。MultiSelectList 允许多选。
<br>
<img src='{{strapiUrl}}/uploads/Dizajn_bez_nazvaniya_d57348fd8f.jpg'>
               
*BPM 设计器* 现在允许开发人员直接在 Studio 中创建  BPM 流程图 (需安装 BPM 扩展)。这可以简化 BPM 流程部署，你不需要从开发环境上传然后导入到产品。 现在 BPM  流程描述和相关的代码(服务、用户提供者等) 存储在了代码库中，所以不会出现因流程定义与代码分离导致的类似新流程部署到旧应用程序的问题。
<br>
<img src='{{strapiUrl}}/uploads/Screenshot_2021_10_30_at_20_07_20_88aa300fe9.png'>
 
需要注意的是，BPM 设计器在运行时仍然可用，所以你也可以像在 Jmix 1.0 中一样动态创建流程。

## 总结

我们在持续改进 Jmix 框架和 Studio。在新功能的帮助下，你可以开始将你的 CUBA 应用程序迁移到现代应用程序栈：Jmix(以 Spring Boot 为核心) 和 JDK 17 。如果你想评估使用 Kotlin 进行后端开发，现在是时候了。你可以从[发行说明]( https://docs.jmix.io/jmix/whats-new/index.html)找到更多详细信息。
