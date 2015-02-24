---
layout: post
title: Connect to TFS2013 or  Visual Studio Online and access to WorkItemStore
categories: [TFS,Visual Studio]
tags: [TFS Object Model]
description: How to connect to TFS or Visual Studio online through API and get WorkItemStore service. Brief description of encountered issues and how to solve them.
---

In this post, I detail how you can access to Team Foundation Server 2013 (on premise) through its API. Once we can connect to the server, we will get an instance of a TFS service, in this example we will access to WorkItemStore, and we'll get a list of all existing user stories in a team project. I suppouse you are familiar to [TFS](http://www.visualstudio.com/en-us/products/tfs-overview-vs.aspx), and you are used to work with [WorkItems](https://msdn.microsoft.com/en-us/library/hh409275.aspx)) and [WIQL](https://msdn.microsoft.com/en-us/library/bb130306.c#).
Ok, let's start with a sample c# console application called TFSUserStoriesConsole. Open your Visual Studio and create a new Visual C# Console Application (File -> New -> Project -> Visual C#). Then we create a class which manage connection to TFS, and get the instance of WorkItemStore object. WorkItemStore let you to get workitems from TFS. Let me show you a piece of code:

         teamProjectCollection = new TfsTeamProjectCollection(tfsUri, myCredentials);

         teamProjectCollection.EnsureAuthenticated();

         workItemStore = teamProjectCollection.GetService<WorkItemStore>();


We connect to TFS, ensure we are connected to it, and finally we get the instance of WorkItemStore. It's strange because workItemStore equals null and I don't get more information about it.


The way I've found to get more information about this null, is create a new instance of WorkItemStore:

         WorkItemStore workItemStore = new WorkItemStore(teamProjectCollection);


In my case seems that I missed some assemblies to reference:


Type: System.IO.FileNotFoundException
Message: Could not load file or assembly 'Microsoft.TeamFoundation.WorkItemTracking.Proxy, Version=14.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a' or one of its dependencies. The system cannot find the file specified.
Source: Microsoft.TeamFoundation.WorkItemTracking.Client
StackTrace:    at Microsoft.TeamFoundation.WorkItemTracking.Client.WorkItemStore.InitializeInternal()
   at Microsoft.TeamFoundation.WorkItemTracking.Client.WorkItemStore.Microsoft.TeamFoundation.Client.ITfsTeamProjectCollectionObject.Initialize(TfsTeamProjectCollection teamProjectCollection)
   at Microsoft.TeamFoundation.Client.TfsTeamProjectCollection.InitializeTeamFoundationObject(String fullName, Object instance)
   at Microsoft.TeamFoundation.Client.TfsConnection.CreateServiceInstance(Assembly assembly, String fullName)
   at Microsoft.TeamFoundation.Client.TfsConnection.GetServiceInstance(Type serviceType, Object serviceInstance)
   at Microsoft.TeamFoundation.Client.TfsTeamProjectCollection.GetServiceInstance(Type serviceType, Object serviceInstance)
   at Microsoft.TeamFoundation.Client.TfsConnection.GetService(Type serviceType)
   at Microsoft.TeamFoundation.Client.TfsConnection.GetService[T]()


Ok, much easier getting a stacktrace to solve the problem. I added that reference, but I get another error:


Message: Error HRESULT E_FAIL has been returned from a call to a COM component.
Source: Microsoft.TeamFoundation.WorkItemTracking.Client.DataStoreLoader
StackTrace:    at Microsoft.TeamFoundation.WorkItemTracking.Client.DataStore.DataStoreNative.UpdateMetadata(IntPtr handle, Object rowset, String dbstamp, UInt32& changes)
   at Microsoft.TeamFoundation.WorkItemTracking.Client.DataStore.Datastore.UpdateMetadata(Object rowset, String dbstamp)
   at Microsoft.TeamFoundation.WorkItemTracking.Client.WorkItemStore.EndBackendCall(BackendCallData data)
   at Microsoft.TeamFoundation.WorkItemTracking.Client.WorkItemStore.RefreshCacheInternal(BackendCallData& data)
   at Microsoft.TeamFoundation.WorkItemTracking.Client.WorkItemStore.InitializeInternal()
   at Microsoft.TeamFoundation.WorkItemTracking.Client.WorkItemStore.Microsoft.TeamFoundation.Client.ITfsTeamProjectCollectionObject.Initialize(TfsTeamProjectCollection teamProjectCollection)
   at Microsoft.TeamFoundation.Client.TfsTeamProjectCollection.InitializeTeamFoundationObject(String fullName, Object instance)
   at Microsoft.TeamFoundation.Client.TfsConnection.CreateServiceInstance(Assembly assembly, String fullName)
   at Microsoft.TeamFoundation.Client.TfsConnection.GetServiceInstance(Type serviceType, Object serviceInstance)
   at Microsoft.TeamFoundation.Client.TfsTeamProjectCollection.GetServiceInstance(Type serviceType, Object serviceInstance)
   at Microsoft.TeamFoundation.Client.TfsConnection.GetService(Type serviceType)
   at Microsoft.TeamFoundation.Client.TfsConnection.GetService[T]()

In this case I monitor the process with [FileMon](https://technet.microsoft.com/en-us/sysinternals/bb896645) and the process ends with an access denied to folder   C:\ProgramData\Microsoft Team Foundation\4.0\Cache

Once I gave write permissions to C:\ProgramData\Microsoft Team Foundation\4.0\Cache the application runs properly.

You can find this errors when you install it to a server which is not TFS data tier and without Visual Studio installed either.

Sample code can be found at [Github](https://github.com/enricforn/sampleapplications/tree/master/csharp/TFSUserStoriesConsole). 

Hope it helps and you save time to solve this problems.
