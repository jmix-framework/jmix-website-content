# Jmix 1.0 发布！

summary: 我们发布了 Jmix 框架的一个稳定版 - 1.0。我们在 bugfix 和代码的稳定性上花了很多工夫，为的是能交付可以用于生产环境的框架。但不止于此。

我们终于推出了 Jmix 框架的一个稳定版 - 1.0。在 [0.9 发布](https://www.jmix.cn/blog/announcing-jmix-0.9-pre-release-version/) 之后，我们在 bugfix 和代码的稳定性上花了很多工夫，为的是能交付可以用于生产环境的框架。但我们做的工作不止于此，Jmix 一直在进化，我们增加了一些功能，进一步简化了应用程序的开发。

## Jmix Studio

除了已有的 Jmix 项目模板之外，我们增加了一个新的模板：`Single Module Add-On - 单一模块扩展插件`。自动生成的项目结构包含所有 Jmix 扩展插件需要的特定设置以及一点点示例代码：包含一个实体、实体界面以及集成测试。这应该可以帮助开发者更快的构建扩展插件项目。

如果你是 BPM 扩展插件的用户，从现在开始，可以在设计时创建 BPM 流程图（目前是 beta 版）。所有的业务流程会在应用程序启动时部署。

![bpmn_idea.png]({{strapiUrl}}/uploads/bpmn_idea_c107e47b25.png)


## 核心

Jmix 核心在这一版没有很多改动，但是有个功能是值得一提的。

这就是新的实验性功能：对 Spring Data Repository 接口的支持。现在 Jmix 中，可以使用 Spring 的 Repository 接口定义数据的存取仓库。我们之前有篇博客介绍过：[CUBA 使用 Spring 查询接口](https://www.cuba-platform.cn/blog/spring-query-interfaces-in-cuba/)。现在 Jmix 中正式引入了此功能。我们目前正在为此功能编写开发者手册，但是代码已经支持了，可以试试看。

## 扩展插件

Jmix 插件市场增加了更多的扩展插件，主要有：

* 实体审计
* 工作流
* IMAP
* 图表和透视表
* AWS 文件存储
* UI 本地化: 中文、俄语、德语
* 多租户
* 报表
* 搜索

所有这些插件都适配了 1.0 并可以通过 Studio 进行安装。

其中提到的最后一个 - 搜索，这里单独说一说。Jmix 中，这个扩展插件使用了 Elasticsearch 引擎。而且，我们为全文检索功能提供了一种新的配置方式，可以参考[文档](https://docs.jmix.io/jmix/1.0/search/index.html)（目前仅英文）了解更多内容。

## 结论

Jmix 已经可以用于生产环境了。如果之前已经用 Jmix 0.9 进行开发，可以根据[升级向导](https://docs.jmix.io/jmix/1.0/whats-new/#upgrade-from-0.9)迁移至 1.0。

下一步，通过 Jmix Studio 的帮助，我们计划支持从 CUBA 迁移至 Jmix。目前我们正在开发这个功能，希望能做到尽可能平滑的迁移。

总之，使用 Jmix 1.0，你可以开始使用该版本提供的新扩展插件和可视化编辑器。

