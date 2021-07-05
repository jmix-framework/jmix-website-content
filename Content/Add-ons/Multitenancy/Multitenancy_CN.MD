# Multitenancy
# 多租户

## Overview
## 简介

The add-on provides support for building multitenant applications with a single database.
该扩展支持使用单一数据库构建多租户应用程序。

The add-on supports two types of data:
该扩展支持两种数据类型：

- common data - shared across tenants. Tenants have read-only access to this type of data;
- tenant-specific data - not accessible to other tenants. Tenants have full access to this type of data.
- 通用数据 - 在租户间共享。所有租户对这些数据仅有只读权限；
- 租户特定数据 - 其他租户无法访问。各租户对其特定数据具有全访问权限。

All tenants have their own admin users which can create tenant users and assign tenant-specific roles.
所有租户都有独立的管理员用户，可以创建租户用户并分配租户特定的角色。

Support for multitenant applications with a single database.
支持使用单一数据库的多租户应用程序。
