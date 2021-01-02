### REST API 
by Haulmont

Back to marketplace

### Latest Version
0.2.0

### Updated
2 weeks

### Supported Version
v0.2

### Licence
Apache 2.0

### Ressources
Documentation
Bugtracker

### Tags
Integration
Integration 

### Component Coordinates

Copy

### OVERVIEW

Jmix provides a generic REST API that allows you to work with data model entities and business services without writing REST controllers on the backend. It automatically exposes endpoints for the following functionality:

* CRUD operations on entities.
* Calling of registered service methods.
* Execution of predefined JPQL queries.
* Uploading and downloading files.
* Returning information about the data model.
* Returning information about the current user and their permissions.

REST API uses the OAuth2 protocol for authentication and supports anonymous access. All REST API endpoints respect data access constraints imposed by security.

Jmix 提供了一套通用的 REST API ，使用这些 API 你可以处理实体数据、调用业务服务，而不需要编写后端 REST 控制器。通用 API 会提供以下功能：

* 对实体的 CRUD 操作
* 调用注册的服务方法
* 执行预定义的 JPQL 查询 
* 上传下载文件
* 返回数据模型信息 
* 当前当前用户及其权限信息

### NOTE
### 注意
Frontend UI works with Jmix backend through the generic REST API.
Frontend UI 通过通用 REST API 与 Jmix 后端集成 

### INSTALLATION

To include REST API in your application, add the following line to the dependencies section of your build.gradle file:

要给应用程序添加 REST API，将以下行添加到你的 build.gradle 文件中的 dependencies 部分。

BUGTRACKER
GITHUB
FORUM