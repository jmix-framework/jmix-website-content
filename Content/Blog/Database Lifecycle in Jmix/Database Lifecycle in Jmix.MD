## Database Lifecycle in Jmix

### Introduction

Jmix is a framework for data-centric application creation. Hence, data model and data access layer play one of the major roles in the framework. We use relational databases and JPA for data access in Jmix.

JPA abstracts us from DB-specific queries and we work with classes and objects in the application. But you need to be sure that your database schema and object model are in synchronized state. Otherwise, the application might not even start or worse - throw unexpected exceptions in runtime. 

So what do we do in Jmix to avoid such issues and simplify a developer’s life?

### Reasoning about the data model

When we start a project (with any technology) that uses an ORM framework (JPA, iBatis, or any other), we should decide what goes first: a database schema definition or an object model? In Jmix, we recommend starting with the object model definition. The rationale behind this recommendation is simple: we should define a data model where it is used. Since all business logic is processed in the application, defining the object model on the app side looks reasonable. 

An application is not a static thing, business requirements change over time, so the application’s data model changes. It means that we need to change the underlying data storage. 

The times when developers wrote and updated SQL for their applications are long gone. Nowadays we usually use dedicated database versioning tools. Liquibase and Flyway are the most common ones. In Jmix, we use Liquibase for the DB versioning support.

### What is Liquibase?

The official definition of Liquibase is: “Liquibase is an open-source database schema change management solution which enables you to manage revisions of your database changes”.

The key concept is the “changeset” - a single database update like table creation, column removal or constraint update.

Changesets are stored in DB-agnostic scripts in XML, YAML or JSON format - changelogs. You can also write DB-specific changelogs like creating a table with a JSONB column for PostgreSQL and BLOB for other databases.

Usually, in the application codebase there is one “master” changelog that contains directives to include other changelogs. And each time a new changelog is created, it is included into master. 

Liquibase provides a robust framework for running database update scripts. This tool even can create changelogs based on the existing database or comparing two database schemas. We can even generate changelogs for the entities model, if Hibernate is used, but a separate maven plugin is needed. 

### Jmix Scripts Generation

In Jmix, we generate Liquibase changelogs by comparing the JPA data model with the database schema. The development cycle basically consists of the following steps:

1.	Implement object data model
2.	Check if all existing changelogs are applied to the DB
3.	Compare object data model against the DB schema
4.	Generate a new Liquibase changelog that updates the DB schema according to object model changes

Looks easy, right? The framework does all the heavy lifting for us. But you need to be careful, because not all changes are harmless. Adding a field to an entity (hence a column to a table) is simple. But removing a field may cause data loss. 

Jmix Studio groups database updates and shows unsafe changesets in red color, and a developer can remove them from the changelog if needed.

 

After generation, the changelog becomes a part of the source code. In Jmix, we store changes, grouping them by date. By default, changelogs are stored in the following folder structure:
 
Every new changelog will be placed in the corresponding folder and included in the main `changelog.xml` file. 

Every time a Jmix application starts, it runs the main changelog using the Spring Boot Liquibase integration bean.

### Database Migration Process

During the development phase we can apply Liquibase changelogs to the dev database using Jmix Studio. Just right-click on the data source in the navigator and select “Update Database”

 

In case of the prod deployment, we sometimes don’t have access to the prod database. In this case, DevOps or DBA has two options:

1.	Apply changelogs automatically on the application startup
2.	Apply manually and then redeploy and restart the application

As it was mentioned above, in a Jmix application, the first option is enabled. If we don’t want to allow our application to update the production database automatically, we need to set the `jmix.liquibase.enabled` property value to `false` in the `application.properties` file.

Jmix keeps changelogs in the same .JAR with the application code. Though Liquibase supports running changelogs packaged into .WAR or .EAR files, it does not support Spring Boot .JAR layout.  If you want to run migration separately, you need to extract and copy changelogs to a separate location manually and run them using Liquibase CLI. 

### Conclusion

Database migration is a challenging task. Fortunately, there are tools that simplify it for a developer. Liquibase provides changelogs execution, validation, checks integrity, etc. 

With Jmix, you can generate changelogs according to JPA model changes, review them and update if needed. Combining Jmix with Liquibase covers the full database schema development lifecycle starting from JPA entities creation to schema update. 
