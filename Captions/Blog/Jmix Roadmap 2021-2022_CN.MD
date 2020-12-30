### Jmix Roadmap 2021-2022

### Jmix Roadmap 2021-2022

First of all, let me wish all of you a Happy New Year and congratulate on surviving 2020! It has been a rough year for the world, and I hope that 2021 will bring us more positive news.
首先，祝大家新年快乐！也恭喜大家能在 2020 年的 hard 模式生存下来！对全人类来说，今年都是很艰难的，希望 2021 年能带给大家更多的好消息。

译者注：原文是 Jmix/CUBA.platform 负责人 Andrey Glaschenko 书写，这里按原文直译，以作者为第一视角。

First of all, let me wish all of you a Happy New Year and congratulate on surviving 2020! It has been a rough year for the world, and I hope that 2021 will bring us more positive news.
In this article I would like to recap the results of 2020 for our team, and share some plans for the upcoming 2021.
首先，祝大家新年快乐！也恭喜大家能在 2020 年的 hard 模式生存下来！对全人类来说，今年都是很艰难的，希望 2021 年能带给大家更多的好消息。
在这篇文章中，我想给大家总结一下我们团队 2020 的成果，并分享一下 2021 年的计划。

We kept mostly silent about our plans over the last year. I hope that now, as [Jmix is released](https://www.cuba-platform.com/blog/jmix-the-future-of-cuba-platform/), you can see why. The amount of changes and R&D work meant that it was just too hard to give promises. We needed to be flexible and move at a comfortable pace.
But even though most of the team was focused on Jmix, we delivered some cool features for CUBA as well:

-   Kotlin support and design-time security roles in [CUBA 7.2](https://www.cuba-platform.com/blog/cuba72-whats-new/)
-   The new [Helium](https://www.cuba-platform.com/blog/helium-announce/) theme with a visual theme editor
-   Support for React Native in the frontend [generator](https://www.cuba-platform.com/discuss/t/frontend-20-1-beta-published/12275/10)
-   [CUBA SDK](https://www.cuba-platform.com/blog/development-in-isolated-network/), helping to develop your projects in isolated environments

过去一年中，我们一直没有对外发布过我们的计划。希望在此时，也就是 [Jmix 发布](https://www.cuba-platform.cn/blog/jmix-the-future-of-cuba-platform/) 之后，你能明白个中原因。改动之大、研发工作量之重意味着很难对外做出 deadline 承诺。我们需要随机应变并保持舒适的开发速度。
但即使团队的大部分人都扑在 Jmix 上，我们还是为 CUBA 平台交付了一些很酷的功能：

-   在 [CUBA 7.2](https://www.cuba-platform.cn/blog/CUBA7.2-what'sNew/) 支持了 Kotlin 和设计时安全角色
-   新的 [Helium](https://www.cuba-platform.cn/blog/helium-announce/) 主题及其可视化设计器
-   在前端 [generator](https://www.cuba-platform.com/discuss/t/frontend-20-1-beta-published/12275/10) 中支持 React Native
-   [CUBA SDK](https://www.cuba-platform.cn/blog/development-in-isolated-network/)，在无网络条件下帮助你开发项目

Of course, there were hundreds of other evolutionary improvements in Studio, the framework and the frontend generator.
当然了，在 Studio，框架，前端生成器中还有其他数以百计的革命性提升。

On the community side, we added [Italian](https://www.cuba-platform.it/) and [French](https://www.cuba-platform.fr/) versions of the website and forum. We also rolled out a simplified form for the academic license requests, so [more and more](https://www.cuba-platform.com/blog/cuba-platform-helping-it-education/) universities are using CUBA for their enterprise software courses!
We welcome new big brands among our customers, including Ingenico and Sber - the largest bank in Eastern Europe. Sber has [signed](https://www.sberbank.ru/en/press_center/all/article?newsID=1ffbb179-f30e-4a14-b230-c04d38123fe5&blockID=1539&regionID=77&lang=en&type=NEWS) a large-scale agreement to adapt and use CUBA Studio to speed up the development of applications for in-house users across the whole bank.

而在社区方面，我们新增了 [意大利语](https://www.cuba-platform.it/) 和 [法语](https://www.cuba-platform.fr/) 版的网站及论坛。我们还推出了方便申请学院许可的简化表单，[越来越多的大学](https://www.cuba-platform.cn/blog/cuba-platform-helping-it-education/) 开始将 CUBA 用在企业级软件课程中！
我们的客户中，也新增了一些“大牌”，包括 Ingenico 和 Sber，Sber 是东欧最大的银行。与我们 [签署](https://www.sberbank.ru/en/press_center/all/article?newsID=1ffbb179-f30e-4a14-b230-c04d38123fe5&blockID=1539&regionID=77&lang=en&type=NEWS) 了大规模协议，约定将使用 CUBA Studio 加速整个银行内部系统的开发。

## What’s coming in 2021?

## 2021 年的新计划

The recent release of Jmix provides us a solid foundation, so we look into the future with confidence. We have ambitious plans and currently we are scaling the team to support them. We expect that over 50 developers will be working on Jmix by the end of next year!
最新发布的 Jmix 为我们提供了一个坚实的基础，所以对未来我们更有信心。我们制定了激进的计划，并正在扩张团队，希望在明年年底 Jmix 有超过 50 个开发人员！

Our first priority is of course the release of a stable version of Jmix. This includes complete documentation, migrating remaining addons and thorough testing. We are aiming at Q2 2020 to finish this work.
我们最重要的目标首先还是发布稳定版的 Jmix。包括完整的文档、迁移剩下的扩展插件以及全面的测试。计划在 2020 第二季度完成这些工作。

New features are described below. Keep in mind that many of them still require R&D so don’t ask me for implementation details. Still, this should give sufficient clue of where we are heading, and I hope you’ll like it!
下面会介绍一些新功能。需要注意的是，很多仍然在开发中，所以不要问我实施细节。但是，下面的介绍能给大家足够的信息，知道我们是朝哪个方向努力，希望你们能喜欢！

### Frontend

### 前端

Now, as our CUBA backend is rebuilt around Spring Boot, the most widely used server side technology for enterprise projects, it is time to shift focus towards the frontend. Well, to be honest, the time has come a couple of years ago, as Vaadin 8 got outdated. However, we always keep long term sustainability and backwards compatibility in mind. Unfortunately for us, the web frameworks world is changing so fast that it was hard to make a safe bet. Even the Vaadin components set [is still actively evolving](https://www.cuba-platform.com/blog/vaadin-10-evaluation/) in the latest releases.
So we just had to keep Vaadin 8 UI which, with all its limitations, “just works”. Nevertheless, the frontend team was exploring new approaches in the portal module and recently in the TypeScript SDK and the React frontend generator. You can already scaffold React and React Native clients, though it is still a much more complicated and manual process compared to the Vaadin-based UI. You can plug in any other web framework with the help of Typescript SDK of course, but it is an even more manual process.

此时，因为 CUBA 后台已经用 Spring Boot 重构了，Boot 是企业级项目用的最广泛的服务端技术，所以我们需要将一部分精力转移到前端。好吧，老实说，我们关注前端转变是在几年前了，彼时 Vaadin 8 开始跟不上潮流。但是，我们始终将长期的可持续性和向后兼容性作为我们考虑的原则。不幸的是，Web 框架瞬息万变，我们很难下一把稳赢的赌注。Vaadin 这边也是，组件库在最新的几个版本中也一直还在 [积极更新](https://www.cuba-platform.com/blog/vaadin-10-evaluation/) 。
所以对于我们来说，只能继续使用 Vaadin 8，尽管有局限性，但是“至少能用”。同时，前端团队也在 portal 模块探索新的方案，最近在研究 Typescript SDK 和 React 前端生成器。你已经可以生成 React 和 React Native 客户端的框架代码了，虽然与 Vaadin UI 比还比较复杂也需要更多手动工作。另外，也可以通过 Typescript SDK 集成任何其它的 web 框架，只不过也需要很多手动工作。

Anyway, the quest is over. We believe that React is “here to stay” for long enough. So the main focus for 2021 is to push React UI client to the state when it is as productive and as easy to use as Vaadin. Naturally, this assumes full support in Studio, including visual designer with screen templates, hot reload, theming, and a complete suite of components, at least equivalent to their Vaadin counterparts. As usual, we will try to abstract (not isolate) developers from the intricacies of the JS ecosystem to the possible extent. The benefits are obvious: faster and better scalable UI with wider customization options and massive community support.
However, there is also a price to pay. Basic understanding of Typescript, HTML, CSS will be required. You will also require the commercial IntelliJ IDEA Ultimate for comfortable work with Typescript. We plan to release a version of Studio bundled with it.

无论如何，探索阶段已经结束。我们相信 React 能支持足够长的时间。所以 2021 年我们主要专注于将 React 客户端的生产力和易用性推至与 Vaadin 客户端同等的层级。自然地，这就意味着我们需要 Studio 的全面支持，包括带界面模板的可视化设计器、热加载、主题以及一组完备的组件，至少与 Vaadin 能实现的类似。与往常一样，我们会尝试将开发者从鱼龙混杂的 JS 生态中抽象出来（而非孤立出来），从而回归到可能正确的路径。好处是显而易见的：使用更快速更容易扩展的 UI，具有更多的自定义选项以及广泛的社区支持。
但是，也需要付出一定的代价。需要了解基础的 Typescript、HTML 和 CSS。如果希望在 IDEA 中舒服的开发 Typescript，还需要商业版的 IntelliJ IDEA Ultimate。我们计划会发布一版 Studio 包含该 Ultimate 版。

What happens to Vaadin? No worries, its story also continues. We still believe that it is a great choice in many scenarios. It is perfect for backend developers who do not have much love for web stuff. Unless you expect tens of thousands of users or high latency networks it will perfectly do the job, and such assumptions are valid for most back office applications. We keep monitoring the progress of Vaadin folks in the latest versions, and we are expecting to be able to upgrade from version 8 to one of those in 2022.

Vaadin 会有什么变化吗？别担心，我们会继续使用。在很多场景中，Vaadin 仍然是非常好的选择。特别是对于不怎么喜欢 web 的纯后端开发者来说，几乎完美。如果你的应用场景中没有数以万计的用户，并且也不是高延迟网络，那么 Vaadin 完全能胜任，大部分后台应用系统基本都符合这个场景。我们也一直在注意着 Vaadin 最新一些版本的动向，预计在 2022 年会从版本 8 升级至一个新的版本。

What about mobile applications? As mentioned above, we are already supporting React Native client generation, as well as PWA in the React client. In addition, we have started small-scale R&D around [Flutter](https://flutter.dev/), a very promising UI technology backed by Google. Flutter’s ultimate goal is to deliver a single UI technology for all platforms: mobile, web and even desktop. It will also be much more familiar to backend developers, while its ideology is similar to React: everything is a component (aka Widget) and UI is a function of state.
Flutter is gaining traction fast and is already the most popular choice for cross platform mobile apps, while web support is in beta. However, we are yet to see if it becomes mainstream.

移动端会怎么样呢？之前已经提到，我们已经支持生成 React Native 客户端，以及在 React 客户端使用 PWA。除此之外，我们还启动了关于 [Flutter](https://flutter.dev/) 的小规模研究，Flutter 是由 Google 支持的 UI 技术。其终极目标是为全平台提供单一的 UI 技术，包括移动端、Web 端甚至桌面端。可能后端开发人员会对于 Flutter 更加熟悉，但是其核心思想还是与 React 类似：万物皆组件，UI 是状态的展示。
Flutter 很快获得了广泛的关注，在移动 App 开发方面已经是最流行的选择了，不过对于 Web 的支持还处于 Beta 阶段。我们还需要观望一阵，看看是否会成为主流技术。

Our main use case - “line of business” applications - assumes manipulating with complex data graphs. So both Flutter and React require a convenient server-side API for this purpose. After some experiments, we ended up with GraphQL, which seems to be a very natural fit and which will become a shared part for both clients.

我们的主要使用场景是 “LOB” 系统，需要操作复杂的数据关系图。所以无论是 Flutter 还是 React，都需要一个方便的服务端 API。在做了一些实验之后，我们选择了 GraphQL，这个技术似乎很自然就满足了我们的需求，将作为两种客户端共享的后台服务使用。

To wrap it up, Jmix will be supporting more options to deliver frontend of any scale and complexity, for both web and mobile platforms, and both for those who love and hate JS :)
总结一下，Jmix 将会提供更多的选项以便交付任何大小、任何复杂度的前端，并同时支持 Web 和移动端，也同时支持喜欢和讨厌 JS 的开发者们 :)

### DevOps and Clouds

### DevOps 和云

For years, we considered deployment “out of scope” and focused purely on the development side of things. However, we get more and more requests to simplify this side of the application lifecycle too. So we decided to form a “DevOps” team within Jmix to handle this. The task is inline with our general approach: abstract (but - I’ll stress that again - not isolate) the developer from the specifics of underlying technologies like Jenkins, Docker, Kubernetes, Terraform and provide simple and convenient visual tools to configure your environments and CI/CD pipelines.
多年以来，我们都没有将部署纳入我们的考虑范围，而是专注于开发阶段的事情。但是，我们收到了越来越多的请求，要求我们能简化应用程序生命周期中的这一步。因此，我们决定在 Jmix 内部成立 “DevOps” 团队专门处理部署的事情。这个任务与我们的目标也是一致的：将开发者从各种底层技术中抽象出来（我要再强调一遍，不是孤立出来），比如 Jenkins、Docker、Kubernetes、Terraform，并提供简单方便的可视化工具用来配置环境和 CI/CD pipeline。

What this means in practice:

-   Configuring, generating and publishing Docker images
-   Configuring environments, e.g. test and production
-   Describing required infrastructure using a visual designer - based on Kubernetes and Terraform
-   Configuring CI/CD pipelines

也就是说我们要实现：

-   配置、生成以及发布 Docker 镜像
-   配置环境，比如测试和生产环境
-   使用可视化设计器描述需要的基础设施，基于 Kubernetes 和 Terraform
-   配置 CI/CD pipeline

We are planning to rely on public clouds infrastructure - AWS to start with - for part of these features. But AWS (Azure, Alibaba, etc) offers so much more than just hosting your app, that it would be a crime to ignore its capabilities! So we will give you a choice to build truly cloud-native applications on top of cloud services including database, file storage, authentication, full text search, monitoring, logging, load balancing, etc.
对于这些功能，我们计划将来会依赖公有云的基础设施，从 AWS 开始。但是 AWS（或者 Azure、Alibaba 等）除了能让你部署 App 之外还提供了很多功能，如果我们忽略这些云平台功能的话，感觉就是在犯罪！因此，你可以选择构建基于这些云服务的真正云原生应用程序，包括数据库、文件存储、认证、全文检索、监控、日志、负载均衡等。

The ultimate goal is to provide you everything to deploy and run your applications in the cloud with minimal efforts. As this is an absolutely new direction, it is hard to declare deadlines. But we are aiming to release a beta version at the end of 2021.
我们的终极目标是为你提供所有需要部署的内容，然后以最小的人力开销在云环境运行你的应用程序。这是一个全新的方向，我们很难给出 deadline。但是我们希望能在 2021 年底推出 Beta 版本。

### Tools

### 工具

Studio team is gradually becoming the largest in Jmix. Indeed, every direction, be it cloud or frontend, assumes relevant tooling support on the Studio side. In addition, we want to introduce some important enhancements this year:

-   New visual designers - for JPQL and GraphQL queries, string messages and simple logical expressions. I hope everyone will love the idea of not having to write JPQL strings!
-   Code generation based on templates for typical actions: open a screen, save/load data, show message, invoke a service, start a business process.
-   Visual reports configuration at design-time.
-   BPM processes configuration at design-time.

Studio 团队逐渐成为了 Jmix 中最大的团队。确实，无论哪个方向，云也好，前端也好，都需要 Studio 提供相关的工具支持。今年，我们想提供一些更重要的功能：

-   新的可视化设计器，支持 JPQL 和 GraphQL 查询、字符串消息和简单的逻辑表达式。我希望所有人都喜欢不需要书写 JPQL 语句的想法！
-   基于典型操作模板的代码生成：打开一个界面、保存/加载数据、显示消息、调用服务、启动工作流。
-   设计时的可视化报表配置。
-   设计时的 BPM 流程配置。

### Moving things to design-time

### 将一些内容迁移至设计时

I would like to highlight the last two features. Up till now, both Reporting and BProc addons only supported configuration at runtime. From one point of view, this is great: reports and business processes can be configured by non-developers without the need to redeploy the application. However, this has a number of side effects:

-   If the data model changes, your report or business process may stop working, and you will not even notice it until you run it.
-   Instances of reports and business processes might easily get out of sync between different installations of an application. You may be testing one version on the test stand, at the same time someone changes something in production…
-   For complex reports, a developer has to use inconvenient runtime code editors.
-   When configuring a business process, a developer has to switch back and forth between Studio and a running application with frequent restarts to add new forms, services, etc.

我想要着重说说最后两个功能。目前为止，报表和 BProc 扩展只支持运行时配置。从某一方面看，这很棒：非开发人员可以配置报表和工作流，而且也不需要重新部署程序。但是这又有一些副作用：

-   如果数据模型修改了，配置的报表和工作流可能会无法正常工作，但直到运行时才知道有问题。
-   在多次安装应用程序升级后，报表和工作流的实例可能很容易不同步。比如你在测试环境测的是一个版本，但是生产环境有人配置了另一个版本...
-   对于复杂的报表，开发者不得不使用不方便的运行时代码编辑器。
-   当需要配置工作流时，开发者不得不在 Studio 和运行的程序之间切换，还得频繁的重启，以便添加新的表单、服务等。

All in all, this becomes a fragile and cumbersome process, leaving lots of room to errors. Considering this, we decided to implement BPM and report designers in Studio.
The option to build reports and edit business processes at runtime will also be preserved. You may notice that this is inline with the recently implemented design time support for access groups and security roles.
总的来说，这个流程很脆弱也很笨重，为犯错误留下了太多空间。考虑到这点，我们决定在 Studio 实现 BPM 和报表设计器。但是我们还会保留运行时构建报表和工作流的能力。你可能已经注意到，这个方法和我们最近实现的设计时访问组和安全角色一致。

For reports, this means that a report is becoming a Java class, configured using a Studio wizard. This enables compile time validation, ability to test and debug reports and better visual tools.
对于报表，一个报表就变成了一个 Java 类，使用 Studio 向导配置。这样的话，能引入编译时检查，并能测试和调试报表，也方便提供更好的可视化设计器。

For BPM, the idea is similar. Design-time editor will enable testing and debugging process definitions, as well as creating many things inline: services, forms, handlers and so on. This will result in a seamless developer environment, powerful enough to compete with some BPMS solutions on the market.
对于 BPM，思路也类似。设计时的编辑器能对流程定义进行测试和调试，并能一并创建其他相关的内容：服务、表单、处理器等等。这样的无缝开发环境足以与市场上的某些 BPMS 解决方案相竞争。

As many other features, we are aiming to release a beta version of these new tools at the end of 2021.
与其他功能一样，我们也计划在 2021 年底发布这些工具的 Beta 版本。

### Timeline

### 时间线

Here is the timeline to summarize the expected releases for your convenience:
为方便起见，这里总结一下各个发布版本的时间线：

-   Q2 2021 - stable version of Jmix
-   Q4 2021 - stable version of the React client
-   Q4 2021 - beta versions of:
    &nbsp;&nbsp;&nbsp;&nbsp;- DevOps and Cloud tools
    &nbsp;&nbsp;&nbsp;&nbsp;- cloud native applications support
    &nbsp;&nbsp;&nbsp;&nbsp;- visual reports and business processes configuration at design time
    &nbsp;&nbsp;&nbsp;&nbsp;- other tools in Studio
-   Q2 2022 - stable versions of everything released in Q4 2021

-   Q2 2021 - Jmix 稳定版
-   Q4 2021 - React 客户端稳定版
-   Q4 2021 - 以下内容 Beta 版：
    -   DevOps 以及云工具
    -   云原生应用程序支持
    -   设计时可视化报表和工作流配置
    -   Studio 中的其它工具
-   Q2 2022 - Q4 2021 发布所有内容 Beta 版的稳定版

This is a challenging schedule and some deadlines might slip, but we are determined to do what’s possible to stick to it.
这个计划非常有挑战性，某些 deadline 可能会跳票，但是我们已经决定不惜一切投入以达到目标。

### The Future

### 未来

Implementing everything described above will mean that Jmix becomes a powerful platform for building modern enterprise applications, providing:
上面描述的所有功能都实现了的话，意味着 Jmix 将成为一个构建现代企业应用的强大的平台，支持：

-   Scalable UI for mobile and web applications
-   Cloud native capabilities and full deployment automation
-   More visual tools, facilitating productive development and easier onboarding

-   支持移动端和 Web 端的可扩展 UI
-   云原生能力以及全自动部署
-   更多的可视化工具，极速极具生产力的开发以及更加容易上手

In fact, Jmix should become a strong competitor on the blooming Low Code Application Platforms (LCAP) market. With at least the same level of productivity, Jmix addresses many of the LCAP shortcomings, so we hope it will be a fresh breeze on this controversial market.
Jmix is built for and offers a comfortable working environment for developers, while most LCAPs are focused on business users (aka “citizen” developers) and hence provide poor developer experience. Jmix is also open and flexible enough to build even the most complex applications like ERPs - this fact has been proven multiple times by our community projects. Finally, unlike most LCAPs, it is built around an open source framework - meaning that your applications are truly yours.

事实上，Jmix 应该是低代码应用程序平台（LCAP）市场中的一个强有力的竞争者。至少除了差不多高效的生产力外，Jmix 还弥补了很多 LCAP 的短板，所以我们希望 Jmix 能为这个具有争议的市场带来一股清风。
Jmix 是为开发者提供舒适的工作环境而构建的，而大部分 LCAP 专注于为业务用户（又称为 “市民” 开发者）服务，开发者体验并不好。同时，Jmix 是开放的，而且足够灵活，甚至可以用来构建最复杂的应用程序，比如 ERP，这个能力已经被我们社区中的项目多次证明。最后，与众多 LCAP 不同，Jmix 是构建在开源框架之上，意味着你的应用程序完全属于你。

We hope that this combination of Jmix features will help you deliver powerful yet beautiful applications in record time, and will be attracting new members to our community. As usual, your feedback is much appreciated - feel free to leave your comments on the forum or contact us directly.
我们希望这些 Jmix 的功能组合能帮助你及时交付功能强大而且界面美观的应用程序，能为我们的社区吸引更多的成员。与往常一样，我们非常期待你的反馈，可以在论坛发言或者直接联系我们。
