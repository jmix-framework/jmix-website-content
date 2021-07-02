# Multitenancy

## Overview

The add-on provides support for building multitenant applications with a single database.

The add-on supports two types of data:

- common data - shared across tenants. Tenants have read-only access to this type of data;
- tenant-specific data - not accessible to other tenants. Tenants have full access to this type of data.

All tenants have their own admin users which can create tenant users and assign tenant-specific roles.

Support for multitenant applications with a single database.