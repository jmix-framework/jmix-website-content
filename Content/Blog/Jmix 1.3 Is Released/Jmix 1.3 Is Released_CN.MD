# Jmix 1.3 Is Released
# Jmix 1.3 版本发布

## The new Jmix version 1.3 has been released recently. In this article, I will highlight the most important updates introduced in this feature release.
## 最近我们发布了 Jmix 的一个新功能版本 1.3.0。本文中，我们将介绍该升级版本中包含的一些重要功能。

The new Jmix version 1.3 has been released recently. In this article, I will highlight the most important updates introduced in this feature release.
最近我们发布了 Jmix 的一个新功能版本 1.3.0。本文中，我们将介绍该升级版本中包含的一些重要功能。

As usual, for the full information on changes and upgrade instructions, check out the <a href="https://docs.jmix.io/jmix/1.3/whats-new/index.html" target="_blank">What's New</a> page of the documentation.
与往常一样，新版本改动的完整信息和升级说明我们都发布在文档的 <a href="https://docs.jmix.cn/jmix/whats-new/index.html" target="_blank">最近更新</a> 页面。

## Java 11 Is Required
## 必须使用 Java 11

Probably the most important thing to note before upgrading is that Java 8 is not supported anymore. The framework is now built with Java 11, so you have to use Java 11 or above to build and run your applications.
在升级这个新版之前，需要注意的最重要一点就是，新版本不再支持 Java 8。框架使用 Java 11 构建，因此需要升级至 Java 11 或以上版本才能构建并运行应用程序。

The main motivation for abandoning Java 8 was introducing of the experimental FlowUI module based on Vaadin 23 (see below), which required Java 11. We decided that it's time to move on and also enjoy little language and standard library enhancements available in Java 11.
不支持 Java 8 的主要原因是因为引入了基于 Vaadin 23 的试验性 FlowUI 模块，这个模块要求 Java 11。因此，我们觉得该是时候跟 Java 8 说再见了，使用新的 Java 版本也可以让我们能享受一些语言和标准库的改进。

## Flow UI Preview
## Flow UI 预览

As promised, we released a preview version of the new UI module based on Vaadin 23. It's called FlowUI and it will allow you to create nice responsive interfaces with easy frontend customization:
我们实现了 Roadmap 中对于新 UI 的承诺，在新版本发布了基于 Vaadin 23 的预览。新的 UI 叫做 FlowUI，支持通过简单的前端自定义创建响应式布局：

![]({{strapiUrl}}/uploads/2022_07_07_flowui_responsive_e0e4018057.gif)

FlowUI will follow the same paradigm as the current UI: server-side programming model, XML layout with visual designer in Studio, data components, similar Java API. But at the same time the set of UI controls and layout rules will be completely different, so please don't expect an effortless migration in the future.
使用 FlowUI 也会遵循与当前 UI 同样的开发模式：服务端编程模式、使用 Studio 可视化设计的 XML 布局、数据容器以及相似的 Java API。但同时，UI 组件的控制和布局规则将会完全不同。所以，不要期望将来能做无缝迁移。

At the moment, the module and its support in Studio are very unstable. We are going to introduce significant and probably breaking changes in subsequent patches of the release 1.3. 
此时，该模块本身和 Studio 对该模块的支持都非常不稳定。我们将在 1.3 后续的补丁版本中引入相当大的改动甚至破坏性改动。

The goal of the current preview is to give community an idea of how the new UI will look, and to start getting feedback on required features and priorities. We hope that by the next feature release in October, 2022, we'll be able to deliver a stable API and a set of minimal functionality for building real applications with the new UI.
当前提供预览的主要目的是给社区展示新 UI 是什么样的，以及通过这个展示向大家收集更多关于功能和开发优先级的反馈。希望在 2022 年 10 月推出的下一个功能版本中，我们能提供稳定的 API 以及使用新 UI 构建真正应用的最小完整功能。

## One-Click Cloud Deployment Preview
## 一键云部署预览

Another preview feature is the ability to deploy application to AWS EC2 cloud. To see it in action, enable it as described in the <a href="https://docs.jmix.io/jmix/whats-new/index.html#one-click-cloud-deployment" target="_blank">documentation</a>.
另一个预览功能是支持将应用程序部署至 AWS EC2 云环境。如果希望试一试，需要按照 <a href="https://docs.jmix.cn/jmix/whats-new/index.html#one-click-cloud-deployment" target="_blank">文档</a> 的说明启用该功能。

![]({{strapiUrl}}/uploads/2022_07_07_aws_deployment_e4b9614a1a.png)

This feature allows you to quickly deploy your application to the cloud. It generates a `docker-compose` file with services based on your application and database settings, creates a virtual machine on AWS EC2, installs Docker on it and builds a Docker image with your application on the VM. Then it runs the containers, gives you the URL, and voila - your application is running in AWS and available to the whole world!
该功能支持将你的应用程序快速部署至云环境。过程中，会使用基于应用程序的服务和数据库配置生成 `docker-compose` 文件，然后在 AWS EC2 上创建一个虚拟机，在虚拟机中安装 Docker 并用你的应用程序构建一个 Docker 镜像。最后会运行 Docker 容器，并为你提供应用程序的 URL。至此完成整个部署过程，应用程序直接可以在互联网访问！

