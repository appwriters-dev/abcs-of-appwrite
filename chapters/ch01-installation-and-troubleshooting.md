---
id: ch01-installation-and-troubleshooting
title: Installation & Troubleshooting
---

Appwrite is an open source back-end as a service (BaaS) application, that recently has gained a lot of momentum. People have been looking at Appwrite as an open source alternative to Google’s Firebase. Appwrite abstracts away the complexities of modern application development by providing nice set of REST and Realtime APIs to most repetitive task in application development. Appwrite provides services like authentication & user management, database, storage, cloud functions, web-hooks and more. Appwrite is free and open source, means you can host your own instance of Appwrite and own your data.

By the end of this book you will learn what Appwrite is and why is it important for developers. You will also understand how Appwrite helps you to build robust applications rapidly. You will also learn to install and troubleshoot Appwrite locally for development as well as for production. Finally, you will learn to setup Appwrite for production use by updating configurations to make it suitable for your production needs.

In this book we will cover the following main topics

- Introduction to Appwrite
- Installing Appwrite Locally or in Cloud
- Understanding Appwrite Environment Configurations
- Configuring Appwrite for Production
- Troubleshooting Appwrite Issues

## Technical Requirements

To learn the contents of this book effectively, you will need following resources

- Docker 20.10 or later
- Docker compose 2.2 or later
- Basic knowledge of working with command line
- Basic knowledge and understanding docker and docker compose ([https://docs.docker.com/get-started/](https://docs.docker.com/get-started/))

You can get additional resources regarding this book in always update web page at [https://appwrite.dlohani.com.np](https://appwrite.dlohani.com.np)

## Introduction to Appwrite

If you are a developer you already know, building modern application is difficult. On top of that, building robust, secure, performant, and scalable app is even harder. You have to take care of tons of different aspects and you will have to have expertise in different areas like security, database, system design and more. This is where [Appwrite](https://appwrite.io) comes in. Appwrite is working to make development of modern applications easy, fun and accessible with it’s Backend-as-a-Service (BaaS) platform.

Appwrite is an open-source, secure and scalable BaaS that provides developers with everything they need to rapidly build robust modern applications. Appwrite is packaged as a set of docker micro services, Appwrite provides a suite of **easy-to-use** APIs, SDKs, tools to build features, not write boilerplate.

By default Appwrite already provides following services

1. Authentication and user management along with teams
2. Highly customizable database with MySQL and MariaDB integration
3. Storage for buckets and files management locally or on S3 compatible object storage
4. Cloud functions with 10+ language runtime support
5. Powerful, flexible permission management

We will learn about each of these services in its own dedicated book.

Appwrite is designed to be cross-platform and technology-agnostic, meaning we can install and run Appwrite on any system that supports Docker and Appwrite integrates well with any language and framework. Appwrite officially provides SDKs for 10+ languages and frameworks, however you can integrate it with any language and framework that can work with REST API and web-socket API. To see the list of all the official SDKs visit [https://appwrite.io/docs/sdks](https://appwrite.io/docs/sdks). Appwrite also provides up to date Swagger and Open-Api specs if you want to build your own SDK or use the REST API directly.
