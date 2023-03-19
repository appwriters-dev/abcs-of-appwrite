---
id: ls01-appwrites-permission-structure
title: Appwrite's Permission Structure
---

Appwrite's permission structure is based on the teams and roles. Each team can have multiple users with multiple roles. Permissions are assigned based on teams and roles. There are also some special permissions that are not assigned to any team or role. Appwrite permission allows you to control access to your Appwrite project resources.

## Permission Types

Appwrite provides few types of permission and for each type Appwrite SDKs provides a helper classes and methods so it's easier to use permissions.

- **read** : `Permission.read()` - access to read resources (both listing and reading)
- **create** : `Permission.create()` - access to create resources
- **update** : `Permission.update()` - access to update existing resources
- **delete** : `Permission.delete()` - access to delete existing resources
- **write** : `Permission.write()` - access to create, update and delete resources

