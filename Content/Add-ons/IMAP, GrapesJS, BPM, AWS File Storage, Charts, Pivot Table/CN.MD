# IMAP
# IMAP

## Overview
## 介绍 

The add-on provides integration of email messaging into any Jmix-based application via IMAP protocol. The component is designed to interact with incoming emails via Spring application events.

You can manipulate email boxes, handle emails, view and retrieve emails, search through them and operate with custom IMAP flags.

IMAP 扩展提供了将电子邮件消息与 Jmix 应用程序进行集成的功能，集成过程基于 IMAP 协议。使用该组件可通过 Spring 应用程序事件机制处理接收到的邮件。

您可以维护收件箱、处理邮件、查看并获取邮件，也可以搜索所有邮件、使用自定义 IMAP 标志。  



## Features
## 特性

- Integration with any IMAP server
- API methods to connect to IMAP server and operate with emails
- User interface to configure IMAP connection, browse messages and events settings
- Predefined events for various updates processing

-  可与任何 IMAP 服务器集成
-  提供连接 IMAP 服务器并操作邮件的 API 
-  提供配置 IMAP 连接、浏览消息和配置事件的用户界面
-  为各种更新处理提供了预定义事件

## Installation
## 安装

To include the add-on into your application, add the following lines to the dependencies section of your build.gradle file:

在 build.gradle 中将以下代码添加到 `dependencies` 部分： 

```
dependencies {
    // ...
    implementation 'io.jmix.imap:jmix-imap-starter'
    implementation 'io.jmix.imap:jmix-imap-ui-starter'
    // ...
```

## Links
## 链接

GitHub: [https://github.com/haulmont/jmix-imap](https://github.com/haulmont/jmix-imap)



# GrapesJS
# GrapesJS

## Overview
## 介绍

The add-on provides a visual HTML editor based on a [GrapesJS](https://grapesjs.com/) JavaScript library with the extensive set of HTML elements. It allows building HTML templates without any knowledge of coding.

All you need is to drag an element into the canvas. The wide range of options enables independent styling of any element inside the canvas.

Tree of elements is always available to control the structure. Also, you can edit HTML code manually or upload code from the file.

此扩展提供了基于 [GrapesJS](https://grapesjs.com/) JavaScript 库的可视化 HTML 编辑器，使用该组件不需要任何编码基础就可以构建 HTML模板。

只需要拖放元素到画布，然后可以使用丰富的配置选项对页面内的元素进行样式设计。

可以通过元素树来控制模板结构。同时您也可以手工编写代码或从本地文件上传代码。


## Features
## 特性

- Wide variety of built-in HTML elements.
- Viewing representation for different devices.
- Using CSS properties.
- Downloading/uploading HTML code.

- 丰富的内置 HTML 元素
- 适应不同设备的可视化展现
- 使用 CSS 属性
- 下载/上传 HTML 代码


## Installation
## 安装

To include the add-on into your application, add the following lines to the dependencies section of your build.gradle file:

将以下代码添加到 `build.gradle` 文件的 `dependencies` 部分：

```
dependencies {
    // ...
    implementation 'io.jmix.grapesjs:jmix-grapesjs-starter'
    // ...
```

## Links
## 链接

GitHub: [https://github.com/Haulmont/jmix-grapesjs](https://github.com/Haulmont/jmix-grapesjs)



# BPM
# BPM

The BPM add-on provides seamless integration of a BPM engine into your project, extending it with multiple powerful features.

The add-on allows you to describe business process steps right in the application using the integrated BPMN 2.0 modeler. Being a part of the application, it enables seamless integration with the runtime application parts and visual process customizing. For example, to specify which service method should be invoked at a particular process step, you just need to select a Spring bean name and a method from a drop-down list.

Users may interact with running process instances using process forms. For simple cases, you can declare input dialogs right in the modeler. Also, you can use screens based on Jmix backoffice UI to create process forms of any complexity.

BPM 扩展将 BPM 引擎无缝集成到您的项目中，同时对其进行了扩展，添加了多个强大的功能。

通过这个扩展可以直接在应用程序内使用集成的 BPMN2.0 建模器对业务处理流程的各个步骤进行描述。作为应用程序的一部分，其提供了与运行时应用程序和可视化流程定制的无缝集成。比如，需要指定在特定流程步骤使用的服务方法时，您可以直接从一个下拉列表选取 Spring bean 名称和方法名。

用户可以使用流程表单与运行中的流程实例做交互。对于简单的场景，您可以直接在建模器中声明简单的输入对话框。此外，您也可以使用基于 Jmix 通用 UI 的界面来创建任何复杂度的流程表单。


## Features
## 特性

- The embedded light-weight [Flowable](https://flowable.org/) runtime engine. You are free to use the Flowable API directly, or you may use an API layer provided by the BProc addon.
- Integrated BPMN 2.0 visual designer based on [bpmn-js](https://bpmn.io/) framework.
- Integrated DMN 1.1 decision table designer for complex decision logic.
- Two types of process forms:
  a) Input dialogs that can be created at runtime in the process modeler
  b) Design-time defined backoffice UI screens
- Administrative screens for managing running processes provide a ready solution to:
  a) view all running process instances
  b) reassign user tasks
  c) modify process variables’ values
  d) investigate failed jobs
  e) analyze processes execution history, etc.
