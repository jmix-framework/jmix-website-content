### Jmix - the future of CUBA Platform 

CUBA started its way back in 2008. Since then it went through a few very important stages. At first it was an internal framework with no documentation and even less API. It was a company-wide thing that allowed Haulmont to develop Business Applications faster. 

## TL;DR 

Jmix is the new name and the new major release of CUBA Platform. It is now in Preview and we are aiming to release Stable version in Q2 2021. Key features:
- Spring Boot as a core technology
- Decomposition into separate pluggable modules (data, security, audit, etc.) 
- A new approach to data model definition
- Database update process based on Liquibase
- Deployment approach utilizing Spring Boot features, allowing better integration with cloud environments.

We will be focused on simplifying ReactJS client development. Meanwhile, we will keep the current Vaadin-based client UI, which will become one of the Jmix modules.

CUBA Platform will be supported for a long time and we are providing a migration path to Jmix via compatibility APIs.

Check the preview release of Jmix on [jmix.io](https://www.jmix.io/). Discuss the new release in the special [forum category](https://www.cuba-platform.com/discuss/c/jmix). 

 
## Introduction

CUBA started its way back in 2008. Since then it went through a few very important stages. At first it was an internal framework with no documentation and even less API. It was a company-wide thing that allowed Haulmont to develop Business Applications faster. 

In 2015 CUBA was introduced world-wide under a proprietary license. We got just a few users that year - that was embarrassing. It became obvious that the licensing policy should be switched to open source. 

2016 and 2017 were very productive years when we got our wider community. This was a big shift in mind, we saw what was right and what was wrong.

 In 2018-2019 we started to introduce a clear and well-documented API level and moved CUBA Studio onto IntelliJ. All that brought an even bigger community with even more feedback. Now we are staying at the border of the next major update. Let's dive into and see what will come in 2021.

## New version objectives

In the next version of CUBA Platform we wanted to do the following:
1. Make developer’s experience closer to the most popular frameworks. CUBA Platform uses Spring, but nowadays Spring Boot has almost conquered the world. New frameworks are emerging - Micronaut and Quarkus. They all have similar principles at its core: simple configuration via .properties or .yaml files, extensive annotation usage, and simple add-on connection and configuration. So we want CUBA to give a similar experience to developers.
2. Do not reinvent the wheel. Since 2008 a lot of new libraries and tools have been developed. Now they are mature and can be used for enterprise-grade applications. So we wanted to replace some custom CUBA’s modules with battle-proven libraries. As an example - database migration system.
3. Make CUBA applications smaller. When creating applications with CUBA, you don’t always need all the features like audit. But it always has been a part of the framework core, polluting the database with unnecessary (for your particular case) tables and starting extra services on your app server. So, it would be nice to have the ability to exclude some CUBA features and include them only when necessary.
4. And the most important thing - keep great experience and application development speed.
 
And the first thing that we will start from is...

## Naming

“What does CUBA stand for?” - It's hard to count how many times we have been asked this question. Honestly, it was just a name not too long and not too short to name the first package of our internal framework back in 2008. If you dig into CUBA core, you can also find “chile” and “bali” packages. 

In 2021 we’re going to release a new major version - and the name will change. “CUBA” becomes “Jmix”. This name is much simpler to explain: “J” for “Java” and “mix” for the technologies and frameworks mix in one application. Less questions, no associations neither with the well-known island nor with the well-known alcohol cocktail. 

Effectively Jmix is the next major CUBA version with well-known APIs and development approach. And it is still the same set of convenient tools and code generators. 

But renaming, which is a big part, also shows a big change in the...

## Core technology

In a wide sense, in CUBA we were copying some of Spring Boot approaches. Our own session storage, security subsystem, auth… and of course deployment. Also, CUBA add-ons were introduced as a response to Boot starters with their own encapsulation and autoconfiguration mechanism.

When we started CUBA development back in 2008, we used “pure” Spring in the framework core. In Jmix we will use Spring Boot as our core technology. 

Using Spring Boot gives us the following advantages:

1. Better developer experience. Currently almost every Java developer is familiar with Spring Boot. With Jmix, Spring Boot development experience can be used at its full, no need to learn a new framework, just new starters.
2. As for starters, Spring Boot - based core allows us using almost all existing starters in our framework. So, we can rely on existing infrastructure with huge community support and tremendous documentation base.
3. And one more thing - Spring Boot has great features regarding deployment, including great containerization support, out-of-the box. 

When mentioning Spring Boot starters, we cannot forget CUBA add-ons. And this brings us to...

![text]({{strapiUrl}}/uploads/c1a763a2f95443c1821b4275b7e4eea3_662b98d9f2.png)

## Modularization

From time to time we get feedback that an “empty” CUBA application that does not contain a single line of a business logic has too many tables and a lot of functional pieces that are never used. 
In the 7th version of the framework, we started extracting core functionality to separate add-ons. Basically, CUBA is a set of APIs, and this approach provided enough flexibility to be able to continue the modularization process. 

Starting from Jmix, you can use the features of the framework (e.g. audit, security) separately and almost independently. All features are now provided as Spring Boot starters.  For example, there was an audit functionality in CUBA, which is now a separate module in Jmix. And this module in its turn is split into Core and UI modules. It means that you can use the audit engine as a whole module or use only the core engine and implement your own custom UI instead of the provided one.

Some functionality like healthcheck is replaced with Spring Boot actuator (see “Do not reinvent the wheel” section).

Jmix provides more than 20 starters that can be used. Here are some starters and dependencies:

|Feature                                         | Starter                                 | Depend On |
|-------------------------------------|--------------------------------|---------------|
|Entity log                                     |Audit                                      |Data             |
|File storage                                  |Core                                       |                     |
|User settings                               |UI Persistence                       |Data             |
|Table presentations                    |UI Persistence                       |Data             |
|Entity log                                     |Audit UI                                 |Audit, UI      |
|Config properties stored in DB |Core                                       |                     |
|Restore deleted entities             |Data tools                             |Data, UI        |
|User sessions                               |Core                                      |                     |
|Dynamic attributes                     |Dynamic attributes              |Data, UI       |
|Entity Snapshots                         |Audit                                     |Data             |
|Related entities                           |Advanced Data Operations|Data, UI       |
|Bulk editor                                   |Advanced Data Operations|Data, UI       |



As you can see, “data” starter is used by almost all Jmix modules. And it is not a surprise, because one of the strongest sides of the CUBA Platform was its...

## Data access layer

We’re going to introduce a lot of changes here, keeping all the best parts of CUBA and introducing new features that will help you to be more productive.

With all the advantages, CUBA’s data model has one fundamental flaw: it is pretty rigid. For example, if you needed soft delete, you had to implement a proper interface (or inherit your entity from `BaseEntity`) and introduce columns with predefined names in the corresponding table. All primary keys had to be stored in the column with the `id` name if you used the `StandardEntity` class. 

This led to limitations during new data model development. And it also caused a lot of issues when developers tried to implement applications with CUBA using an existing data model. This was a case when CUBA was used as a modern framework to migrate from legacy or unsupported frameworks.

In Jmix, the Entity model becomes more flexible. You don’t need to extend the StandardEntity class or implement the Entity interface anymore. Just add the annotation `@JmixEntity` to a class to make it accessible to the framework. 

We decided to deprecate interfaces that specify an entity’s functionality. They are replaced with common annotations. For example, we use JPA’s `@Version` annotation and Spring Boot’s `@CreatedBy` instead of proprietary `Versioned` and `Creatable` interfaces. 

This allows us to make code more explicit - you can tell which features are supported by the entity by just looking at its code. 


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

“CUBA Views” are now “Fetch Plans”. The new name describes the purpose of these artifacts much better. 

Jmix’s data access layer now supports automatic lazy loading of references. So if you choose not to use fetch plans for filtering out local attributes, you will never get the notorious “UnfetchedAttributeException” anymore.

Another big thing is the database generation and update process. We decided to use Liquibase instead of the custom DB update engine. Spring Boot is responsible for running these scripts. This is another example of “not reinventing the wheel” - using a well-known engine with good documentation. 

Liquibase can generate DB-agnostic update scripts, so if you develop a product or an add-on with Jmix, you won’t need to generate database creation scripts for all possible RDBMSes. Liquibase will use the appropriate SQL dialect depending on a JDBC driver. At the same time, it allows DB-specific SQL customization, if you need it. 

And we keep the good old CUBA magic. Whenever you change an entity, Jmix Studio will generate a Liquibase script entry to reflect the changes.

What else can we think about when we talk about CUBA? Of course, it is the framework’s advanced... 

## Security

In Jmix security is a separate module. Now you can choose whether or not you want the CUBA security engine or something else. 

And we reworked our security engine, now it is tightly integrated with spring-security. In order to simplify things for developers and “do not reinvent the wheel” concept, we’ve replaced our custom engine with the “standard” framework that has a lot of documentation and is familiar to developers. The model has changed accordingly - in Jmix we use classes from Spring Security like UserDetails and SessionRegistry, so it might look a bit unfamiliar at the beginning. 

Roles have changed too - we have merged Roles and Access Groups to simplify security management. In addition to this, we’ve added an “Aggregation Role”. This is a role that is composed from other roles - there were a lot of requests from users about this feature. 

Spring security is not the easiest thing to set up but in Jmix we made this process as seamless as possible. You will be able to set access to entities, attributes, screens, as well as set up row-based security as it was in CUBA.

And as it was in CUBA, all you need to do to install the security into your application is to add a dependency to your project and Jmix will do its magic - you will have security set up as well as user management UI (if you want to).

Apart from security, there is one more thing that everyone liked about CUBA: the simplicity of the development of an application’s...

## User Interface

Backoffice UI (a.k.a. Generic UI) stays intact. Component-based UI was a big part of CUBA and we’re planning to support it in Jmix. Support includes screen generators, UI editors in the IDE, etc. We have added new components like a separate Pagination component or ResponsiveGridLayout. The only difference - now you can exclude Generic UI from the application completely thanks to the modular structure of the Jmix framework. 

Please note that Jmix applications are single-tiered; there is no more “core-web” separation. This approach is simpler and fits into the modern architectural approach. If you want a separation, you can achieve it by implementing two Jmix applications and create a REST API for communication. In this case, UI won’t depend on the data model and you will pass DTOs in order to display data on the front-end or process it on the back-end.

When we were planning the new version of our framework, we could not ignore the rise of JS UI frameworks. So we started developing ReactJS client generators (front-end module) in CUBA 7 and we continue this work in Jmix. JS frameworks usually have a pretty steep learning curve, so our aim is to make the ReactJS development experience with Jmix closer to Generic UI development. 

We have introduced TypeScript SDK and developed a set of custom ReactJS components that can be used for the UI development. The front-end module relies on the Generic REST API which is familiar for CUBA developers. The IDE supports basic UI generation with ReactJS. 

For now a developer can generate a familiar “browser” and “editor” UI screens using our components. Later we plan to add more components and simplify ReactJS UI development in the Studio. 

And now we have discussed almost all major changes in Jmix, but it would be unfair not to mention...
![text]({{strapiUrl}}/uploads/9b0dd8c1ff404e01aa0d9e90b1729b2e_716b21f236.png)

## Deploy

CUBA has two deploy formats: WAR and UberJar and two options: a single app deployment or a separate applications deployment (core+web+...). 
 
Jmix will use Spring Boot build plugins for application deploy. It means that you can run a Jmix app as an executable fat JAR or deployable WAR (it also can be executed as a standalone application). 

But the best thing here is containerization. Now you don’t need to create your own Docker file to create an application image, its generation is supported out-of-the-box. Also, you can create layered JARs to make Docker images more efficient. In addition to this, cloud native buildpacks are supported. 

So, Jmix applications will use the cutting edge technologies for deployment in modern cloud environments.

And with so many changes, how about...

## Migration from CUBA to Jmix

First thing: we are not going to abandon CUBA. Version 7 is going to be long-term-support and will be supported for five years. And after that, there will be commercial support available for the next five years. So, CUBA framework will live for at least next 10 years.

At the moment Jmix is at Preview stage, so we’re going to stabilize it for some time before announcing production-ready stable release - provisionally in Q2 2021. But if you plan to start using CUBA, have a look at Jmix first. It is stable enough to start PoC development. And remember that almost all Spring Boot ecosystem is at your service. 

For backward compatibility purposes, we have introduced a jmix-cuba module. This module contains most of the APIs implemented in CUBA. So, you won’t need to change your code much in order to migrate to the next framework version. The compatibility module will be added automatically to your application during migration.

Most CUBA add-ons will be gradually migrated to Jmix platform: reporting, maps, business processes. As we did with CUBA 7 before, we might deprecate some modules when moving to Jmix because there is a Spring Boot starter with the same functionality.

The add-ons format has changed, but functionality stays the same. You can extend entities and screens using the same technique that was used in CUBA. As for services override, you’ll need to use Spring Boot approach - just mark the add-on service with the Primary annotation and functionality will be replaced. 

As usual, when the major version is introduced (basically, Jmix is CUBA 8), some breaking changes may appear. And those changes, as well as workarounds, will be described in details in the documentation. 

And the big part of the migration is the new Studio. Jmix Studio plays a very important role in the framework ecosystem. So, you still be able to use all familiar designers (entity and UI), shortcuts and intentions. And Jmix Studio will help you with creating applications using the framework. 

## Conclusion

Jmix is the next big step in CUBA Platform evolution. Now you can enjoy almost all Spring Boot starters and use techniques applicable for the most popular Java framework in the world. At the same time you still have all the convenient and familiar APIs and functionality provided by Jmix - a CUBA descendant as well as great development experience with the new Studio.  
