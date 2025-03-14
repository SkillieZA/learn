﻿In this unit, you learn how to create an Azure App Service web app using the Azure portal.

## Why use the Azure portal?

The first step in hosting your web application is to create a web app (an Azure App Service app) inside your Azure subscription.

There are several ways you can create a web app. You can use the Azure portal, the Azure Command Line Interface (CLI), a script, or an integrated development environment (IDE) like Visual Studio.

The information in this unit discusses how to use the Azure portal to create a web app, and you use this information to create a web app in the next exercise. For this module, we demonstrate using the Azure portal because it's a graphical experience, which makes it a great learning tool. The portal helps you discover available features, add other resources, and customize existing resources.

## What is Azure App Service?

Azure App Service is a fully managed web application hosting platform. This platform as a service (PaaS) offered by Azure allows you to focus on designing and building your app while Azure takes care of the infrastructure to run and scale your applications.

### Deployment slots

Using the Azure portal, you can easily add **deployment slots** to an App Service web app. For instance, you can create a **staging** deployment slot where you can push your code to test on Azure. Once you're happy with your code, you can easily **swap** the staging deployment slot with the production slot. All it takes is a few mouse clicks in the Azure portal.

:::image type="content" source="../media/2-deployment-slots.png" alt-text="Screenshot of the staging deployment slot to test the deployments.":::

### Continuous integration/deployment support

The Azure portal provides out-of-the-box continuous integration and deployment with Azure Repos, GitHub, Bitbucket, FTP, or a local Git repository on your development machine. You can connect your web app with any of the preceding sources, and App Service does the rest for you. It automatically syncs your code and any future changes on the code into the web app. Furthermore, with Azure Repos, you can define your own build and release process. A full process that compiles your source code, runs the tests, builds a release, and finally deploys the release into your web app every time you commit the code. All that happens implicitly, without any need for you to intervene.

:::image type="content" source="../media/2-continuous-integration.png" alt-text="Screenshot of setting up deployment options and choosing source for the deployment source code.":::

### Integrated Visual Studio publishing and FTP publishing

In addition to being able to set up continuous integration/deployment for your web app, you can always benefit from the tight integration with Visual Studio to publish your web app to Azure via Web Deploy technology. App Service also supports FTP-based publishing for more traditional workflows.

### Built-in autoscale support (automatic scale-out based on real-world load)

The ability to scale up/down or scale out is baked into the web app. Depending on the web app's usage, you can scale your app up/down by increasing/decreasing the resources of the underlying machine that's hosting your web app. Resources can be the number of cores or the amount of RAM available. On the other hand, you can scale out your app by increasing the number of machine instances that are running your web app.

## Creating a web app

When you're ready to run a web app on Azure, you can visit the Azure portal and create a **Web App** resource. Creating a web app allocates a set of hosting resources in App Service. You can use these resources to host any web-based application Azure supports, whether it's ASP.NET Core, Node.js, Java, Python, and so on.

The Azure portal provides a wizard to create a web app. This wizard requires the following fields:

| *Field* | *Description* |
|---|---|
| **Subscription** | A valid and active Azure subscription. |
| **Resource group** | A valid resource group. |
| **Name** | The name of the web app. This name becomes part of the app's URL, so it must be unique among all Azure App Service web apps. |
| **Publish** | You can deploy your application to App Service as **code** or as a ready-to-run Docker **Container**. Selecting **Container** activates the wizard's Container tab, where you provide information about the Docker registry from which App Service retrieves your image. |
| **Runtime stack** | If you choose to deploy your application as code, App Service needs to know what runtime your application uses (examples include Node.js, Python, Java, and .NET). If you deploy your application as a container, you don't need to choose a runtime stack, because your image includes it. |
| **Operating system** | App Service can host applications on **Windows** or **Linux** servers. For more information, see the *Operating systems* section in this unit. |
| **Region** | The Azure region from which your application is served. |
| **Pricing Plans** | See the *Pricing Plans* section in this unit for information about App Service plans. |

### Operating systems

If you're deploying your app as code, many of the available runtime stacks are limited to one operating system or the other. After you choose a runtime stack, the toggle will indicate whether or not you have a choice of operating system. If your target runtime stack is available on both operating systems, select the one that you use to develop and test your application.

If your application is packaged as a container, specify the operating system in your container.

### App Service plans

An **App Service** plan is a set of virtual server resources that run App Service apps. A plan's **size** (sometimes referred to as its **sku** or **pricing tier**) determines the performance characteristics of the virtual servers that run the apps assigned to the plan, and the App Service features to which those apps have access. Every App Service web app you create must be assigned to a single App Service plan that runs it.

A single App Service plan can host multiple App Service web apps. In most cases, the number of apps you can run on a single plan is limited by the apps' performance characteristics and the plan's resource limitations.

App Service plans determine the App Service's unit of billing. The size of each App Service plan in your subscription, in addition to the bandwidth resources the apps deployed to those plans use, determines the price you pay. The number of web apps deployed to your App Service plans has no effect on your bill.

You can use any of the available Azure management tools to create an App Service plan. When you create a web app via the Azure portal, the wizard helps you to create a new plan at the same time if you don't already have one.
