---
layout: post
title: TFS 2017 Package Management Feature for npm
categories: [TFS, ALM, npm]
tags: [TFS, Package Management, ALM, npm]
image: /images/posts/tfs-package-management/header.png
---

In this post I'll explain briefly how to work with Visual Studio Package Management for npm. I suppose you are familiar with Visual Studio Team Services, NuGet (.NET libraries) and npm (javascript libraries).

While you code your applications, you probably want to share libraries with other teams, in order to reuse code. Also you should supervise dependencies used by your applications, and you can reduce dependencies between them or avoid multiples packages doing the same action.

To solve the first problem, you need to encapsule your code and then you can share that capsule. To solve de second problem, you need under control which dependencies can install the applications

If you are using Visual Studio Team Services you can use ([Package Management feature](https://www.visualstudio.com/en-us/docs/package/overview)) feature to store your packages. It supports two kinds of packages: npm and NuGet. I hope Package Management will support docker images in earlier versions.

Let's go configuring a npm package repo:

Go to Package management feature, and add a new feed:

![New Feed Creation]({{ site.url }}/images/package-management-1.PNG)

Feed creation allows you to configure some options:

- Name and Description for this repository.
- Read permissions to this repository: only team members, or all members in the collection.
- Contribute permissions: who can upload packages to this repository, team members or only project collection build service. This permission try to force the upload of packages from a build process.
- Enabling check 'Include packages from npmjs.org',  uses npmjs.org as a secondary scoped registry. It's interesting when you want to use private packages and public packages from npmjs.org.

Once you have create your repository, you can connect to it:

![Feed Connection]({{ site.url }}/images/package-management-2.PNG)

You can choose whether the access is through NuGet or npm. In this example we choose npm:

- Open a command-line.
- Install the auth helper by running this command: 'npm install -g vsts-npm-auth --registry https://registry.npmjs.com'
- Add your registry manually to your project by creating and .npmrc file at the root project, and adding the following configuration:
			registry=https://enformat.pkgs.visualstudio.com/_packaging/npm-packages/npm/registry
			always-auth=true
![File creation with powershell]({{ site.url }}/images/package-management-3.PNG)

  Note that you can configure the access to this repository to download only release packages, prerelease or both, by adding a parameter:
			registry=https://enformat.pkgs.visualstudio.com/_packaging/npm-packages@Release/npm/registry
			registry=https://enformat.pkgs.visualstudio.com/_packaging/npm-packages@Prerelease/npm/registry

- Store credentials to home folder, by running the following command: 'vsts-npm-auth -config .npmrc'. By running this command, the app asks for the credentials to store in the .npmrc file on your profile folder. In this example, I'm using Windows 10, and file was created to C:\Users\enric\.npmrc.
![Creating credentials to user profile folder]({{ site.url }}/images/package-management-4.PNG)

It's highly recommended to create two files:

- One at the root project that contains the configuration for the whole team.
- Another one to your home profile folder containing the your credentials in a secure mode.

Once we've configured our package with the url and the credentials to access to the feed, we're ready to publish that package. This action is as easy typing command npm publish.

![Publish npm package]({{ site.url }}/images/package-management-5.PNG)

Now your package is ready for being installed to any application.

![Web access view from a published npm package]({{ site.url }}/images/package-management-6.PNG)


Enjoy sharing code from your feeds with your colleagues!
