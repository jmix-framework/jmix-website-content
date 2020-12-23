### Email 
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

### FEATURES
* Synchronous or asynchronous sending. In case of synchronous sending, the calling code waits till the message is sent to the SMTP server. In case of asynchronous sending, the message is persisted to the database and the control is returned immediately to the calling code. The actual sending is done later by a scheduled task.

* Reliable tracking of message sending timestamp or errors in the database for both synchronous and asynchronous modes.

* User interface to search and view information about sent messages, including all message attributes and content, sending status and the number of attempts.

### INSTALLATION
To include email sending functionality in your application, add the following lines to the dependencies section of your build.gradle file:

BUGTRACKER
GITHUB
FORUM