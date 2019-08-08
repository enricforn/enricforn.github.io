---
layout: post
title: 5 Lessons learned from devops journey
categories: [DevOps]
tags: [development, software, devops]
author: eforn
image: /images/posts/lessons-learned-devops/header.jpg
---

### In this post I write about five points I consider core to successfully adopt DevOps. I highly recommend you to follow these 5 core points if you want to move an organization towards a DevOps transformation.

Over the past ten years I've been guided on my DevOps journey by the aim to improve development cycle of the products I've been working on, and the desire of continuous learning.

DevOps technics and patterns are widely explained in many posts, books and podcasts. In this post I share five most important lessons learned in my DevOps journey.

## 1. Measure your development processes

Eficiency and removing waste are two main objective key results that you should pursue in your DevOps journey. If you want to improve your software delivery performance, it's important to drive your actions based on emphirical information. You should be able to measure the following metrics:

   **- Lead time for changes**: many companies are efficient on using their resources, but their pace is too low. This indicator gives you information on how fast you can bring new business requirements to production environment, and can help you to balance resource usage and flow.

   **- Deployment frequency**: this indicator it's highly correlater with batch sizes of your projects. As soon as you reduce batch sizing, it's less complex deploy applications in production environment, and therefore, you will be able to deploy more frequently.

   **- Mean time to restore service**: this measure captures the average time needed to recover your service from an incident like unplanned outage. This  time includes not only the time spent until you recover customer's service, but also time spent to figure out the root cause and fix it in the production environment.

By collecting all this information from these indicators you are assessing which is your starting point. At this time, you can address objective conversations based on these data, and allows you to create the first backlog to improve your system. While monitoring these indicators, you will be able to check if your system is improved or not, in each changes delivered to your applications, tools or processes.

## 2. Show business value to managers

Regardless the size of the organization, you'll need investment to improve your toolchain, refactor applications, update processes or teach your employees. It's really important to map your efforts to monetization, in terms of improvement.

By improving key performance indicators listed in point 1, first beneficiary is business in terms of:

- If you improve your lead time, business will be able to deliver products to customers more quickly, and so your company will obtain profit with these products faster too.

- By improving your frequency in deployment, this means your business will be able to deliver more frequently value to customers. Thus these customers will get more new features more frequently too.

- If you improve your mean time to recover service, you can traduce it to better service given to customers.

## 3. Focus on a Learning culture in your organization

Work on culture's organization is one of the most difficult challenges to be addressed. DevOps is an enabler that allows your company to walk to a learning and innovation culture.

DevOps technics and practices are focused on improve speed, availability and cost reduction, and it's necessary that everyone should be able to learn new approaches on how apply new technics, and experiment in their daily work. Create an innovation mindset, move people to continuously learn and be more open to change. When people embrace creativity, they are able to deliver smarter solutions for your business.

At this point, when I work on improve a culture's organization, I focus the efforts on try to figure out which kind of context allows the creation of high-performance teams, and I found these three points:

**Build a safety environment** where everyone is comfortable to work together. All members in your team has skills to succeed delivering the product. One of the most difficult task create de context to motivate them. Use belonging cues every day (morning coffee) or weekly (breakfast on friday)  to include people in the team. The most awful part is when a person do not want to stay in a team working on a product, but they don't want to leave, you must pick up trash and remove bad apples, and it's not an easy task.

**Share vulnerability** by creating spaces where you can talk on what you've done, and also discuss which actions the team want to take, in order to improve or change. Take out people from their confort zone at first is awkward, but has positive results. You can organize retrospective with teams, after the delivery of a feature in your product.

**Establish purpose** which guide outputs aligned to outcomes defined by business, through your products. This strategy enables alignment in the entire organization.

## 4. Achieve big through small

It's very difficult to transform an organitzation in a short term. People need to learn step by step how to use new techniques and tools, and change their behaviors.

Innovation Curve of Rogers classify adopters and innovators into various categories, based on the idea that some people are more open to adapt to changes:

![Rogers adoption/innovation ]({{ site.baseurl }}/images/posts/lessons-learned-devops/rogers-innovation-curve.png "Rogers adoption/innovation curve")

Innovation teams probably are the ones who are leading the DevOps transformation in your organization.

I should propose you to identify the early adopters teams in your organization to start your DevOps transformation. Check your model with early adopters teams and refine it.  Collect KPIs before and after the adoption, and then extract metrics from your measurements. You should visualize the improvements as the teams are more comfortable and more productive while using devops toolchain. Overcommunicate all these results to the entire organization, and then expand that devops model step by step throughout your company. 

## 5. Your DevOps journey never ends

Yes, once you've started your DevOps journey it will never ends. Capabilities, processes and behaviours of teams, will probably change, and you technics, practices and platforms must also change. I've been observing these kind of situations, and the reasons are:
 + New languages used by development team which are not supported by your pipeline.
 + New kinds of infrastructure where you want to deploy artifacts that you doesn't support either.
 + The level of delegation you give to team for being more autonomous on doing some tasks (customize builds, quality parameter configuration, integration between requirements and development tools, ...)
 + Observing the system and learning how to improve it.
 + Receiving feedback from users regarding to paint point they have during the process.
 + Stay tuned on what's going on the community: many people innovate an try new tools and techniques. You can watch webinars and read many interesting books explaining deeply these techniques and succeeded use cases. Each organization adopt DevOps model through their own way, there's no a road to follow. I should recommend to read these interesting books:
   - Gene Kim, Patrick Debois, John Willis, Jez Humble, John Allspaw: **The DevOps Handbook**: How to Create World-Class Agility, Reliability, and Security in Technology Organizations Paperback – 2016
   - Nicole Forsgren, Jez Humble, Gene Kim: **Accelerate**: The Science of Lean Software and DevOps: Building and Scaling High Performing Technology Organizations Paperback – March , 2018
   - Daniel Coyle: **The Culture Code**: The Secrets of Highly Successful Groups - 2018
   - Jez Humble, Joanne Molesky, Barry O'Reilly. **Lean Enterprise**: How High Performance Organizations Innovate at Scale Hardcover – 2015