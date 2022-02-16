# WebDAV
# WebDAV

Enables collaborative work on documents located in the file storage using WebDAV protocol.
支持使用 WebDAV 协议对文件存储中的文件协作共享。

## Overview
## 介绍

Jmix WebDAV add-on provides powerful functionality for collaborative work on documents of various formats.
Jmix WebDAV 扩展插件为各种格式的文档协作功能提供了强大的支持。

The add-on enables the WebDAV protocol over the standard Jmix file storage API, which allows users to seamlessly open and edit files using their desktop applications (Word, Excel, LibreOffice, etc.) without the need to download and upload files to the web application.
该扩展插件在标准的 Jmix 文件存储 API 之上启用了 WebDAV 协议，这样用户可以使用桌面客户端程序（Word，Excel，LibreOffice 等）无缝的打开并编辑在线文件，无需手动上传下载。

## Features
## 功能

- Operating with documents in applications that support WebDAV (such as Microsoft Office) straight from the server.  
- Visual components to work with files and file versions in the application UI.
- Full support for collaborative work and file versioning, manageable both from the client application and the application UI.
- Configurable conflict resolution policies.
- Simple management of file access control via full integration with Jmix security subsystem.
- Access to files from external systems using static links.

- 在支持 WebDAV 协议的应用程序（比如微软的 Office）中直接操作服务器的文件。
- 提供 Jmix 应用中的可视化组件，用于处理文件和文件版本。
- 全面支持共享协作和文件版本管理，支持从客户端软件和 Jmix UI 进行管理。
- 可配置的冲突解决策略。
- 通过全面集成 Jmix 安全子系统，提供简洁的文件访问控制管理。
- 为外部系统提供文件访问的静态链接。

Files are stored in the standard Jmix file storage, so there is no need for an external WebDAV server.
文件存于标准的 Jmix 文件存储中，因此无需额外的 WebDAV 服务器。
