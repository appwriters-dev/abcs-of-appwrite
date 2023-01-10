---
id: ls02-authenticating
title: Authenticating
---

Once you create the account for an user with email and password like you learned in the previous section, you need to create a session for the user to authenticate. The session generates a cookie that you can use to authenticate the user in the future. No worries, cookies are automatically handled by the SDK.

## Create Session

There are several ways to create sessions in Appwrite. You can create anonymous session, email and password based sessions and more. Let's look at  them.

### Create Email Session

When you create a user with email and password, you can use the email and password to create a session for the user. The session is created with the `account.createEmailSession` method.

```dart
final session = await client.account.createEmailSession(
  email: 'user1@appwrite.io',
  password: 'password',
);
```

Once you successfully create the session, all the subsequent request from the SDK using the same `Client` instance will include the user's cookie in the request headers. This means that you don't need to manually handle the cookie.

However, this is only one of the way to create a session. You can also create an anonymous session, or create session using OAuth2, Magic Link, or Phone Number. Let's look at each of those methods.

### Create Anonymous Session

What if, you don't want to ask user for email and password? For various reasons, to reduce friction, for privacy reason or anything else. Well, Appwrite provides a way to create an anonymous session for the user. The anonymous session is created with the `account.createAnonymousSession` method. The method doesn't require any parameters.

> Note: Creating an anonymous session also creates a new anonymous user account in the Appwrite server.

```dart
final session = await account.createAnonymousSession();
```

That's it, once you create an anonymous session, all the subsequent request from the SDK using the same `Client` instance will include the new user's cookie in the request headers automatically.

### Create OAuth2 Session

Appwrite supports OAuth2 authentication. You can use the `account.createOAuth2Session` method to create a session for the user using OAuth2. The method requires the `provider` parameter. The `provider` parameter is the name of the OAuth2 provider. For example, if you want to use Google OAuth2, the `provider` parameter will be `google`.

You have to enable the provider in the Appwrite console before you can use it.

```dart
final session = await account.createOAuth2Session(
  provider: 'google',
);
```

> Note: Creating a OAuth2 session also creates a new user account if the account doesn't exist for the email associated with the OAuth2 account.

### Create Magic Link Session

Appwrite also supports Magic Link authentication. You can use the `account.createMagicURLSession` method to create a session for the user using Magic Link. The method requires the `email` parameter. The `email` parameter is the email of the user.

```dart
final session = await account.createMagicURLSession(
  email: 'user1@appwrite.io',
);
```

> Note: Creating a Magic Link session also creates a new user account if the account doesn't exist for the email.

### Create Phone Number Session

Appwrite also supports Phone Number authentication. You can use the `account.createPhoneSession` method to create a session for the user using Phone Number. The method requires the `phoneNumber` parameter. The `phoneNumber` parameter is the phone number of the user.

```dart
final session = await account.createPhoneSession(
  phoneNumber: '+123456789',
);
```

> Note: Creating a Phone Number session also creates a new user account if the account doesn't exist for the phone number.

## Checking Authentication Status

Whenever your application restarts or whenever you are making a authenticated request to the server, though server has authentication checks, it's always better to have a status check in the client as well. In order to check whether or not the user is authenticated, we can simply call `account.get()` to get the user account details. If the user is authenticated, the method will return the user account details. If the user is not authenticated, the method will throw an exception.

```dart
try {
  final account = await client.account.get();
  // user is authenticated
} on AppwriteException catch (e) {
  if(e.code == 401) {
    // user is not authenticated
  } else {
    // some other error
  }
  print(e.message);
}
```

In Flutter it's always a good practice to use state management to handle authentication so that you can easily update the UI when the authentication status changes. You can use the `account.get()` method to check the authentication status and update the state accordingly.

## Logging Out

Logging out in Appwrite is deleting the current active session. To do that we can call `account.deleteSession()` with the session ID. No worries, we don't have to save the session ID exclusively, instead we can pass `current` as the session ID so that it deletes the currently active session.

```dart
await account.deleteSession(sessionId: 'current');
```

Once you delete the session, the cookie will no longer be valid and all the subsequent request will not be authorized.
