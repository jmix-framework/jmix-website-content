# IMAP

## Overview

The add-on provides integration of email messaging into any Jmix-based application via IMAP protocol. The component is designed to interact with incoming emails via Spring application events.

You can manipulate email boxes, handle emails, view and retrieve emails, search through them and operate with custom IMAP flags.

## Features

- Integration with any IMAP server
- API methods to connect to IMAP server and operate with emails
- User interface to configure IMAP connection, browse messages and events settings
- Predefined events for various updates processing

## Installation

To include the add-on into your application, add the following lines to the dependencies section of your build.gradle file:

```
dependencies {
    // ...
    implementation 'io.jmix.imap:jmix-imap-starter'
    implementation 'io.jmix.imap:jmix-imap-ui-starter'
    // ...
```

## Links

GitHub: [https://github.com/haulmont/jmix-imap](https://github.com/haulmont/jmix-imap)



# GrapesJS

## Overview

The add-on provides a visual HTML editor based on a [GrapesJS](https://grapesjs.com/) JavaScript library with the extensive set of HTML elements. It allows building HTML templates without any knowledge of coding.

All you need is to drag an element into the canvas. The wide range of options enables independent styling of any element inside the canvas.

Tree of elements is always available to control the structure. Also, you can edit HTML code manually or upload code from the file.

## Features

- Wide variety of built-in HTML elements.
- Viewing representation for different devices.
- Using CSS properties.
- Downloading/uploading HTML code.

## Installation

To include the add-on into your application, add the following lines to the dependencies section of your build.gradle file:

```
dependencies {
    // ...
    implementation 'io.jmix.grapesjs:jmix-grapesjs-starter'
    // ...
```

## Links

GitHub: [https://github.com/Haulmont/jmix-grapesjs](https://github.com/Haulmont/jmix-grapesjs)



# BPM

The BPM add-on provides seamless integration of a BPM engine into your project, extending it with multiple powerful features.

The add-on allows you to describe business process steps right in the application using the integrated BPMN 2.0 modeler. Being a part of the application, it enables seamless integration with the runtime application parts and visual process customizing. For example, to specify which service method should be invoked at a particular process step, you just need to select a Spring bean name and a method from a drop-down list.

Users may interact with running process instances using process forms. For simple cases, you can declare input dialogs right in the modeler. Also, you can use screens based on Jmix backoffice UI to create process forms of any complexity.

## Features

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

## Installation

To include the add-on into your application follow the steps described in the documentation:  [https://docs.jmix.io/jmix/0.x/bpm/index.html#_installation](https://docs.jmix.io/jmix/0.x/bpm/index.html#_installation)

## Links

Documentation: [https://docs.jmix.io/jmix/0.x/bpm/index.html](https://docs.jmix.io/jmix/0.x/bpm/index.html)




# AWS File Storage

## Overview

The add-on provides a FileStorage implementation that stores data backed by file references in [Amazon S3](https://aws.amazon.com/s3/) storage.

## Installation

To include the add-on into your application, add the following lines to the dependencies section of your build.gradle file:

```
dependencies {
    // ...
    implementation 'io.jmix.awsfs:jmix-awsfs-starter'
    // ...
```

## Links

GitHub: [https://github.com/Haulmont/jmix-awsfs](https://github.com/Haulmont/jmix-awsfs)




# Charts

## Overview

The charts module is based on the [amCharts](https://www.amcharts.com/) library and includes various types of dynamic charts: basic charts such as pie chart, bar chart, serial chart, funnel, etc as well as advanced charts - stock chart and Gantt chart.

## Installation

To include add-on into your application, add the following lines to the dependencies section of your build.gradle file:

```
dependencies {
    // ...
    implementation 'io.jmix.ui:jmix-charts-starter'
    // ...
```

## Links

GitHub: [https://github.com/Haulmont/jmix-ui](https://github.com/Haulmont/jmix-ui/)





# Pivot Table

## Overview

The add-on provides a PivotTable UI component based on [PivotTable.js](https://github.com/nicolaskruchten/pivottable) library. The table component enables turning a data set into a summary table and manipulating it using 2D drag-and-drop UI.

## Installation

To include add-on into your application, add the following lines to the dependencies section of your build.gradle file:

```
dependencies {
    // ...
    implementation 'io.jmix.ui:jmix-pivot-table-starter'
    // ...
```

## Links

GitHub: [https://github.com/Haulmont/jmix-ui](https://github.com/Haulmont/jmix-ui/)

