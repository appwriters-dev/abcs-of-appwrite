---
id: ls05-understanding-appwrite-projects
slug: understanding-projects
title: Understanding Appwrite Projects
---

Appwrite projects are the core of your Appwrite application. They are the place where you can manage all your Appwrite resources, such as databases, functions, authentication, storage, and more. You can also manage your project settings, such as API keys, platforms, teams, and more. Appwrite services are grouped into projects so that developers can serve multiple applications from a single Appwrite instance. Projects keeps the resources of each application separate and secure.

In this section we will learn how to create a new Appwrite project and how to manage it.

## Creating a New Project

To create a new Appwrite project, you need to open the Appwrite console and click on the **Create Project** button.

1. Click on the **Create Project** button.
2. On the dialog that appears enter a name for your project.
3. If you want to provide a custom ID click on **Project ID** button and provide a custom ID in the field that appears
4. Click on the create button to create the project.

![Create Project](/images/ch01-ls05-1.png)

Once the project is created, you will be redirected to the project dashboard. The project dashboard is the place where you can manage all your Appwrite resources and settings.

## Getting to Know the Project Dashboard

The project dashboard is the place where you can manage all your Appwrite resources and settings. It provides various sections that you can use to manage your project's resources and settings.

![Project Dashboard](/images/ch01-ls05-2.png)

1. Sidebar: The sidebar provides quick access to all the resources of the project. You can use the sidebar to navigate between the resources and settings.
2. Account: Use the link to get your account details and manage organization
3. Link to Settings: Use the link to get to the project settings
4. Main Dashboard: The main dashboard provides a quick overview of the project's resources and settings. You can add platforms and API keys as well as view some usage stats regarding your project.

Going to each link from the sidebar you can manage individual resources of your project. We will learn about all of those resources and services in their respective sections.

### Project Settings

The project settings provide information about project like the project id, API endpoint, that are later required to connect to your Appwrite services using the Appwrite SDKs and API. You can also use the settings to enable, disable the project's services like databases, authentication, and more. You can also delete the project from the settings page. Be careful when deleting a project as it will delete all the resources associated with the project and it's irreversible.

![Project Settings](/images/ch01-ls05-3.png)

There are two additional tabs in the settings page to manage the project's associated domains and webhooks.