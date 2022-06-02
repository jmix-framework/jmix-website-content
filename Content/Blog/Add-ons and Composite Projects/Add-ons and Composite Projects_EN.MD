# Add-ons and Composite Projects

In this article, we explore what is an add-on and how Jmix Studio helps developing add-ons and modular applications. 

The concept of add-ons plays significant role in development with Jmix framework. In this article, we explore what is an add-on and how Jmix Studio helps developing add-ons and modular applications. 

An add-on in Jmix is a fancy word for a library, that is a collection of pre-compiled code and other resources that can be used in applications. We use the specific term “add-on” to emphasize that this library, unlike a Java library in general, follows particular rules and leverages some Jmix core features to automatically integrate provided functionality into the host application.  

The most important thing is that an add-on is full-stack: it can contain entities, database schema and UI screens that seamlessly integrate into the data model and UI of the application. So just by adding an add-on as a dependency to `build.gradle`, you can get a whole new subsystem in your project, with data stored in your database and UI integrated with the main menu.  

An add-on doesn’t have to be a complex full-stack project. Many add-ons just provide a UI feature or an alternative implementation of some framework interface like `FileStorage`. In this case, the add-on can just utilize the common infrastructure for publication on <a href="https://www.jmix.io/marketplace/" target="_blank">Marketplace</a> and for easy installation to projects. 

## Developing Add-ons 

Jmix Studio provides the “Single Module Add-on” project template that allows you to quickly bootstrap the development of an add-on. The project will contain a single functional module and a Spring Boot Starter.  

When working on a reusable add-on, you usually have to create also an application which demonstrates use cases for the add-on, and may contain additional automatic tests that are difficult to create in the add-on project itself. 

Studio now offers a feature to streamline the development of such modularized systems. But before looking at it, let’s consider the previous development workflow. 

Generally, the work on an add-on and an application which uses it requires constant switching between two projects. You need to change the add-on's code, build it and publish to the local Maven repository. Then you switch to the application project and IDE loads and reindexes the new add-on artefacts. Now you can adjust the application code, test and run it to see the changes in action. 

![Feedback Loop 1.drawio.svg]({{strapiUrl}}/uploads/Feedback_Loop_1_drawio_bfdcf3761d.svg)

The situation gets worse when you work on an application consisting of multiple add-ons. Most probably, some of your add-ons depend on each other, and you need to switch between several projects and publish multiple add-ons before you can run your application and make sure you got what you wanted. If you failed, you have to repeat the process again. 

![Feedback Loop 2.drawio.svg]({{strapiUrl}}/uploads/Feedback_Loop_2_drawio_36e9edf509.svg)

The feedback loop when developing add-ons was far from ideal: you have to make too many steps to see the result of your changes. The obvious solution would be to combine both the add-on and the runnable application as modules of a single project. On one hand, an IDE then could provide transparent refactoring and you could instantly see the results of changes in any module. On the other hand, the add-ons and applications become tightly coupled for their entire lifecycle, and the idea of an add-on as a standalone library becomes meaningless. 

Wouldn’t it be great if we could work with the add-ons and applications both in separate projects and in a single project when needed? It allows us to keep the codebase clean and manageable, while not sacrificing the short feedback loop when it’s important, especially on the early stages of development when cross-cutting changes are very frequent.  

This is why we improved Jmix Studio to support this scenario with the Gradle’s “composite build”. 

## Composite Projects 

Gradle has several features that help structuring projects, and one of them is <a href="https://docs.gradle.org/current/userguide/composite_builds.html" target="_blank">composite build</a>. It boils down to just using `includeBuild` instruction in the `settings.gradle` file of the composite project: 

```
includeBuild ‘../addon1’ 
includeBuild ‘../addon2’  
includeBuild ‘../myapp’ 
```

In a composite build, Gradle replaces dependencies on artefacts with direct dependencies between subprojects, so changes in an add-on will immediately affect the dependent add-ons and the application. IntelliJ IDEA perfectly imports such a project, taking into account dependencies recognized by Gradle. As a result, you get a composite project which provides the transparent refactoring and removes the need to go through the "publish locally" cycle. 

Jmix Studio supports composite projects starting from version 1.2. It brings to the table a number of features that improve the developer experience even further.  

First of all, you can easily create an empty composite project from a template. Then you can add subprojects by creating new add-ons or applications, checking out an existing project from VCS or just adding an existing folder with a project. 

Studio shows the composite project and all subprojects as top-level nodes in the Jmix tool window: 

![jtw1.png]({{strapiUrl}}/uploads/jtw1_fb9391416f.png)

You can edit common properties of all subprojects: just select **All subprojects** when Studio asks you which project you want to edit: 

 ![edit-properties.png]({{strapiUrl}}/uploads/edit_properties_f19add527a.png)

The common properties include the artifact repository settings and Jmix framework version. So you can upgrade all subprojects to a newer Jmix version at once. 

Probably the most useful feature for large composite projects is the ability to configure dependencies between subprojects in a simple dialog: 

![deps1.png]({{strapiUrl}}/uploads/deps1_655e33a97e.png)

Here **orders** is an add-on which depends on the **staff** and **customers** add-ons. According to changes you make in this dialog, Studio adds artefact dependencies to `build.gradle` files of the subprojects, and also configures the `@JmixModule` annotations of the add-ons. It also prevents you from introducing circular dependencies. In the screenshot below you can see that the dialog doesn’t allow you to make the **customers** add-on dependent on **orders** because **orders** already depends on **customers**: 

![deps2.png]({{strapiUrl}}/uploads/deps2_18c5ae5f9c.png)

When you create new project elements like entities and screens, Studio considers what project is currently selected in the Jmix tool window: 

 ![new-entity.png]({{strapiUrl}}/uploads/new_entity_da72b2d070.png)

The last but not least, Studio correctly hot deploys changes in add-ons to the running application. So if you start the application and then change a UI screen provided by an add-on, you will see the changes in the application without restarting it, as if the screen was in the application’s source code. 

Summing up, it can be said that Gradle’s composite build feature together with IntelliJ IDEA and Jmix Studio support for it allows developers to work with large families of add-ons and applications as with a single multi-module application. At the same time, the developer can detach an add-on at any moment and continue maintaining as a completely separate project. 


