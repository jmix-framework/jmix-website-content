# Jmix 1.1 is released!
The next version of Jmix – 1.1 - is available for download. 
In this version, we introduce several major features:

1.	Migration from CUBA projects
2.	Kotlin support
3.	Full Java 17 support

Jmix Studio was updated too to support all these features.

## CUBA projects migration

You can migrate a CUBA project to Jmix, there are two ways to do it.

If you open CUBA project in Jmix Studio, the IDE will ask you if you want to migrate to the latest Jmix version, so you can start the process instantly. 
<br>
<img src='{{strapiUrl}}/uploads/1_a69e931d8e.png'>
 
But if you want to start the migration later, you can do it using Jmix Studio’s menu: `File -> New -> Jmix project from this CUBA project`.
<br>
<img src='{{strapiUrl}}/uploads/Screenshot_2021_10_30_at_10_36_55_2fd61a90e4.png'> 
 
Studio automatically changes the project structure to satisfy Jmix requirements. Most of the code remains untouched, Jmix uses CUBA Compatibility API to provide backward compatibility after migration.

Migration results and recommendations log are stored in the `MigrationResult.md ` file. It contains automatic migration results and recommendations on manual operations. 
Please note that the migration procedure keeps your CUBA project untouched, so it’s safe to run the procedure on any working copy of a project.

You can find more details in [Jmix Documentation](https://docs.jmix.io/jmix/cuba/index.html).

## Kotlin Support

With Jmix 1.1, we provide the application template for Kotlin developers as well as full Kotlin support in Jmix Studio.
<br>
<img src='{{strapiUrl}}/uploads/Screenshot_2021_10_30_at_10_39_35_8400b34f25.png'>
 
If you choose the Kotlin-based project template, Jmix Studio will generate entities, services and screen controllers using this language and its best practices. Please note: when developing JPA entities with Kotlin, you need to remember some rules in order to avoid issues in runtime: use open classes, implement `toString()` method in a special way, etc. 

There is [an article](https://www.jpa-buddy.com/blog/best-practices-and-common-pitfalls/) about best practices and common pitfalls in Kotlin. The good thing Is that visual editors in Jmix Studio take all these issues into account, so you don’t need to remember them.  

The same applies to all generators and code intentions in the IDE to help both new and experienced Kotlin developers make their code better.

## Java 17 support

Jmix 1.1 now allows you to use Java 17 in your project code. The framework runtime was fully tested against the 17th version of the JDK. It is the LTS (long-term support) version, that is [supported for two years](https://mreinhold.org/blog/forward-even-faster). It means the stable platform for running Jmix applications and proper support level from JDK vendors for this time. 
Apart from that, Java 17 provides a lot of improvements that allow applications run faster (thanks to compiler optimizations and better GCs) and developers to write better and safer code (sealed classes, records, switch expressions, etc.).

If you want to use Java 17 in your project, just ensure that you removed `sourceCompatibility` line from your `build.gradle` project and you installed Gradle 7.2 or later as your build tool, you can set it in `gradle-wrapper.properties`. 
<br>
<img src='{{strapiUrl}}/uploads/Screenshot_2021_10_30_at_10_42_27_d708bbcd65.png'>
 
Of course, you need to set up JDK 17 support in Jmix Studio settings.
<br>
<img src='{{strapiUrl}}/uploads/Screenshot_2021_10_30_at_10_46_41_8460b0854f.png'>
 
After that, you can enjoy the latest Java with Jmix. 

## Studio Improvements

Let’s go through the most noticeable Jmix Studio improvements.

*New “Inject” Dialog* now shows object available to injection to the following categories to provide better observability:

- Project Beans - Spring beans of the current project
- Project Properties - configuration property classes of the current project
- Infrastructure - frequently used framework beans
- Other Beans - all other Spring beans of the framework and add-ons
- Other Properties - all configuration property classes of the framework and add-ons

<img src='{{strapiUrl}}/uploads/Screenshot_2021_10_30_at_20_20_03_2584c1a829.png'>

In addition to this, you can always use quick filter: just start typing the desired component name to reduce a number of available objects.
*New Visual Components* include ResponsiveGridLayout, Single- and Multi- Select Lists.

ResponsiveGridLayout is a container where the components are laid out on a grid, based on Bootstrap’s 12 columns grid system. Let’s have a look at the following code:

```
<window xmlns="http://jmix.io/schema/ui/window">
    <layout>
        <responsiveGridLayout stylename="demo">
            <row>
                <col>
                    <label value="1 of 2"/>
                </col>
                <col>
                    <label value="2 of 2"/>
                </col>
            </row>
            <row>
                <col>
                    <label value="1 of 3"/>
                </col>
                <col>
                    <label value="2 of 3"/>
                </col>
                <col>
                    <label value="3 of 3"/>
                </col>
            </row>
        </responsiveGridLayout>
    </layout>
</window>
```
This code will be rendered into the following UI:
<br>
<img src='{{strapiUrl}}/uploads/Screenshot_2021_10_30_at_20_26_05_3cfdf0ca74.png'>
 
As you can see, now you have more options for planning your layout.

*Select List* displays a pre-defined list of options in a vertically scrollable list. SingleSelectList allows users to select only a single item from the list. MultiSelectList allows multi selection, obviously.
<br>
<img src='{{strapiUrl}}/uploads/Dizajn_bez_nazvaniya_d57348fd8f.jpg'>
               
*BPM Designer* now allows developer to create BPM diagrams right in the Studio, if they have BPM add-on installed. It simplifies BPM process deployment, you don’t need to unload it from the development environment and import into production. Now BPM process descriptors and related code (services, user providers, etc.) are stored in the codebase and there is no chance to deploy a new process version to an old application.
<br>
<img src='{{strapiUrl}}/uploads/Screenshot_2021_10_30_at_20_07_20_88aa300fe9.png'>
 
Please note that BPM designer is still available in Jmix application, so you can create ad-hoc business processes like you did in Jmix 1.0.

## Conclusion

We continue improving both Jmix framework and Studio. With new functionality you can start migrating your CUBA applications to the modern application stack: Jmix (with Spring Boot at its core) and JDK 17. And if you want to evaluate Kotlin for backend development, now is the time. You can find more information about Jmix 1.1 in the [release notes]( https://docs.jmix.io/jmix/whats-new/index.html).
