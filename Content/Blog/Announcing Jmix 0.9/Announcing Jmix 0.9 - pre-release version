# Announcing Jmix 0.9 - pre-release version

Jmix 0.9 is the last pre-release branch that should be considered as “almost stable”. We also deliver the latest version of the companion development tool for the framework - Jmix Studio: 0.9.1-202.

In this release, we have frozen all major APIs: data model definition, data access layer, and security subsystem. They will probably remain the same in Jmix 1.0. Therefore, 0.9 can be considered as a good version for MVP development, and we expect that migration to 1.0 will be near trivial.

Let’s have a look at the most noticeable features in this version in various framework areas.

## Jmix Studio
The first thing that should be mentioned: you can create different types of projects with Jmix. In version 0.9, Studio provides three templates for your Jmix projects:
- *Application* - to create a new Jmix application.
- *Theme* - to create a CSS theme for your application. A theme can be installed as an add-on.
- *Widget* - this project type simplifies a custom widget creation.

To assist with project development, the Studio provides a [specialized tool window](https://docs.jmix.io/jmix/0.x/studio/tool-window.html). It can help with exploring Jmix-specific configuration files, navigate through the data model, configure data stores, and many other things.

## Core
The framework core is based on Spring Boot 2.4.2, and we are planning to update it to the latest version - 2.4.4 in Jmix 1.0, needless to say, the update process will not stop in the future versions of the framework.

As it has already been announced, Jmix uses Liquibase for the database update process. The framework generates database update scripts based on data model changes, similar to CUBA. But in contrast to the predecessor, the scripts are in XML format now, and the same script set can be applied to different database types.

The experienced CUBA developers will definitely notice the explicit definition of the `User` class in the application code, which may be unusual to them. This is a big change compared to the CUBA Platform - we decided to generate key user management functionality classes for every application, to make it simpler to extend or override if needed.

## Backoffice UI
At the moment, all UI components are converted to use the Jmix framework’s API and ready for the stable release. Just a reminder: in Jmix, Backoffice UI is a part of the main project, there is no separation into `core` and `web` modules anymore.

By default, the generated Jmix project contains Backoffice UI. It is added as a dependency, and you can remove it if you don’t need it. Familiar wizards for screen code generation stay in the Studio, so you will be able to create CRUD screens for your application just in a few clicks as before.

## React UI
The React UI client generator integration has been significantly improved. We continue developing libraries to simplify ReactJS development with Jmix. Now you can use two libraries: [Jmix React Core](https://docs.jmix.io/jmix-frontend-docs/0.x/jmix-react-core/index.html) - to work with Jmix entities and invoke the services and [Jmix React UI](https://docs.jmix.io/jmix-frontend-docs/0.x/jmix-react-ui/index.html) - a  set of UI components for the user interface development.

ReactJS client customization is simpler than before. Similar to Jmix Backoffice UI themes, you can [create themes](https://docs.jmix.io/jmix-frontend-docs/0.x/client-react/theme.html ) for the front-end client.

## Add-ons
There are six add-ons available on the Jmix marketplace now:
- REST API
- Maps
- Dynamic Attributes
- Entity Log
- Email
- Entity Inspector

We continue working hard on add-ons adoption, you can expect to see Jmix 0.9 compatible BPM and Charts add-ons in the marketplace soon.

## Conclusion
If you think about adopting Jmix, now it is a good time to start doing that. API is stable, so you won’t need to reimplement your MVP completely because of breaking changes.

Meanwhile, you can enjoy the updated core that allows you to use Spring Boot starters, better deployment options, including Docker image creation, and keep good old CUBA development speed.
