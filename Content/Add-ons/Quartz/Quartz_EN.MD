# Quartz

Enables managing Quartz jobs via user interface.

## Overview

This add-on allows you to manage [Quartz](https://www.quartz-scheduler.org/) jobs via user interface: create and remove jobs, schedule triggers, pause and resume job execution.

At development time, you should create implementations of the org.quartz.Job interface that will be invoked to do the actual job. At run time, the add-on allows you to configure and run the jobs defined in your application.