- API for working with business processes from the code.

- 内嵌了轻量级的 [Flowable](https://flowable.org/) 运行时引擎。您可以直接使用 Flowable API，或者也可以使用由 BPM 扩展提供的 API 层
- 集成了基于 [bpmn-js](https://bpmn.io/) 框架的 BPMN2.0 可视化设计器
- 集成了为复杂决策逻辑设计的 DMN1.1 决策表设计器
- 两种类型的流程表单：
  a）输入对话框-可以通过流程建模器在运行时创建
  b）设计时定义的后台 UI 界面
- 内置的运行中流程管理界面在以下方面提供了即用的解决方案：
  a）查看所有运行的流程实例 
  b）重新分配用户任务 
  c）修改流程变量的值 
  d）调查失败的任务 
  e）分析流程执行历史等
- 提供代码级处理业务流程的 API


## Installation
## 安装

To include the add-on into your application follow the steps described in the documentation:  [https://docs.jmix.io/jmix/0.x/bpm/index.html#_installation](https://docs.jmix.io/jmix/0.x/bpm/index.html#_installation)

根据以下文档将此扩展集成到您的应用程序：[https://docs.jmix.io/jmix/0.x/bpm/index.html#_installation](https://docs.jmix.io/jmix/0.x/bpm/index.html#_installation)

## Links
## 链接

Documentation: [https://docs.jmix.io/jmix/0.x/bpm/index.html](https://docs.jmix.io/jmix/0.x/bpm/index.html)

文档: [https://docs.jmix.io/jmix/0.x/bpm/index.html](https://docs.jmix.io/jmix/0.x/bpm/index.html)


# AWS File Storage
# AWS 文件存储

## Overview
## 介绍

The add-on provides a FileStorage implementation that stores data backed by file references in [Amazon S3](https://aws.amazon.com/s3/) storage.

此扩展以提供了基于 [Amazon S3](https://aws.amazon.com/s3/) 存储的文件存储实现。

## Installation
## 安装

To include the add-on into your application, add the following lines to the dependencies section of your build.gradle file:

将以下代码添加到 `build.gradle` 文件的 `dependencies` 部分：

```
dependencies {
    // ...
    implementation 'io.jmix.awsfs:jmix-awsfs-starter'
    // ...
```

## Links
## 链接

GitHub: [https://github.com/Haulmont/jmix-awsfs](https://github.com/Haulmont/jmix-awsfs)




# Charts
# 图表

## Overview
## 介绍

The charts module is based on the [amCharts](https://www.amcharts.com/) library and includes various types of dynamic charts: basic charts such as pie chart, bar chart, serial chart, funnel, etc as well as advanced charts - stock chart and Gantt chart.

Charts 模块基于 [amCharts](https://www.amcharts.com/) 库，提供了各种类型的动态图表：饼图、条状图、序列图、漏斗图等基础图表以及股票图、甘特图等高级图表。

## Installation
## 安装

To include add-on into your application, add the following lines to the dependencies section of your build.gradle file:

将以下代码添加到 `build.gradle` 文件的 `dependencies` 部分：

```
dependencies {
    // ...
    implementation 'io.jmix.ui:jmix-charts-starter'
    // ...
```

## Links
## 链接

GitHub: [https://github.com/Haulmont/jmix-ui](https://github.com/Haulmont/jmix-ui/)





# Pivot Table
# 数据透视表

## Overview
## 介绍

The add-on provides a PivotTable UI component based on [PivotTable.js](https://github.com/nicolaskruchten/pivottable) library. The table component enables turning a data set into a summary table and manipulating it using 2D drag-and-drop UI.

此扩展提供了一个基于 [PivotTable.js](https://github.com/nicolaskruchten/pivottable) 库的 PivotTable UI 组件。 PivotTable 组件允许旋转数据集为汇总表格，同时可以使用 2 维拖拽 UI 来操作数据。

## Installation
## 安装

To include add-on into your application, add the following lines to the dependencies section of your build.gradle file:

将以下代码添加到 `build.gradle` 文件的 `dependencies` 部分：

```
dependencies {
    // ...
    implementation 'io.jmix.ui:jmix-pivot-table-starter'
    // ...
```

## 链接

GitHub: [https://github.com/Haulmont/jmix-ui](https://github.com/Haulmont/jmix-ui/)

