---
id: ls03-teams-and-roles
slug: teams-and-roles
title: Teams and Roles
---

Teams and roles are the core of user and authentication management in Appwrite. They provide for a flexible and powerful way to manage access to your Appwrite's project and it's resources.

## Create Team

We should start by creating an instance of the teams service. We will use this service to create a new team.

```dart
final teams = Teams(client);
```

Now that we have an instance of the teams service, we can create a new team. We will use the `create` method to do this. This method takes a single parameter, `name`, which is the name of the team we want to create.

```dart
final team = await teams.create(name: 'My Team');
```

## Invite User

Now that we have a team, we can invite users to join it. We will use the `create` method of the teams service to do this. This method takes two parameters, `email` and `name`, which are the email and name of the user we want to invite.

```dart
final team = await teams.create(name: 'My Team');
final user = await teams.createMembership(email: 'user@gmail.com', name: 'User');
```

