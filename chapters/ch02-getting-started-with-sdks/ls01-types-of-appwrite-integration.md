---
id: ls01-types-of-appwrite-integration
title: Types of Appwrite Integration
---

Appwrite is more than just a Back-end-as-a-Service, its extendable in a way that you can build your own tailored back-end on top of Appwrite. So Appwrite currently provides two types of integration. One, server side integration with elevated permission using API keys and another client side integration suitable to use directly with platforms to build end user applications. Appwrite being technology and platform agnostic, it integrates well with any platform or framework that support REST API. Appwrite already provides tons of SDKs for various framework and languages. To find the list of all supported SDKs visit [https://appwrite.io/docs/sdks](https://appwrite.io/docs/sdks). This is where we will always find the up to date list of supported SDKs.

## Server Side SDKs

Appwrite’s server side SDKs provide a way to extend Appwrite and build our own custom services on top of it as server side integration has elevated permissions and access. It is mostly useful for setups, configurations and extending Appwrite to build your own custom features on top of it. It can even be used with Appwrite’s Functions to extend and add new functionalities. As it uses API keys wit elevated access that is given to the key, you must be careful not to expose such services to public. With permitted keys, they can have unrestricted access to resources on your Appwrite instance. We will look into details in the next steps how to allow only needed permissions to an API key so that even if it’s exposed only the resources it has access to is affected.

## Client Side SDKs

Another type of integration that we can have with Appwrite is the client side integration. This is the one to be used while building end user applications like front facing web pages and mobile applications. Appwrite provides client SDKs for web, Flutter, Android, iOS at the moment and more are being worked on. As Appwrite is fully open source, if you see a platform that Appwrite doesn’t have SDK for which you can develop, you can contribute. However, even without SDK you can easily integrate Appwrite using it’s REST APIs which we will talk about in a separate book. To connect with client side SDKs you need to follow few steps let’s look at them below.