---
layout: post
title: Five Reasons Why An Internal Developer Platform Is Worth It
categories: [DevOps, Platform, Efficiency]
tags: [development, software, devops,platform]
author: eforn
image: /images/posts/internal-developer-platform-is-worth-it/header.jpg
---

### Companies around the world increased the number of deployed apps by 9% in 2021, Okta study says. You would be interested in this post if you are concerned about how to accelerate or scale software development in your organization.

All types of companies regardless of their size are creating more software apps every day. Over the past four years, deployed apps per customer have risen for a combined growth of 22%, based on analysis by [Okta Inc](https://www.okta.com/businesses-at-work/2021/#fastest-growing-apps). Increased software codebase in organizations often means higher complexity of their systems. Add to that the shift to microservice architecture in cloud native setups, which has been underway for many years now. How can you deal with this complexity? How can you develop more software at the same pace or even faster? How do you rationalize your software and infrastructure?


In this post, you will learn how to deal with this complexity and productively scale your ecosystem of tools through an Internal Developer Platform.

## What is an Internal Developer Platform (IDP) and why doI need one

Internal Developer Platform is a set of tools, services, and processes that supports and accelerate your software development and the management of its infrastructure. 

Kaspar von Grünberg, Humanitec’s CEO [defines an IDP](https://humanitec.com/blog/what-is-an-internal-developer-platform) “as a self-service layer that allows developers to interact independently with their organization's delivery setup, enabling them to self-serve environments, deployments, databases, logs and anything else they need to run their applications.”

In their journey to an efficient software development process, teams often struggle with trying to find the right balance between the standardization of infrastructure and applications and giving enough freedom to developers to customize the applications and self-serve the tech they need. An IDP comes with standardization.

Let’s take the example of a developer creating a new application. Usually they would manually have to create a repo in the SCM, assign permissions to all contributors, create a ticket for the infrastructure team to provision resources like databases, file storage or DNS for the application and finally deploy the application. All of this is automated by an IDP, which also eliminates key person dependencies between developers and operations.

Additionally, we could develop a plugin in our preferred IDE or web application that, based on an application name, technology stack and traffic load requirements, automatically registers our new application in our Application Portfolio Catalog.

## Win-Win For Everyone

Some of the advantages listed below are closely interconnected. Let's detail the most important advantages of using or start implementing an IDP:

### **1. Alignment**

Through an IDP is explicitly implemented which kind of infrastructure you can deploy and which types of applications are supported. The offering is robust and well-defined. Everyone knows the expectations of the system. A detailed documentation on how each tool or integration works is crucial, to create transparency on the development process.

### **2. Compliance and Governance**

Having your development process implemented throughout an ecosystem of tools allows you to drive software development to satisfy some requirements. For example, from a software development lifecycle perspective, avoid anti patterns implemented by analyzing code statically. Digging a little bit more on this example, you can run an analysis using the sonar scanner of [Sonarqube](https://www.sonarqube.org/) as a step of your build process and use your standard [Quality Gate](https://docs.sonarqube.org/latest/user-guide/quality-gates/) which automatically decides if the analyzed code has the quality for being built. I used to customize [Quality Profile](https://docs.sonarqube.org/latest/instance-administration/quality-profiles/) with these [custom rules](https://github.com/davidetaibi/sonarqube-anti-patterns-code-smells). From an infrastructure perspective, by implementing an IDP, you can automate the provisioning of the [resources](https://humanitec.com/blog/what-are-resources-in-humanitec) needed, and assure that the platform is hardened and secured automatically. You can store information regarding your data, applications, and supported infrastructure. All these catalogs are commonly used by architects to manage applications and define evolution roadmaps.

### **3. Let Dev Teams Focus on Business Value**

An IDP brings self-service features by automating tasks, which your development teams do not have to worry about any longer. For example, imagine that we implement a feature in our IDP in which you type a name of the application, and define the required components (e.g., a React SPA, an NPM component and a web service implemented in Rust). By introducing this information to the IDP, you can automate the following tasks:
 * Automatically provision a group with some repositories in your SCM.
 * Create three repositories for each component and assign a pipeline to each repo as a webhook.
 * Apply a default template to the project.
 * Allocate resources to the development and production environment to allow the deployment of the application.

The usability of such a toolchain smooths the path of using your ecosystem of tools, and developers spend just minutes to click on the right options to allocate the resources needed.

### **4. Autonomy**

Developers have all the tools they need and are easily accessible to do the required job in the expected timeline. An IDP also enables teams to centralize interactions inside the platform. It liberates team members from dealing with ticketing tools with different workflows and instead interact with other teams. If you need to create a new application or business logic, you simply access the IDP and you are able to self-serve the resources you need.

### **5. Efficiency**

Autonomy in software development increases speed and reduces the cost of interacting with other teams in your organization. Your IDP must integrate a set of tools which allows using this ecosystem really fast. To check if you are on the right way, you should measure the efficiency in delivering software. Lead time, deployment frequency, change failure rate and mean time to recover are great indicators.

## Start Building Your IDP Now

The implementation of an [IDP](https://internaldeveloperplatform.org/) needs to be tailored to each organization. Start delivering small changes that benefit development teams in their daily work:

 1. Identify in your software development process actions to automate or integrations between tools developers use daily.
 2. Validate if there's any open source tool that fixes this gap, probably other teams had this problem before. Take a loot at [CNCF Cloud Native Interactive Landscape](https://landscape.cncf.io/), there's a bunch of useful tools.
 3. Integrate this new product whether it is built or bought as smoothly as possible to the development lifecycle.
 4. Measure the impact in terms of development performance ([How to measure your development process](https://enricforn.github.io/devops/2019/08/09/five-lessons-learned-from-devops-journey/#1-measure-your-development-process)), and share results with all stakeholders (Developers, Product Managers, C-Level).
 5. Repeat process.

You can also consider contacting companies experts in this field like [Humanitec](https://humanitec.com/) or [Shipa](https://shipa.io/), which has built great SaaS products.

Don't hesitate to contact me if you want more information about how to evolve your development ecosystem.

Thanks for reading!

### Interesting Links

- [Okta Businesses at Work report](https://www.okta.com/businesses-at-work/2021/#fastest-growing-apps)
- [Technology advance at exponential pace](https://en.wikipedia.org/wiki/Accelerating_change)
- [State Of The Developer Nation](https://www.slashdata.co/free-resources/state-of-the-developer-nation-21st-edition?)
- [The Global Home for Platform Engineers](https://platformengineering.org/)
- [IDP](https://internaldeveloperplatform.org/)
- [Internal Developer Platform](https://internaldeveloperplatform.org/)
- [CNCF Clout Native Interactive Landscape](https://landscape.cncf.io/)
- [CNCF Cloud Native Trail Map](https://github.com/cncf/landscape/blob/master/README.md#trail-map)
- [Humanitec](https://humanitec.com/)
- [Shipa](https://shipa.io/)
- [Sonarqube](https://www.sonarqube.org/)
- [Anti patterns and code smells](https://github.com/davidetaibi/sonarqube-anti-patterns-code-smells)