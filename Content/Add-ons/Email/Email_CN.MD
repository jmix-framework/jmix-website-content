### Email
### 邮件
by Haulmont

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
Features

### Component Coordinates

Copy 

OVERVIEW
The addon provides email sending facilities.
此扩展提供电子邮件发送基础设施。

### FEATURES
### 功能
* Synchronous or asynchronous sending. In case of synchronous sending, the calling code waits till the message is sent to the SMTP server. In case of asynchronous sending, the message is persisted to the database and the control is returned immediately to the calling code. The actual sending is done later by a scheduled task.

* Reliable tracking of message sending timestamp or errors in the database for both synchronous and asynchronous modes.

* User interface to search and view information about sent messages, including all message attributes and content, sending status and the number of attempts.

* 支持同步或异步发送。在同步发送时，调用方会等待消息发送到 SMPT 服务器。异步发送时，消息被存在到数据库并立即返回。实际的发达随后由计划任务完成。

* 两种模式下都会存储发送错误或成功信息到数据库，以进行可靠性跟踪

* 提供用于搜索和查看有送已发消息的信息的界面，包括所有消息属性和内容、发送状态和尝试次数。

### INSTALLATION
### 安装
To include email sending functionality in your application, add the following lines to the dependencies section of your build.gradle file:

要给应用程序添加电子邮件功能，添加以下行到 builg.gradle 文件的 dependencies 部分。 

BUGTRACKER
GITHUB
FORUM