# Quartz
# Quartz

Enables managing Quartz jobs via user interface.
支持通过用户界面管理 Quartz 作业。

## Overview
## 介绍

This add-on allows you to manage [Quartz](https://www.quartz-scheduler.org/) jobs via user interface: create and remove jobs, schedule triggers, pause and resume job execution.
此扩展组件支持通过 UI 管理 [Quartz](https://www.quartz-scheduler.org/) 作业：创建和删除作业，定时触发，暂停和继续执行作业。

At development time, you should create implementations of the org.quartz.Job interface that will be invoked to do the actual job. At run time, the add-on allows you to configure and run the jobs defined in your application.
开发时，需要创建类实现 org.quartz.Job 接口，完成具体的作业任务。运行时，该扩展组件可以配置并执行应用程序中定义的作业。
