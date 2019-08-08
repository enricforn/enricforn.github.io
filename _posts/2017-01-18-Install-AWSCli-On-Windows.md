---
layout: post
title: Install AWSCli on windows 
categories: [AWS]
tags: [AWS,AWSCli]
image: /images/posts/aws-cli-win/header.png
---

### This post describe how to install AWSCli on windows, and how to solve encountered issues

Amazon Web Services is a great cloud environment. Personnally I'm using its S3 service ([Simple Storage Service](https://docs.aws.amazon.com/AmazonS3/latest/dev/Welcome.html)) to backup all my information. It's really cheap and easy to access.

I use [AWSCli](https://aws.amazon.com/es/cli/) to interact with amazon web services. Most of actions you can do with their web console, can also be run from awscli.

I just downloaded the application and installed it. Apparently is very easy, the install application is an easy wizard. After that, I opened a powershell console and configure a default credentials to access to my AWS account:

- Open powershell console (powershell.exe).
- Run command 'aws configure'. This command ask you credentials to access to AWS: 
	- Access Key Id: This key
	- Secret Access Key: Key showed only when you create the user.
	- Default Region: in my case eu-west-1
	- Default output format: I chose json

It seems everything works fine, but when I ran the next command (aws s3 cp s://mybucket D:\data\mybucket.) the following error appears:

C:\Program Files\Amazon\AWSCLI\.\dateutil\parser.py:336: UnicodeWarning: Unicode  equal comparison failed to convert both arguments to Unicode - interpreting them as being unequal

This is an error with python 2.7.9 version, which was solved in earlier versions of python. And this is the python version that awscli installs to run properly.

You can run command 'aws --version' to know which version of python is using your installed awscli:

PS C:\Users\enric> aws --version
aws-cli/1.11.38 Python/2.7.9 Windows/10 botocore/1.5.1

Trying to solve this issue, I started to find a solution in google. And I found an opened issue in [github awscli](https://github.com/aws/aws-cli/issues/424). I hope AWS guys will solve it in the next version :). There I found the workaround to solve this issue:

- Uninstall AWSCli from my machine.
- Install the latest version of python.
- Install awscli from python 3 installer: open a powershell console. Run commmand 'pip install awscli'.

Now, the awscli installed on my machine, is using a newer version of python and works fine:

PS C:\Users\enric> aws --version
aws-cli/1.11.38 Python/3.6.0 Windows/10 botocore/1.5.1


If you encounter the same issue, hope this helps.