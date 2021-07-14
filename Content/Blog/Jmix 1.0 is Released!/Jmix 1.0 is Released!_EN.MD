# Jmix 1.0 is Released!

 We have released a stable version - 1.0 of the Jmix framework. We’ve spent most efforts on bugfixes and code stabilization to deliver the production-ready framework. But that is not all. 

 Finally, we have released a stable version - 1.0 of the Jmix framework. After [version 0.9 release](https://www.jmix.io/blog/announcing-jmix-0.9-pre-release-version/) we’ve spent most efforts on bugfixes and code stabilization to deliver the production-ready framework. But that is not all. Jmix is evolving and we’ve added some new features that should simplify application development even more.

## Jmix Studio

In addition to the existing Jmix project templates, we have added one more: `Single Module Add-On`. The generated project structure will contain all settings specific for Jmix add-ons and a sample code: an entity, its UI screen, and integration tests. This should help you to ramp up your add-on development project faster.

If you are a BPM add-on user, you will be able to create BPM diagrams in the design time now (beta feature). All business processes should be deployed on the application start-up. 

![bpmn_idea.png]({{strapiUrl}}/uploads/bpmn_idea_c107e47b25.png)


## Core

We haven’t changed Jmix’s core much since release 0.9, but there is a feature that should be mentioned. 

A new experimental feature - Spring Data repositories support. Now in Jmix, you can define data repositories using the well-known approach from Spring: repository interfaces. The concept was described in the [blog article](https://www.cuba-platform.com/blog/spring-query-interfaces-in-cuba/), now this feature is introduced in Jmix. We’re creating a developer’s guide for this feature now, but you can try it in this release.

## Add-Ons

Now you can find more add-ons in the Jmix marketplace. The most significant are:

* Audit
* BPM
* IMAP
* Charts & Pivot Table
* AWS File Storage
* UI Localization: German, Chinese, Russian
* Multitenancy
* Reports
* Search

All of them are ready for 1.0 and can be installed from the Jmix Studio. 

The last one - Search - should be mentioned separately. In Jmix this add-on uses the Elasticsearch engine. Also, we have introduced a new configuration approach for the full-text-search feature, you can find more information about it in the [documentation](https://docs.jmix.io/jmix/1.0/search/index.html).

## Conclusion

Jmix is ready for production. If you have started development with Jmix 0.9, you can find a migration guide in [the documentation](https://docs.jmix.io/jmix/1.0/whats-new/#upgrade-from-0.9). 

In the next step, we are planning to have support for the migration of existing CUBA apps to Jmix with the help of Jmix Studio. This functionality is being developed to provide as slick a process as possible.

Anyway, with Jmix 1.0 you can start implementing your applications using all-new add-ons and visual designers that we provide you in this version. 

