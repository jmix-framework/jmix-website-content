# Application Settings
# 应用程序参数

Provides a simple API and UI to work with mutable values of different types stored in database.
提供了简洁的 API 和 UI，用来处理数据库中存储的不同类型参数值。

## Overview
## 介绍

The Application Settings add-on provides a simple API and UI to work with mutable values of different types stored in the database. These values are usually used as parameters of different functionality of the application.
此扩展组件提供了简洁的 API 和 UI，用来处理数据库中存储的不同类型参数值。这些值通常作为应用程序不同功能的参数使用。

Settings are defined by regular entities, the only requirement for them is to extend a specific base class. You can set default values of parameters using annotations on the settings entity class.
配置定义在常规实体中，只需要它们从一个特殊的基类继承。参数的默认值通过在配置定义实体类使用注解配置。

The API enables loading settings by the entity class and saving changed values. The add-on also provides a UI screen for managing settings at runtime.
使用 API 可以通过实体类加载配置或保存修改的参数。该扩展组件还提供了运行时管理参数的 UI 界面。
