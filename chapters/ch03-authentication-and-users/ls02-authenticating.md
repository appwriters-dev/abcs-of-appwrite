---
id: ls03-authenticating
title: Authenticating
---

Once you create the account for an user with email and password like you learned in the previous section, you need to create a session for the user to authenticate. The session generates a cookie that you can use to authenticate the user in the future. No worries, cookies are automatically handled by the SDK.

## Create Email Session

When you create a user with email and password, you can use the email and password to create a session for the user. The session is created with the `account.createEmailSession` method.

```dart
final session = await client.account.createEmailSession(
  email: 'user1@appwrite.io',
  password: 'password',
);
```

Once you successfully create the session, all the subsequent request from the SDK using the same `Client` instance will include the user's cookie in the request headers. This means that you don't need to manually handle the cookie.

However, this is only one of the way to create a session. You can also create an anonymous session, or create session using OAuth2, Magic Link, or Phone Number. Let's look at each of those methods.

## Create Anonymous Session

What if, you don't want to ask user for email and password? For various reasons, to reduce friction, for privacy reason or anything else. Well, Appwrite provides a way to create an anonymous session for the user. The anonymous session is created with the `account.createAnonymousSession` method. The method doesn't require any parameters.

> Note: Creating an anonymous session also creates a new anonymous user account in the Appwrite server.

```dart
final session = await account.createAnonymousSession();
```

That's it, once you create an anonymous session, all the subsequent request from the SDK using the same `Client` instance will include the new user's cookie in the request headers automatically.
