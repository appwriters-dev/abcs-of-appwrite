---
id: ch03-authentication-and-users
slug: authentication-and-user-management
title: Authentication and Users Management
---

Appwrite provides a set of APIs that allow you to manage your users and their authentication. You can use the Appwrite SDKs to easily integrate these APIs into your app. You can also use the Appwrite Console to manage your users. Appwrite provides teams and roles to help you manage your users and their permissions. Appwrite's permission model is very flexible and allows you to manage your users and their permissions in a way that suits your app's needs. We will learn more about permissions in the next chapter. In this chapter we will learn to manage users, teams and authentication.

This chapter will cover following Appwrite services:

* Account
* Users
* Teams

To use any of the Appwrite's services, you need to instantiate the service with an instance of the Appwrite client. You need to configure Appwrite SDK and client like we discussed in the previous chapter. Once that is done, you can instantiate the services as the following:

```dart
final account = Account(client);
final users = Users(client);
final teams = Teams(client);
```

Next we will learn how to create a new user account using the Account service.