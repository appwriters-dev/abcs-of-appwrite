---
id: ls03-client-side-integration
slug: client-side-integration
title: Client Side SDKs
---

Another type of integration that we can have with Appwrite is the client side integration. This is the one to be used while building end user applications like front facing web pages and mobile applications. Appwrite provides client SDKs for web, Flutter, Android, iOS at the moment and more are being worked on. As Appwrite is fully open source, if you see a platform that Appwrite doesn’t have SDK for which you can develop, you can contribute. However, even without SDK you can easily integrate Appwrite using it’s REST APIs which we will talk about in a separate book. To connect with client side SDKs you need to follow few steps let’s look at them below.

### Add SDK dependency

In your client project add the SDK as the dependency. For example for Flutter you need to add the latest version of appwrite package as dependency in the `pubspec.yaml` as the following.

```yaml
dependencies:
	appwrite: "<version>"
```

<!-- TODO examples for each platform? -->

### Initialize with Endpoint and Project ID

Like with server side SDKs the client side SDKs do need endpoint and project ID to connect to the correct server and project. To get the endpoint and project ID head over to settings page for your project in the console. There you can find the project ID and the API Endpoint.

![Project Settings](/images/project-settings.png)

Once you have got the endpoint and project ID you can initialize the SDK with them. For example in Flutter you can initialize the SDK as the following.

```dart
import 'package:appwrite/appwrite.dart';

final client = Client();
client
	.setEndpoint('https://[HOSTNAME_OR_IP]/v1') // Your API Endpoint
	.setProject('flappwrite') // Your project ID
	.setSelfSigned(); // Only use in development when you don't have valid Domain and SSL for your Appwrite server
;
```
Once you have initialized the SDK, before you can use it to make calls to Appwrite server you need to add platform to your project. This is required to validate the request coming from your application. We will look at how to add platform in the next section.

### Add Platform

In order for the server to validate the request you need to add details of your application that you are connecting from. You can do that in the project dashboard by adding a platform. Based on which client platform you are building for you need different information to let server know about our application. If you are building a web application you just need the URL that your application will be deployed to so that Appwrite will know all the requests coming from that URL is a valid request. Similarly if you are building a mobile or a desktop application you might need to add your application ID. We will look at how we can add each supported platform in the upcoming sections.

<!-- Adding platform steps and screenshots -->

### Make API calls

Once you have added the platform you can start making API calls to Appwrite server. For example in Flutter you can make API calls as the following.

```dart
final account = Account(client);

try {
	final user = await account.create(email: 'hello@appwriters.dev', password: 'mystrongpassword');
} on AppwriteException catch (e) {
	print(e.message);
}
```

<!-- other platform examples -->

We will learn about each service and making various API calls in the upcoming chapters.

> More updates soon..
