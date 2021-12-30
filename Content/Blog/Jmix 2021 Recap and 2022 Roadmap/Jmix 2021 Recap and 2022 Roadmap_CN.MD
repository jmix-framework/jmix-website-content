# Jmix：回顾2021，展望2022

又一年快要过去了，到了年底的传统节目：回顾上一年和计划下一年。

## 2021 

2021 年是非常忙碌的一年，我们完成了大量的研发工作和新功能的开发，我们的团队成员增加到了 60 人。上半年，由于新人的加入，我们的老员工们承担了不小的压力，好在最后证明这一切都是值得的：我们现在能完成的工作是一年以前想都不敢想的。

其中最重要的工作当然是发布 Jmix 的稳定版。我们在六月份发布了 [1.0 版本](https://www.jmix.cn/blog/jmix-1-0-is-released/)，但老实说，直到最近 [1.1 版本的发布](https://www.jmix.cn/blog/jmix-1-1-is-released/)，这项工作才算正式完成。在 1.1 中，我们提升了平台的可用性和稳定性，并且大多由 Haulmont 开发 的 CUBA 插件也迁移到了 Jmix。

我们清楚的知道，企业级项目一般都会存续很长时间，所以我们最重要的工作就是加快完成项目迁移至框架最新版的功能。在 Jmix 1.1 中，我们支持了从 CUBA 平台迁移至 Jmix，这项工作由框架中一个[特定的兼容模块和 Studio](https://docs.jmix.io/jmix/cuba/index.html) 完成。
 
另外，今年还诞生了一个新产品，同样也是 IntelliJ IDEA 插件 - [JPA Buddy](https://plugins.jetbrains.com/plugin/15075-jpa-buddy)。一句话总结它的功能就是，我们将 Jmix 中处理数据模型的能力用在了使用 JPA 的通用 Java 或 Kotlin 项目中。新产品的成功出乎所有人的意料，一年内的独立下载量超过 50 万次！这证明我们以轻量级、非倾入式的方式提供开发工具的想法能被开发者社区接受。欢迎阅读 JPA Buddy 的[回顾文章](https://www.jpa-buddy.com/blog/the-first-annual-recap-from-jpa-buddy/)进一步了解。

![logo jpa buddy]({{strapiUrl}}/uploads/Logo_JPA_Buddy_1b97eec30f.png)

也许您会觉得 JPA Buddy 与 Jmix 社区关系不大，但事实上它为 Jmix 带来了正反馈。这样一款小巧且受欢迎的工具有着非常快速的响应和发布周期，以至于我们能迅速打磨这款产品，为开发者提供了完美的体验。于是，我们将许多 JPA Buddy 的成功设计和功能复制到了 Jmix！比如，我们就用这个方法将自定义的数据库迁移脚本换成了行业标准 Liquibase。

另一项我们今年启动的工作是 CloudControl，这是一个为 Jmix 扩展 DevOps 和云部署能力的项目。这个项目完成后，Jmix 将能支持应用程序的完整软件开发生命周期。CloudControl 将支持两种场景：

- 一键部署，从 Studio 部署至公有云，比如 AWS，这个方式是原型系统、个人项目或者 Demo 系统的理想部署方式。
- 一个完整的基础架构和团队合作的工作环境，用来管理和部署项目，使用者不需要有很深的 DevOps 知识。

第二点我再详细解释下。CloudControl 的设计遵循我们的口号 “不重复造轮子”，背后其实用的是 GitLab，因此，您可以用 CloudControl 提供的配置好的 GitLab 实例或者连接至您已有的实例。这样可以直接使用问题追踪、CI/CD 引擎、Git 或者二进制仓库等功能。除此之外，CloudControl 还增加了以下功能：

- Terraform、Docker Compose、Kubernetes 的代码生成和拖拽式设计器，使得项目基础架构描述更加便捷
- 标准的 CI/CD pipeline 代码生成
- 访问项目和部署环境的限制策略
- Jmix Studio 中集成的专用简洁的 web 界面

所以本质上，CloudControl 是在开发工具、DevOps 基础设施、部署环境之间建起的一道桥梁。

一直以来我们还有一个关键的工作方向，那就是新的前端技术。最初，我们计划将新的 React 前端构建在 GraphQL API 之上作为 Vaadin 的完全对等替换方案。然而，随着研发的进展，我们意识到同时支持两个对等的客户端会把 Jmix 搞得一团糟，比如需要维护成倍的文档，不同的 API 等。此外，web 开发者对 Jmix 的通用 API 方案持有保留意见，因为他们习惯于使用特定的 API 端点。

上面这些因素使得我们重新思考并改变了策略，Jmix 将继续使用 Vaadin 作为主要客户端，专注于提供无缝的纯 Java/Kotlin 全栈开发体验。同时，Jmix Studio 自动生成自定义的 REST/GraphQL API 端点（包括通用 API），以方便其它前端使用 Jmix 作为后端程序。有了这个决定之后，我们开始着手将 Vaadin 升级至最新的 23 LTS 版本。

即便如此，我们在 React 客户端所做的工作也并没有白费。我们最近发布了 [React Buddy](https://plugins.jetbrains.com/plugin/17467-react-buddy) 的 beta 版本，这也是一个 IntelliJ IDEA/WebStorm 插件，为 React 开发者提供可视化工具和编码辅助功能。与 JPA Buddy 一样，我们希望这个工具也能广受欢迎并为 Jmix 社区提供正反馈。React Buddy 可以为构建在 Jmix GraphQL 之上的 React 客户端提供快速开发体验，目前有一些额外的工作仍在进行。它作为一个独立的产品进行维护，这样就不会影响 Jmix 的代码了。

![logo React Buddy]({{strapiUrl}}/uploads/Logo_React_Buddy_a2e1766bdf.png)

按照计划，我们也启动了基于 GraphQL API 的 Flutter 移动端的研发。另外，还有一些 Jmix 的小改进，包括 JPQL 设计器、支持代码片段以及在 Studio 中提供 BPM 设计器等。所有这些都仍在进行，并且势头不错。唯一一项之前有计划但由于人手不够没有启动的功能就是支持设计时的报表。

我们在 12 月上线了[新的网站](https://jmix.io)，这是我们重新调整营销策略的第一步。我们发现 Jmix 的易用性和高生产力首先会引起这些关注商业结果的人产生共鸣，比如技术经理、自由职业者、或者小 IT 公司的职员。所以我们现在更多的是谈论商业价值，强调 Jmix 的灵活性、开源、对开发者友好以及无需运行时的天价费用等特性，将 Jmix 作为过度宣传的低代码平台的健康替代品。

与新的产品功能一起，我们希望新的营销策略能帮助我们提高销售额，并加快社区的成长。今年我们实现了增长 20% 以上，而营销活动几乎为零，这更增加了我们的信心。

最后，我想在 2021 年结束时对我们所有的社区成员致以诚挚的感谢，感谢大家体谅我们最近对价格进行了调整，感谢大家对我们的支持，有了你们的帮助，我们才能创造更好的产品并在将来为之提供专业的服务。

## 2022

 
如您所见，我们今年启动了多个新方向。这些都有很好的进展，但是很多工作需要大量的研发，并不能在一年之内完成。所以我们 2022 年的终极目标是完成这些工作。


下面列举一下几个关键功能的发布计划，实时的 roadmap 可以通过 [Github](https://github.com/orgs/Haulmont/projects/1) 查看。

- 一季度：JPQL 设计器、BPM 设计器、业务日历以及用户通知插件
- 二季度：CloudControl 以及新版 Vaadin 23 UI 客户端预览版
- 三季度：CloudControl 以及新版 Vaadin 23 UI 客户端稳定版

 
上面提过，我们仍然在努力让 React Buddy 能与 Jmix 结合，以提高 Jmix 的前端开发速度。我确信我们今年能发布一版。Flutter 工作可能需要暂停一阵，我们要集中精力先完成其它的项目。

当然，我们今年也计划发布很多改进和一些新插件。我们还有另外一个大的研发方向，目前暂时保密，来年晚些时候会公布。敬请保持关注！

希望您喜欢 Jmix 2022 年将要发布的内容。我们团队祝您新年快乐，项目成功！感谢大家一直以来的支持！欢迎在[论坛讨论帖](https://forum.cuba-platform.cn/t/topic/2018)中发表您的看法和建议。

Andrey Glaschenko
