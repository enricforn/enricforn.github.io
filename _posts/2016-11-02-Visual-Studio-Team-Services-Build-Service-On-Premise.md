---
layout: post
title: Configure on premise build server to Visual Studio Team Services
categories: [Visual Studio, Builds]
tags: [Visual Studio Team Services, Build, Release]
description: Description on how to connect your Build server to a team project on Visual Studio Team Services
---

In this post I suppose you are familiar to Visual Studio Team Services (from now VSTS). I'm gonna explain briefly how you can configure your own build server hosted on premise.

Build service is the feature from Visual Studio Team Services to automate your build process. Build service allows you to build your code, and run several tasks to assure your code quality. After this process you can create a release definition and deploy it to your environments. You can use a hosted build controller to run a build process after you check-in to source control ([TFVC](https://www.visualstudio.com/docs/tfvc/overview) or [GIT](https://www.visualstudio.com/en-us/docs/git/gitquickstart)).

You can configure your project to build automatically by following this [guide](https://www.visualstudio.com/en-us/docs/build/get-started/dot-net). This example is based on a standard .NET for Windows application, but VSTS Build can support any language and platform.

Ok, let's suppose we want to run [WinSCP](https://winscp.net) from our build process, and we need FileZilla to be installed in the build server. First of all, we would review if WinSCP is installed on a hosted build controller in this [list of software](http://listofsoftwareontfshostedbuildserver.azurewebsites.net/). WinSCP is not installed on hosted build servers.

If we must use WinSCP during our release process, then we should to create our own build server, in order to set up with all software we need to run in our build process.

If we compare build process from TFS2013 and before, the concept is slightly different: Controller instances do not exists, you only define queues and agents. Your queue can be configured as hosted or not. This means that you are using hosted server builds, or you configure agents hosted on premise.

Access your admin panel to download the agent:

![Build Service Configuration]({{ site.url }}/images/download-agent.PNG)

Depending on your platform, download the appropriate agent:

![Download agent depending on your platform]({{ site.url }}/images/download-agent-2.PNG)

Regardless which agent you configure, you should create a specific user to run this service. This user needs powerful permissions to do many tasks on your environment, and you should secure it.

#Configure Build Agent in VSTS or TFS15 

If you are using VSTS or TFS15 then download standard image.

Before running the agent configuration, you need to create a personal access token to access for VSTS:

![Creating a personal access token]({{ site.url }}/images/agent-config-2.PNG)

If you are using VSTS or TFS15 then download standard image and run ./config.cmd from command line to configure, its pretty easy:

![Configuring build agent VSTS]({{ site.url }}/images/agent-config-1.PNG)

As you can see in the image below, build agents are configured and running have a green flag. On the right side, you can see a list of builds that previously ran:

![Configured build agent VSTS]({{ site.url }}/images/agent-config-3.PNG)


#Configure Build Agent in TFS2013

If your VSTS or TFS version is older then you should download the legacy version, and then the following step differs a little bit:

First of all you should to keep in mind this point: you need to open TCP port 9191 in your firewall, in order to allow VSTS to connect to the service installed in you machine.

After the port service is opened you can configure the agent by running ./configure.cmd from command line:

![Configured build agent VSTS]({{ site.url }}/images/Configure-agent-powershell-command.PNG)

In windows environment, create agent as service, allows you to manage service from server without access to VSTS:

![VSTS Build Agent configured as service]({{ site.url }}/images/Agent-created-as-a-service.PNG)

