# Jmix 1.3 Is Released

## The new Jmix version 1.3 has been released recently. In this article, I will highlight the most important updates introduced in this feature release.

The new Jmix version 1.3 has been released recently. In this article, I will highlight the most important updates introduced in this feature release.

As usual, for the full information on changes and upgrade instructions, check out the <a href="https://docs.jmix.io/jmix/1.3/whats-new/index.html" target="_blank">What's New</a> page of the documentation.

## Java 11 Is Required

Probably the most important thing to note before upgrading is that Java 8 is not supported anymore. The framework is now built with Java 11, so you have to use Java 11 or above to build and run your applications.

The main motivation for abandoning Java 8 was introducing of the experimental FlowUI module based on Vaadin 23 (see below), which required Java 11. We decided that it's time to move on and also enjoy little language and standard library enhancements available in Java 11.

## Flow UI Preview

As promised, we released a preview version of the new UI module based on Vaadin 23. It's called FlowUI and it will allow you to create nice responsive interfaces with easy frontend customization:

![]({{strapiUrl}}/uploads/2022_07_07_flowui_responsive_e0e4018057.gif)

FlowUI will follow the same paradigm as the current UI: server-side programming model, XML layout with visual designer in Studio, data components, similar Java API. But at the same time the set of UI controls and layout rules will be completely different, so please don't expect an effortless migration in the future.

At the moment, the module and its support in Studio are very unstable. We are going to introduce significant and probably breaking changes in subsequent patches of the release 1.3. 

The goal of the current preview is to give community an idea of how the new UI will look, and to start getting feedback on required features and priorities. We hope that by the next feature release in October, 2022, we'll be able to deliver a stable API and a set of minimal functionality for building real applications with the new UI.

## One-Click Cloud Deployment Preview

Another preview feature is the ability to deploy application to AWS EC2 cloud. To see it in action, enable it as described in the <a href="https://docs.jmix.io/jmix/whats-new/index.html#one-click-cloud-deployment" target="_blank">documentation</a>.

![]({{strapiUrl}}/uploads/2022_07_07_aws_deployment_e4b9614a1a.png)

This feature allows you to quickly deploy your application to the cloud. It generates a `docker-compose` file with services based on your application and database settings, creates a virtual machine on AWS EC2, installs Docker on it and builds a Docker image with your application on the VM. Then it runs the containers, gives you the URL, and voila - your application is running in AWS and available to the whole world!

We think that this feature can help a lot when a developer needs to demonstrate the application to clients or colleagues, or just for a simple and lightweight deployment.

## Studio Improvements

We now consider the JPQL designer reliable enough for editing existing queries. It is opened when you click on the query attribute of a data container in the Component Inspector tool window. You can also open the designer for queries defined in code using the gutter icon.

![]({{strapiUrl}}/uploads/2022_07_08_jpql_1_8e5fc51a83.gif)

There are a number of improvements related to Liquibase changelogs: 

- Studio now shows existing Liquibase changelog files in the Jmix tool window under the Data Store node.
- You can create a new empty changelog file using the action of the Jmix tool window and write changesets manually with the help of code completion which suggests names of tables and columns defined in your entities.
- File names of new changelogs now include the timestamp in the HHmmss format (instead of previously added sequential numbers 010, 020, …​). It should eliminate duplication of changelogs when switching VCS branches.

![]({{strapiUrl}}/uploads/2022_07_08_lbcl_1_3938862131.gif)

## BPM Improvements

We have put a lot of effort into improving the BPMN designer in Studio, so now we think it's a good alternative to the runtime designer, offering the tight integration with your source code.

![]({{strapiUrl}}/uploads/2022_07_08_bpm_e5f3355165.gif)

Also, the BPM engine now integrates with the Multitenancy add-on if it is used in the project.

## Role Management

Resource and row-level role management screens now have filters for quick search when editing roles or assigning them to users. Export/import actions allow you to transfer the roles configuration between application instances.

![]({{strapiUrl}}/uploads/2022_07_08_role_filter_7f462b7b5e.png)

Row-level policy editor now offers code completion for JPQL, Check syntax action and link to documentation.

![]({{strapiUrl}}/uploads/2022_07_08_row_level_policy_add36702b0.gif)

## Support for JPA Cascade

As a matter of following standards, we've implemented full support for JPA cascade operations, defined in annotations like `@ManyToOne(cascade = CascadeType.ALL)`. All Jmix features (entity events, dynamic attributes, entity log, security, cross-datastore references) take effect for entities saved through the cascasde operations.

## What's next?

The main direction in the upcoming months is to stabilize FlowUI module, add necessary UI components and build UI for the essential parts of the framework, such as the security subsystem. 

We are also constantly working on fixing issues in the current release 1.3. Patches 1.3.x will be released approximately once a month. 

We'll be glad to see your feedback on our [forum](https://forum.jmix.io)!
Thanks to all who contributed with their ideas, suggestions and bugreports! 