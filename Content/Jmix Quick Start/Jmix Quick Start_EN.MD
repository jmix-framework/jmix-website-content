# Jmix Quick Start
<div id="chapter0" class="section"></div>

## Preface
In this quick start, we will scratch the surface of Jmix and develop a very simple but fully functional project management application. It will show the main things for creating any web application:

- How to design a data model.
- How to manipulate data.
- How to create business logic.
- How to add security.
- How to create a user interface.

This tutorial will be just enough for you to start your own Jmix application. In this tutorial, we will use <a href="https://www.jmix.io/tools/">Jmix Studio</a>, so please install it before you begin and accept a trial subscription to access the visual designers.

Sample code repo: [https://github.com/Haulmont/jmix-quickstart](https://github.com/Haulmont/jmix-quickstart).

<div id="chapter1" class="section"></div>

## Jmix project creation

<div class="timestamp-wrapper">
   <a id="stamp1" class="timestamp-wrapper-buttons"><div class="timestamp">
    <img src="/images/learn/play.svg" class="delta">
    <div class="video-time">1:05</div>
  </div></a>
</div>

We will create an empty Jmix project using the corresponding IntelliJ IDEA menu. We will use JDK 11.

![create-project.png]({{strapiUrl}}/uploads/create_project_2560630927.png)

With Jmix, you can generate project code based on templates. To create an application, let’s use the ```single-module-application``` template.

![template.png]({{strapiUrl}}/uploads/template_e4f902df3c.png)

Assign a name - ```jmix-pm``` for your application.

![project-name.png]({{strapiUrl}}/uploads/project_name_cb7b01702f.png)

After the project is created, you can move further with the help of the Jmix Tool Window that allows you to get access to different files and settings, as well as add some project-specific objects.

![studio.png]({{strapiUrl}}/uploads/studio_9d2d26beec.png)
  
<br>
<div id="chapter2"  class="section"></div>

## Data model and database creation

<div class="timestamp-wrapper">
   <a id="stamp2" class="timestamp-wrapper-buttons"><div class="timestamp">
    <img src="/images/learn/play.svg" class="delta">
    <div class="video-time">2:45</div>
  </div></a>
</div>

The first task is creating entities. The business domain model has only two classes: ```Project``` and ```Task```. The relation is one-to-many: one project can have many tasks.
![data-model.png]({{strapiUrl}}/uploads/data_model_b0983e6fdf.png)
For a starter, let’s create the ```Project``` entity. To do this, we can use a link on the project’s welcome page.

![new-entity-welcome.png]({{strapiUrl}}/uploads/new_entity_welcome_38503d524f.png)

Another way is to right-click the **Data Model** node in the **Jmix Tool Window** and select **New → JPA Entity**.

![new-entity.png]({{strapiUrl}}/uploads/new_entity_71a06abc39.png)

Enter entity’s class - ```Project```. For this sample application, we do not need to change other entity parameters.

![project-entity.png]({{strapiUrl}}/uploads/project_entity_5c15c504b9.png)

In the entity designer, create attributes according to the specification:

<div class="scrollable-table ">
<table>
<tbody>
<tr>
<td>Name</td>
<td>Type</td>
<td>Mandatory</td>
</tr>
<tr>
<td>name</td>
<td>String (255)</td>
<td>Yes</td>
</tr>
<tr>
<td>startDate</td>
<td>LocalDate</td>
<td></td>
</tr>
<tr>
<td>endDate</td>
<td>LocalDate</td>
<td></td>
</tr>
<tr>
<td>manager</td>
<td>Association to the "User" entity, many-to-one cardinality</td>
<td>Yes</td>
</tr>
</tbody>
</table>
</div>

In Jmix, we use standard JPA entities, so you can create them using either a code editor or a visual designer. Just click the *+* icon and add attributes to the entity. Jmix Studio will generate class members for you.

![new-attribute.png]({{strapiUrl}}/uploads/new_attribute_faac04df32.png)

Look at how to add  a mandatory reference to a user. The relation is many-to-one, so we’ll define an association field called ```manager``` that references the ```User``` class. Finally, the field definition should look like this:

![manager-attribute.png]({{strapiUrl}}/uploads/manager_attribute_773cf285d2.png)

In Jmix, you can specify a format for a proper entity display as a string in the UI using the **Instance name**  field. For the ```Project``` entity, we will select the ```name``` attribute.

![instance-name.png]({{strapiUrl}}/uploads/instance_name_136368a2b2.png)

If we look at the **Text** tab at the bottom of the entity designer, we can see just a JPA-annotated Java class. The generated code can be updated if needed, and the designer will be updated accordingly when you switch to the **Designer** tab.

Let’s move further and create the ```Task``` entity and link it to our ```Project``` class. Fields specification table follows.

<table>
<tbody>
<tr>
<td>Name</td>
<td>Type</td>
<td>Mandatory</td>
</tr>
<tr>
<td>name</td>
<td>String (255)</td>
<td>Yes</td>
</tr>
<tr>
<td>assignee</td>
<td>Association to the "User" entity, many-to-one cardinality</td>
<td>Yes</td>
</tr>
<tr>
<td>startDate</td>
<td>LocalDateTime</td>
<td></td>
</tr>
<tr>
<td>estimatedEfforts</td>
<td>Integer</td>
<td></td>
</tr>
</tbody>
</table>

A task cannot exist without a project. This relation is called ```Composition``` in Jmix. Let’s create a link between a task and a project. Open the ```Project``` entity and create a composition attribute - ```tasks``` - the list of tasks within ```Project```.

![tasks-attribute.png]({{strapiUrl}}/uploads/tasks_attribute_4ad87a6cb5.png)

To make a link to ```Project``` from the ```Task``` entity, we need to create an inverse attribute in the task.

![mapped-attribute.png]({{strapiUrl}}/uploads/mapped_attribute_7a3311b79c.png)

The data model is ready. Let’s generate database update scripts.

Expand the **Data Stores** node in the **Jmix Tool Window**, right-click **Main Data Store** and select **Generate Liquibase Changelog**.

![generate-database-scripts.png]({{strapiUrl}}/uploads/generate_database_scripts_58c99e0cb2.png)

Jmix Studio generates update scripts by comparing the existing database schema with the application data model.

For our project, we will use an in-memory database - HSQLDB.

![hsqldb.png]({{strapiUrl}}/uploads/hsqldb_bd3d342711.png)

Studio may ask us to apply existing scripts to align the application and the database state.

![apply-existing-scripts.png]({{strapiUrl}}/uploads/apply_existing_scripts_7014b817af.png)

That’s it. The database has been created.

<div id="chapter3" class="section"></div>

## Generating CRUD admin screens
<div class="timestamp-wrapper">
   <a id="stamp3" class="timestamp-wrapper-buttons"><div class="timestamp">
    <img src="/images/learn/play.svg" class="delta">
    <div class="video-time">5:27</div>
  </div></a>
</div>

Jmix Studio contains a UI screen generation wizard that helps us to create basic but useful UI screens:

- Browser - to show the list of entities in a grid.
- Editor - to edit one entity instance using a form-like user interface.

First, we will create screens to work with projects. Start a wizard by clicking the **Create screen** menu item in the **Screens** menu on the top of the entity designer.

![create-screen.png]({{strapiUrl}}/uploads/create_screen_aabb9f80f4.png)

Also, you can use Jmix tool window to start screen generation wizard. Open the context menu by clicking the + icon in the toolbar and select **Screen**.

![create-screen-menu.png]({{strapiUrl}}/uploads/create_screen_menu_297631d0a9.png)

Select **Entity browser and editor screens** in the wizard.

![templates.png]({{strapiUrl}}/uploads/templates_0ec0a12a10.png)

Then click **Next** and stop at the **Entity browser fetch plan** step.

In Jmix, we can define several fetch plans for every entity. They specify which fields will be fetched from the database. You can define fetch plans in a separate file to use them in different modules of your application or create an inline fetch plan while creating a screen.

Let’s create an inline fetch plan. In addition to the selected properties, mark the ```manager``` reference.

![project-browser.png]({{strapiUrl}}/uploads/project_browser_5a5eaf9cce.png)

At the next step, let’s add both ```manager``` and ```tasks``` fields.

![project-editor.png]({{strapiUrl}}/uploads/project_editor_a82d50f560.png)

Click **Next** at the next step and finish screens creation.

As you can see, each screen consists of two parts: a controller, written in Java, which is responsible for internal screen logic and events handling, and an XML layout that defines the screen appearance. In our case, the browser consists of the ```ProjectBrowse.java``` and ```project-browse.xml``` files and editor - ```ProjectEdit.java``` and ```project-edit.xml``` accordingly.

You can find XML descriptors in the **Data Model** sections in the **Jmix Tool Window**.

![xml-files.png]({{strapiUrl}}/uploads/xml_files_25c2db561d.png)

To open the controller, use the context menu.

![open-controller.png]({{strapiUrl}}/uploads/open_controller_d70576a34c.png)

Please pay attention to the data section in the XML screen descriptors - it defines how the data is fetched from the database.

```
<data readOnly="true">
    <collection id="projectsDc"
                class="com.company.jmixpm.entity.Project">
        <fetchPlan extends="_base">
            <property name="manager" fetchPlan="_base"/>
        </fetchPlan>
        <loader id="projectsDl">
            <query>
                <![CDATA[select e from Project e]]>
            </query>
        </loader>
    </collection>
</data>
```
After screens are created, you can preview a screen by using buttons in the top right corner of the screen layout editor. The preview shows that all selected attributes are added to the screens.

![preview.png]({{strapiUrl}}/uploads/preview_ff61b86cbf.png)

UI components can be bound to data in a bidirectional way. All changes in the bound fields are reflected in the selected data and vice versa.

![bound-data.png]({{strapiUrl}}/uploads/bound_data_a53602e4db.png)

Now let’s generate CRUD screens for the ```Task``` entity. With the ```Task```, we will also fetch ```Assignee``` and ```Project``` entities.

![task-screens.png]({{strapiUrl}}/uploads/task_screens_93fbc29528.png)

At the next step, the necessary fields are already selected.

![task-editor.png]({{strapiUrl}}/uploads/task_editor_8ba252c246.png)

You can easily navigate between a screen controller, descriptor, and linked entities with Jmix Studio using buttons on the top of the window:

![navigate-controller.png]({{strapiUrl}}/uploads/navigate_controller_e18c6459c9.png)
 
![navigate-descriptor.png]({{strapiUrl}}/uploads/navigate_descriptor_b677194646.png)
 
![navigate-data-model.png]({{strapiUrl}}/uploads/navigate_data_model_6d99880909.png)

<div id="chapter4" class="section"></div>

## Running application in the development mode

<div class="timestamp-wrapper">
   <a id="stamp4" class="timestamp-wrapper-buttons"><div class="timestamp">
    <img src="/images/learn/play.svg" class="delta">
    <div class="video-time">07:25</div>
  </div></a>
</div>

To run the application, you can use the **Run Configuration** tool on the top of the IDE window.To run the application, you can use the Run Configuration tool on the top of the IDE window.

![run-configuration-menu.png]({{strapiUrl}}/uploads/run_configuration_menu_01f78288bb.png)

After some time, you can access the application using the browser. By default, the URL will be http://localhost:8080/ .

You can see the application log file at the bottom of the IDE in the **Run** window.

![run-console.png]({{strapiUrl}}/uploads/run_console_3a43289d77.png)

Open the URL in your browser and log into the application using ```admin``` as a username. The password is ```admin``` by default.

![login.png]({{strapiUrl}}/uploads/login_06139cb32c.png)

You can find screens for entities manipulation under the **Application** menu.

![application-menu.png]({{strapiUrl}}/uploads/application_menu_f7c4aaf89b.png)

Then let’s add some data to the database. Create a new project and assign the ```admin``` user as a manager.

![new-project-one.png]({{strapiUrl}}/uploads/new_project_one_3963b3ac58.png)

We can add a task when creating a project.

![new-task-one.png]({{strapiUrl}}/uploads/new_task_one_6a55c9589e.png)

Let’s create a new user - dev1 - as an assignee for this task.

![create-dev1.png]({{strapiUrl}}/uploads/create_dev1_85398f3aa7.png)

Save the newly created project. The task will be saved automatically.

<div id="chapter5" class="section"></div>

## Adding security

<div class="timestamp-wrapper">
   <a id="stamp5" class="timestamp-wrapper-buttons"><div class="timestamp">
    <img src="/images/learn/play.svg" class="delta">
    <div class="video-time">08:25</div>
  </div></a>
</div>

In Jmix, you can create roles and give them permissions to access the application data such as particular entities, attributes, or functionality like screens and menu items, in the admin UI.

Open the **Resource roles** screen and create the "Developer" role. Select **Entity policy** from the list and allow developers to view and edit tasks.

![entity-policy-menu.png]({{strapiUrl}}/uploads/entity_policy_menu_260322af8a.png)

![entity-policy.png]({{strapiUrl}}/uploads/entity_policy_fc74f06cad.png)

Then allow developers to edit task estimated time and start date only.

![attributes-policy.png]({{strapiUrl}}/uploads/attributes_policy_0c8ed78391.png)

Finally, add permissions to view browser and editor screens. Select **Grant access to the menu item** to add **Tasks** to the main menu.

![browse-policy.png]({{strapiUrl}}/uploads/browse_policy_067f4c25b8.png)

![edit-policy.png]({{strapiUrl}}/uploads/edit_policy_9c1e735c04.png)

Then, switch to the **Child roles** tab and add another role to the "Developer" - the "UI: minimal access" role that allows users to log in to the application.

![minimal-role.png]({{strapiUrl}}/uploads/minimal_role_0da38e7a48.png)

Let’s assign the role "Developer" to the "dev1" user. Select **Role assignments** for the necessary user in the **Users** screen.

![role-assingments.png]({{strapiUrl}}/uploads/role_assingments_1124380ca4.png)

Now let’s log in as developer one. We can see that this user has access to the specified screens and attributes only.

![developer-login.png]({{strapiUrl}}/uploads/developer_login_446615a954.png)


<div id="chapter6" class="section"></div>

## Adding business logic

<div class="timestamp-wrapper">
   <a id="stamp6" class="timestamp-wrapper-buttons"><div class="timestamp">
    <img src="/images/learn/play.svg" class="delta">
    <div class="video-time">09:38</div>
  </div></a>
</div>

Now we will use Jmix Studio to create a service that implements business logic and use this service in a screen. It will be a Spring service that will return the least busy user. In the admin UI, we will use this service to assign a task to this user by default.

Use a toolbar in the Jmix tool window to open commonly used actions. Select **Spring Bean** and enter the class name - ```TaskService```.

![create-service.png]({{strapiUrl}}/uploads/create_service_6695122e0b.png)

Studio will generate an empty Spring bean. Replace the ```@Component``` annotation with ```@Service```.

![empty-class.png]({{strapiUrl}}/uploads/empty_class_8e00549665.png)

Let’s create the ```findLeastBusyUser()``` method. In the service, we will use the Jmix service - ```DataManager```. It allows us to access data by using a JPQL query.

Inject ```DataManager``` into the service by using the Inject button on top of the window.

![inject-button.png]({{strapiUrl}}/uploads/inject_button_aa94f16b6a.png)

Select ```DataManager``` in the popup window.

![select-data-manager.png]({{strapiUrl}}/uploads/select_data_manager_ebaa015202.png)

Add the method’s implementation represented below:

```
@Service
public class TaskService {

    @Autowired
    private DataManager dataManager;

    public User findLeastBusyUser() {
        User leastBusyUser = dataManager.loadValues("select u, count(t.id) " + // (1)
                "from User u left outer join Task_ t " +
                "on u = t.assignee " +
                "group by u order by count(t.id)")
                .properties("user", "tasks")
                .list().stream().map(e -> e.<User>getValue("user"))
                .findFirst() // (2)
                .orElseThrow(IllegalStateException::new);
        return leastBusyUser; // (3)
    }
}
```
1. A JPQL query that selects users and counts tasks assigned to these users.
2. Takes the first user in the selected set.
3. Returns the user.

The service is ready, let’s use it in the task editor screen.

Click the **Generate Handler** button on the top of the window with the screen controller and select the ```InitEntity``` event.

![generate-handler.png]({{strapiUrl}}/uploads/generate_handler_5e2fcad2e6.png)

![init-entity-event.png]({{strapiUrl}}/uploads/init_entity_event_c48ed9d898.png)

Here is the implementation of the method:

```
public class TaskEdit extends StandardEditor<Task> {
    @Autowired
    private TaskService taskService; // (1)

    @Subscribe
    public void onInitEntity(InitEntityEvent<Task> event) {
        event.getEntity().setAssignee(taskService.findLeastBusyUser()); // (2)
    }
}
```

1. We inject the ```TaskService``` into the screen.
2. Assigns the execution result to the ```assignee``` field of the created task.

That’s it. Let’s restart the application and see the service execution in action.

First, let’s add one more developer - ```dev2```.

![create-dev2.png]({{strapiUrl}}/uploads/create_dev2_b94c1189ed.png)

We have one task assigned to Developer One, so an Admin or Developer Two will be the next least busy developer.

![create-task-two.png]({{strapiUrl}}/uploads/create_task_two_fdaadbf4b4.png)

After adding four tasks, the next least busy developer will be either Admin or Developer One, they both have one task each.

![tasks-list.png]({{strapiUrl}}/uploads/tasks_list_f070d7b7e0.png)

<div id="chapter7" class="section"></div>

## Deploy

<div class="timestamp-wrapper">
   <a id="stamp7" class="timestamp-wrapper-buttons"><div class="timestamp">
    <img src="/images/learn/play.svg" class="delta">
    <div class="video-time">11:45</div>
  </div></a>
</div>

Let’s see how to deploy a Jmix application with an executable JAR file.

First, run the ```boot:jar``` command in Jmix Studio.

![boot-jar.png]({{strapiUrl}}/uploads/boot_jar_68e7162b03.png)

The file is ready. Navigate to the folder with the file.

![navigate-terminal.png]({{strapiUrl}}/uploads/navigate_terminal_59b31fa661.png)

Then, execute the command ```java -jar <file_name>```.

![java-jar.png]({{strapiUrl}}/uploads/java_jar_28326f2f57.png)

Now you can open the browser and see the application running.

<div id="chapter8" class="section"></div>

## Conclusion

<div class="timestamp-wrapper">
   <a id="stamp8" class="timestamp-wrapper-buttons"><div class="timestamp">
    <img src="/images/learn/play.svg" class="delta">
    <div class="video-time">12:26</div>
  </div></a>
</div>

With Jmix, you can implement a ready-to-deploy Spring Boot application in minutes, thanks to the powerful development tools and code generators. 