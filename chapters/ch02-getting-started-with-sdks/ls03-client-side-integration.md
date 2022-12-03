---
id: ls03-client-side-integration
title: Client Side SDKs
---

Another type of integration that we can have with Appwrite is the client side integration. This is the one to be used while building end user applications like front facing web pages and mobile applications. Appwrite provides client SDKs for web, Flutter, Android, iOS at the moment and more are being worked on. As Appwrite is fully open source, if you see a platform that Appwrite doesn’t have SDK for which you can develop, you can contribute. However, even without SDK you can easily integrate Appwrite using it’s REST APIs which we will talk about in a separate book. To connect with client side SDKs you need to follow few steps let’s look at them below.

### Add SDK dependency

In your client project add the SDK as the dependency. For example for Flutter you need to add the latest version of appwrite package as dependency in the `pubspec.yaml` as the following.

```yaml
dependencies:
	appwrite: "<version>"
```

// examples for each platform?

### Initialize with Endpoint and Project ID

Like with server side SDKs the client side SDKs do need endpoint and project ID to connect to the correct server and project. You can get it the similar way as we did above for the server side integration by following the below steps.

### Add Platform

In order for the server to validate the request you need to add details of your application that you are connecting from. You can do that in the project dashboard by adding a platform. Based on which client platform you are building for you need different information to let server know about our application. If you are building a web application you just need the URL that your application will be deployed to so that Appwrite will know all the requests coming from that URL is a valid request. Similarly if you are building a mobile or a desktop application you might need to add your application ID. We will look at how we can add each supported platform in the upcoming sections.
