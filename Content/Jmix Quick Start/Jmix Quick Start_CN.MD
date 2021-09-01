# Jmix 快速入门
<div id="chapter0" class="section"></div>

## 前言
在这个快速入门教程中，我们将使用最基础的 Jmix 功能，并开发一个非常简单但功能齐全的项目管理应用程序。其中会展示创建任何 web 应用程序都会涉及的主要内容：

- 如何设计数据模型。
- 如何操作数据。
- 如何创建业务逻辑。
- 如何增加安全机制。
- 如何创建用户界面。

完成本教程之后，您就可以开始开发自己的 Jmix 应用程序。在本教程中，我们将使用 <a href="https://www.jmix.cn/tools/">Jmix Studio</a>，所以在开始学习本教程之前，请先安装，并启用试用版许可，以便访问可视化设计器。

示例代码仓库：[https://github.com/Haulmont/jmix-quickstart](https://github.com/Haulmont/jmix-quickstart)

<div id="chapter1" class="section"></div>

## 创建 Jmix 项目

<div class="timestamp-wrapper">
   <a id="stamp1" class="timestamp-wrapper-buttons"><div class="timestamp">
    <img src="/images/learn/play.svg" class="delta">
    <div class="video-time">1:05</div>
  </div></a>
</div>

我们将用 IntelliJ IDEA 的菜单创建一个空的 Jmix 项目。项目使用 JDK 11。

![create-project.png]({{strapiUrl}}/uploads/create_project_2560630927.png)

使用 Jmix，可以基于模板生成项目代码。我们用 ```single-module-application``` 模板创建应用程序。

![template.png]({{strapiUrl}}/uploads/template_e4f902df3c.png)

设定项目名称：```jmix-pm``` 。

![project-name.png]({{strapiUrl}}/uploads/project_name_cb7b01702f.png)

在项目创建完成之后，可以进一步尝试使用 Jmix 工具窗口（Jmix Tool Window），通过 Jmix 工具窗口可以访问项目中不同的文件和配置，还能添加一些项目特定的对象。

![studio.png]({{strapiUrl}}/uploads/studio_9d2d26beec.png)
  
<br>
<div id="chapter2"  class="section"></div>

## 创建数据模型和数据库

<div class="timestamp-wrapper">
   <a id="stamp2" class="timestamp-wrapper-buttons"><div class="timestamp">
    <img src="/images/learn/play.svg" class="delta">
    <div class="video-time">2:45</div>
  </div></a>
</div>

首要任务是创建实体。业务领域模型只包含两个类：```Project```（项目）和 ```Task```（任务）。它们的关联关系为一对多：一个项目有多个任务。

![data-model.png]({{strapiUrl}}/uploads/data_model_b0983e6fdf.png)

首先，我们创建 ```Project``` 实体。我们可以用项目欢迎页上的一个链接来完成。

![new-entity-welcome.png]({{strapiUrl}}/uploads/new_entity_welcome_38503d524f.png)

另一个方法就是右键点击 **Jmix Tool Window** 中的 **Data Model** 节点，然后选择 **New → JPA Entity**。

![new-entity.png]({{strapiUrl}}/uploads/new_entity_71a06abc39.png)

输入实体的类名 - ```Project```。对于该示例项目，我们不需要修改其他的实体参数。

![project-entity.png]({{strapiUrl}}/uploads/project_entity_5c15c504b9.png)

在实体设计器中，根据下面的字段规范创建属性：

<div class="scrollable-table ">
<table>
<tbody>
<tr>
<td>属性名</td>
<td>类型</td>
<td>是否必须</td>
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
<td>关联至 “User” 实体，多对一关系</td>
<td>Yes</td>
</tr>
</tbody>
</table>
</div>

在 Jmix 中，我们使用标准的 JPA 实体，因此可以通过代码编辑器或者可视化设计器进行创建。只要点击 **+** 图标，然后为实体创建属性，Jmix Studio 会为您生成类成员。

![new-attribute.png]({{strapiUrl}}/uploads/new_attribute_faac04df32.png)

我们看看如何添加一个对 User 实体的必须引用。引用关系为多对一，所以我们要定义关联字段 ```manager```，关联至 ```User``` 类。最后，该字段定义是这样的：

![manager-attribute.png]({{strapiUrl}}/uploads/manager_attribute_773cf285d2.png)

在 Jmix 中，通过使用 **Instance name** 字段，可以为实体设置一个合适的字符串形式的展示格式。对于 ```Project``` 实体，我们选取 ```name``` 作为展示属性。

![instance-name.png]({{strapiUrl}}/uploads/instance_name_136368a2b2.png)

如果我们切换至实体设计器底部的 **Text** 标签页，我们能看到这只是一个普通的带有 JPA 注解的 Java 类。如果需要，可以手动更新生成的代码，当切换至 **Designer** 标签页时，设计器会同步更新。

下面我们开始创建 ```Task``` 实体，并将其关联至我们已经创建好的 ```Project``` 类。字段规范表如下。

<table>
<tbody>
<tr>
<td>属性名</td>
<td>类型</td>
<td>是否必须</td>
</tr>
<tr>
<td>name</td>
<td>String (255)</td>
<td>Yes</td>
</tr>
<tr>
<td>assignee</td>
<td>关联至 “User” 实体，多对一关系</td>
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

任务不能脱离于项目而存在。这种关系在 Jmix 中被称为 ```Composition``` - 组合。下面我们开始创建任务和项目之间的链接。打开 ```Project``` 实体，创建一个组合属性 - ```tasks``` - 一个 ```Project``` 内的任务列表。

![tasks-attribute.png]({{strapiUrl}}/uploads/tasks_attribute_4ad87a6cb5.png)

为了创建 ```Task``` 实体中的 ```Project``` 链接，我们需要在 ```Task``` 中创建一个反向属性。

![mapped-attribute.png]({{strapiUrl}}/uploads/mapped_attribute_7a3311b79c.png)

现在数据模型完成了，下一步我们生成数据库的更新脚本。

在 **Jmix Tool Window** 中展开 **Data Stores** 节点，右键点击 **Main Data Store** 然后选择 **Generate Liquibase Changelog**。

![generate-database-scripts.png]({{strapiUrl}}/uploads/generate_database_scripts_58c99e0cb2.png)

Jmix Studio 通过比较已有的数据库结构和应用程序的数据模型来生成更新脚本。

我们的项目将使用内存数据库 - HSQLDB。

![hsqldb.png]({{strapiUrl}}/uploads/hsqldb_bd3d342711.png)

Studio 可能会要求我们运行已有的脚本同步应用程序和数据库的状态。

![apply-existing-scripts.png]({{strapiUrl}}/uploads/apply_existing_scripts_7014b817af.png)

完成了，数据库已经创建。

<div id="chapter3" class="section"></div>

## 生成 CRUD 管理界面
<div class="timestamp-wrapper">
   <a id="stamp3" class="timestamp-wrapper-buttons"><div class="timestamp">
    <img src="/images/learn/play.svg" class="delta">
    <div class="video-time">5:27</div>
  </div></a>
</div>

Jmix Studio 包含一个 UI 界面生成向导，可以用来创建虽然很基础但非常有用的 UI 界面：

- 浏览界面 - 用表格的方式展示实体列表。
- 编辑界面 - 用类似表单的界面编辑一个实体示例。

首先，我们将创建处理项目的界面。在实体编辑器的顶部，点击 **Screens** 菜单下的 **Create screen** 启动一个界面生成向导。

![create-screen.png]({{strapiUrl}}/uploads/create_screen_aabb9f80f4.png)

另外，也可以使用 Jmix 工具窗口启动界面生成向导。在工具栏中点击 **+** 按钮然后选择 **Screen**。

![create-screen-menu.png]({{strapiUrl}}/uploads/create_screen_menu_297631d0a9.png)

选择 **Entity browser and editor screens**。

![templates.png]({{strapiUrl}}/uploads/templates_0ec0a12a10.png)

点击 **Next**，然后在 **Entity browser fetch plan** 这一步停一下。

在 Jmix 中，我们可以为每个实体定义多个 fetch plan。Fetch plan 定义从数据库读取哪些字段。可以把 fetch plan 定义在一个单独的文件中以供不同的模块使用，也可以在创建界面的时候定义内联的 fetch plan。

我们来创建一个内联的 fetch plan。除了已经选择的属性外，将 ```manager``` 也勾选上。

![project-browser.png]({{strapiUrl}}/uploads/project_browser_5a5eaf9cce.png)

下一步，我们添加 ```manager``` 和 ```tasks``` 字段。

![project-editor.png]({{strapiUrl}}/uploads/project_editor_a82d50f560.png)

下一步，点击 **Next** 完成界面的创建过程。

我们可以看到，每个界面由两部分组成：一个用 Java 编写的界面控制器，负责实现界面的内部逻辑和事件处理，以及一个 XML 布局文件，用来定义界面的外观。我们这个例子中，浏览界面由 ```ProjectBrowse.java``` 和 ```project-browse.xml``` 组成，而编辑界面由 ```ProjectEdit.java``` 和 ```project-edit.xml``` 组成。

XML 界面描述可以通过 **Jmix Tool Window** 的 **Data Model** 找到。

![xml-files.png]({{strapiUrl}}/uploads/xml_files_25c2db561d.png)

通过右键菜单打开界面控制器。

![open-controller.png]({{strapiUrl}}/uploads/open_controller_d70576a34c.png)

请留意 XML 界面描述中的 data 部分，这里定义了如何从数据库读取数据。

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
界面创建之后，您可以用布局编辑器右上角的按钮预览界面。在预览界面可以看到，所有选择的实体属性都已经添加至界面。

![preview.png]({{strapiUrl}}/uploads/preview_ff61b86cbf.png)

UI 组件与数据是双向绑定的。在已绑定界面字段中的所有改动都会影响选择的数据，反之亦然。

![bound-data.png]({{strapiUrl}}/uploads/bound_data_a53602e4db.png)

现在我们生成 ```Task``` 实体的 CRUD 界面。在读取 ```Task``` 的同时，我们还要同时读取 ```Assignee``` 和 ```Project``` 实体。

![task-screens.png]({{strapiUrl}}/uploads/task_screens_93fbc29528.png)

下一步，需要的字段已经被选中。

![task-editor.png]({{strapiUrl}}/uploads/task_editor_8ba252c246.png)

使用 Jmix Studio 提供的窗口顶部的切换按钮可以很方便的在界面控制器、界面描述以及关联实体之间切换：

![navigate-controller.png]({{strapiUrl}}/uploads/navigate_controller_e18c6459c9.png)
 
![navigate-descriptor.png]({{strapiUrl}}/uploads/navigate_descriptor_b677194646.png)
 
![navigate-data-model.png]({{strapiUrl}}/uploads/navigate_data_model_6d99880909.png)

<div id="chapter4" class="section"></div>

## 开发模式运行应用程序

<div class="timestamp-wrapper">
   <a id="stamp4" class="timestamp-wrapper-buttons"><div class="timestamp">
    <img src="/images/learn/play.svg" class="delta">
    <div class="video-time">07:25</div>
  </div></a>
</div>

可以通过 IDE 窗口顶部的 **Run Configuration** 工具运行应用程序。

![run-configuration-menu.png]({{strapiUrl}}/uploads/run_configuration_menu_01f78288bb.png)

等程序启动之后，可以通过浏览器访问应用程序。默认地址是 http://localhost:8080/ 。

可以在 IDE 的 **Run** 窗口查看应用程序的运行日志。

![run-console.png]({{strapiUrl}}/uploads/run_console_3a43289d77.png)

在浏览器打开地址后，可以使用默认的用户名和密码 ```admin``` / ```admin``` 登录。

![login.png]({{strapiUrl}}/uploads/login_06139cb32c.png)

在 **Application** 菜单中，可以找到我们创建的实体操作界面。

![application-menu.png]({{strapiUrl}}/uploads/application_menu_f7c4aaf89b.png)

尝试添加一些数据，创建一个新的项目并将 ```admin``` 用户指派为项目的管理员。

![new-project-one.png]({{strapiUrl}}/uploads/new_project_one_3963b3ac58.png)

可以在创建项目的同时添加任务。

![new-task-one.png]({{strapiUrl}}/uploads/new_task_one_6a55c9589e.png)

我们创建一个新用户 - dev1（一号程序员）作为该任务的接收者。

![create-dev1.png]({{strapiUrl}}/uploads/create_dev1_85398f3aa7.png)

保存新创建的项目，任务也会自动保存。

<div id="chapter5" class="section"></div>

## 增加安全机制

<div class="timestamp-wrapper">
   <a id="stamp5" class="timestamp-wrapper-buttons"><div class="timestamp">
    <img src="/images/learn/play.svg" class="delta">
    <div class="video-time">08:25</div>
  </div></a>
</div>

在 Jmix 中，您可以创建角色，并赋予角色访问应用程序数据的权限，比如访问特定实体、实体属性，也可以赋予角色一些管理界面的功能权限，比如访问界面、菜单项。

打开 **Resource roles** 界面并创建“Developer”角色。从列表中选择 **Entity policy** 并允许开发人员查看和编辑任务实体。

![entity-policy-menu.png]({{strapiUrl}}/uploads/entity_policy_menu_260322af8a.png)

![entity-policy.png]({{strapiUrl}}/uploads/entity_policy_fc74f06cad.png)

但是只允许开发人员编辑任务的估算和开始时间。

![attributes-policy.png]({{strapiUrl}}/uploads/attributes_policy_0c8ed78391.png)

最后，添加查看浏览界面和编辑界面的权限。选择 **Grant access to the menu item** 添加 **Tasks** 至主菜单。

![browse-policy.png]({{strapiUrl}}/uploads/browse_policy_067f4c25b8.png)

![edit-policy.png]({{strapiUrl}}/uploads/edit_policy_9c1e735c04.png)

然后切换至 **Child roles** 标签页，为“Developer”添加另一个角色 - “UI: minimal access”，这个角色的作用是允许用户登录应用程序。

![minimal-role.png]({{strapiUrl}}/uploads/minimal_role_0da38e7a48.png)

将“Developer”角色分配给“dev1”用户。在 **Users** 界面选择 **Role assignments** 为用户添加角色。

![role-assingments.png]({{strapiUrl}}/uploads/role_assingments_1124380ca4.png)

现在我们用一号程序员的身份登录。可以看到，该用户只有访问指定界面和属性的权限。

![developer-login.png]({{strapiUrl}}/uploads/developer_login_446615a954.png)


<div id="chapter6" class="section"></div>

## 增加业务逻辑

<div class="timestamp-wrapper">
   <a id="stamp6" class="timestamp-wrapper-buttons"><div class="timestamp">
    <img src="/images/learn/play.svg" class="delta">
    <div class="video-time">09:38</div>
  </div></a>
</div>

现在我们将用 Jmix Studio 创建一个实现业务逻辑的服务，并在界面使用这个服务。这将是一个 Spring 服务，返回最空闲的用户。在管理 UI 中，我们将默认使用此服务为该用户分配任务。

通过 Jmix 工具窗口的工具栏打开常用的操作。选择 **Spring Bean** 然后输入类名 - ```TaskService```。

![create-service.png]({{strapiUrl}}/uploads/create_service_6695122e0b.png)

Studio 会生成一个空的 Spring bean。用 ```@Service``` 替换 ```@Component``` 注解。

![empty-class.png]({{strapiUrl}}/uploads/empty_class_8e00549665.png)

现在创建 ```findLeastBusyUser()``` 方法。在该服务中，我们将使用一个 Jmix 的服务 - ```DataManager```。这个服务可以使用 JPQL 查询语句帮我们访问数据。

使用窗口顶部的 Inject 按钮在服务中注入 ```DataManager```。

![inject-button.png]({{strapiUrl}}/uploads/inject_button_aa94f16b6a.png)

弹窗内选择 ```DataManager```。

![select-data-manager.png]({{strapiUrl}}/uploads/select_data_manager_ebaa015202.png)

添加该方法的实现内容如下：

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
1. JPQL 查询语句，用来查询用户并统计这些用户已经分配的任务数。
2. 选择第一个用户（任务数最少的）。
3. 返回该用户。

服务写好了，我们在任务编辑界面使用它。

点击位于界面控制器窗口顶部的 **Generate Handler** 按钮，然后选择 ```InitEntity``` 事件。

![generate-handler.png]({{strapiUrl}}/uploads/generate_handler_5e2fcad2e6.png)

![init-entity-event.png]({{strapiUrl}}/uploads/init_entity_event_c48ed9d898.png)

这里是该方法的实现：

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

1. 将 ```TaskService``` 服务注入到界面中。
2. 将服务方法的执行结果设置到任务的接收者字段。

完成了。我们重启一下应用程序，看看服务的真实执行情况。

首先，我们添加另外一个开发人员 - ```dev2```.

![create-dev2.png]({{strapiUrl}}/uploads/create_dev2_b94c1189ed.png)

我们已经给一号程序员分配了一个任务，所以目前最空闲的程序员应该是 Admin 或者二号程序员。

![create-task-two.png]({{strapiUrl}}/uploads/create_task_two_fdaadbf4b4.png)

增加的四项任务后，下一个最空闲的程序员将是 Admin 或者一号程序员，他们都只有一个任务。

![tasks-list.png]({{strapiUrl}}/uploads/tasks_list_f070d7b7e0.png)

<div id="chapter7" class="section"></div>

## 部署

<div class="timestamp-wrapper">
   <a id="stamp7" class="timestamp-wrapper-buttons"><div class="timestamp">
    <img src="/images/learn/play.svg" class="delta">
    <div class="video-time">11:45</div>
  </div></a>
</div>


下面我们看看如何用一个可执行的 JAR 文件部署 Jmix 应用程序。

首先，在 Jmix Studio 运行 ```boot:jar``` 命令。

![boot-jar.png]({{strapiUrl}}/uploads/boot_jar_68e7162b03.png)

文件打包好之后，切换到文件所在目录。

![navigate-terminal.png]({{strapiUrl}}/uploads/navigate_terminal_59b31fa661.png)

然后，运行命令：```java -jar <file_name>```。

![java-jar.png]({{strapiUrl}}/uploads/java_jar_28326f2f57.png)

现在可以打开浏览器查看应用程序的运行情况。

<div id="chapter8" class="section"></div>

## 总结

<div class="timestamp-wrapper">
   <a id="stamp8" class="timestamp-wrapper-buttons"><div class="timestamp">
    <img src="/images/learn/play.svg" class="delta">
    <div class="video-time">12:26</div>
  </div></a>
</div>

借助 Jmix，您可以在几分钟内实现一个可立即部署的 Spring Boot 应用程序，这要归功于强大的开发工具和代码生成器。