We think that this feature can help a lot when a developer needs to demonstrate the application to clients or colleagues, or just for a simple and lightweight deployment.
由于这个功能目前只是简单部署（不涉及集群、负载均衡等），所以可以用在为客户或同事演示应用程序或者简易轻量级部署的场景。

## Studio Improvements
## Studio 改进

We now consider the JPQL designer reliable enough for editing existing queries. It is opened when you click on the query attribute of a data container in the Component Inspector tool window. You can also open the designer for queries defined in code using the gutter icon.
这一版中，JPQL 设计器已经足够稳定，可以用来编辑查询语句。在 Jmix 工具窗口中的组件探查器（Component Inspector）中点击数据容器的 query 属性时会自动打开。也可以通过装订线栏的图标为代码中定义的查询语句手动打开设计器。

![]({{strapiUrl}}/uploads/2022_07_08_jpql_1_8e5fc51a83.gif)

There are a number of improvements related to Liquibase changelogs: 
而针对 Liquibase 生成更改日志方面，则有以下改进：

- Studio now shows existing Liquibase changelog files in the Jmix tool window under the Data Store node.
- You can create a new empty changelog file using the action of the Jmix tool window and write changesets manually with the help of code completion which suggests names of tables and columns defined in your entities.
- File names of new changelogs now include the timestamp in the HHmmss format (instead of previously added sequential numbers 010, 020, …​). It should eliminate duplication of changelogs when switching VCS branches.

- Studio 支持在 Jmix 工具窗口的 Data Store 节点下展示已有的更改日志文件
- 可以通过 Jmix 工具窗口的操作新建空的更改日志文件，然后通过代码自动完成功能手动写入变更集，代码自动完成功能支持对实体中定义的表名和列名自动提示。
- 新的更改日志文件名现在包含 HHmmss 格式的时间戳（而不是之前用的 010，020 这样的序列号）。这样可以在切换代码分支时避免更改日志名称重复。

![]({{strapiUrl}}/uploads/2022_07_08_lbcl_1_3938862131.gif)

## BPM Improvements
## BPM 改进

We have put a lot of effort into improving the BPMN designer in Studio, so now we think it's a good alternative to the runtime designer, offering the tight integration with your source code.
我们花了很多努力用于提升 Studio 中的 BPMN 设计器，现在它已经和运行时的设计器功能相当，提供与源代码的紧密集成。

![]({{strapiUrl}}/uploads/2022_07_08_bpm_e5f3355165.gif)

Also, the BPM engine now integrates with the Multitenancy add-on if it is used in the project.
另外，如果项目中用到了多租户扩展组件，BPM 引擎也支持与其集成提供多租户工作流功能。

## Role Management
## 角色管理

Resource and row-level role management screens now have filters for quick search when editing roles or assigning them to users. Export/import actions allow you to transfer the roles configuration between application instances.
在资源和行级角色管理界面添加了过滤器组件，支持在编辑、分配角色时进行快速搜索。还增加了导入导出功能按钮，支持在不同的应用程序间共享角色配置。

![]({{strapiUrl}}/uploads/2022_07_08_role_filter_7f462b7b5e.png)

Row-level policy editor now offers code completion for JPQL, Check syntax action and link to documentation.
行级策略编辑器现在提供针对 JPQL 语句的代码完成功能、语法检查操作以及文档链接操作。

![]({{strapiUrl}}/uploads/2022_07_08_row_level_policy_add36702b0.gif)

## Support for JPA Cascade
## 支持 JPA 级联

As a matter of following standards, we've implemented full support for JPA cascade operations, defined in annotations like `@ManyToOne(cascade = CascadeType.ALL)`. All Jmix features (entity events, dynamic attributes, entity log, security, cross-datastore references) take effect for entities saved through the cascasde operations.
为了更好地遵循标准，我们实现了对 JPA 级联操作（通过 `@ManyToOne(cascade = CascadeType.ALL)` 注解定义）的完整支持。为所有通过级联操作保存的实体提供所有 Jmix 功能的支持，包括实体事件、动态属性、实体日志、安全控制、跨数据存储引用。

## What's next?
## 后续计划

The main direction in the upcoming months is to stabilize FlowUI module, add necessary UI components and build UI for the essential parts of the framework, such as the security subsystem. 
我们未来几个月的主要方向是 FlowUI 模块的稳定性，包括添加必要的 UI 组件和为框架中的基础部分构建 UI，比如安全子系统。

We are also constantly working on fixing issues in the current release 1.3. Patches 1.3.x will be released approximately once a month. 
我们也会持续地为 1.3 提供问题修复。补丁版本 1.3.x 基本上会按照一个月一次的频率进行发布。

We'll be glad to see your feedback on our [forum](https://forum.jmix.io)!
Thanks to all who contributed with their ideas, suggestions and bugreports! 
希望大家在我们的[论坛](https://forum.jmix.cn)上多提意见！感谢大家提供的想法、建议以及问题报告！
