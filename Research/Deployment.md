# Deployment research:

## Content
- Foreword
- Questions:
   - Different ways to deploy an application?
      - Recreate:
      - Ramped:
      - Blue/Green:
      - Canary:
      - Shadow:
- Different deployment infrastructures?
      - Virtual machine:
      - Dedicated machine:
      - Cloud services:
- Best way to deploy a React application?
- Best way to deploy an ASP.NET application?
- Conclusion:
- References:


## Foreword

The reason I've researched this topic is to be able to deploy the application I've made this
semester. The research strategy I used were Library Research and Lab studies. The research method from the framework I use are Literature study and A/B testing. I used these method because there are a lot of good online sources for information. We can use these sources to conduct our research. And to determine which is best for I tried them out and compared them.


## Questions:


- How can I best deploy my CMS application?
   - Different methods to deploy an application?
   - Different deployment infrastructures?
   - Best way to deploy a React application?
   - Best way to deploy an ASP.NET application?


## Different ways to deploy an application?

### Recreate:

First the existing instances will be terminated after which new instances will be created with
the new update.This is used for applications that can afford down time and don’t have any
extra resources.
  <br/>
  <img src="https://github.com/DB-S3/Documentation/blob/main/Images/recreate.gif?raw=true" alt="drawing" width="350"/>

### Ramped:

New instances will slowly be rolled out to replace the old ones.
  <br/>
  <img src="https://github.com/DB-S3/Documentation/blob/main/Images/ramped.gif?raw=true" alt="drawing" width="350"/>

### Blue/Green:

The new instances are created alongside the old ones after which all traffic will be switched
to the new instances. When this new instance is not stable enough the users can always be
diverted back to the old instances. This ensure uptime of an application
  <br/>
  <img src="https://github.com/DB-S3/Documentation/blob/main/Images/blue-green.gif?raw=true" alt="drawing" width="350"/>

### Canary:

A new instance is created alongside the old ones and traffic is slowly diverted to the new
instances. This technique is used when the confidence about the stability is low. The
instances are kept so when the new application doesn’t work as intended the old instance
can be switched back to.
  <br/>
  <img src="https://github.com/DB-S3/Documentation/blob/main/Images/canary.gif?raw=true" alt="drawing" width="350"/>

### Shadow:

With this deployment technique the new instance will be rolled out along the existing one.
Users will use the old instance but the traffic will also be sent to the new instance to test the
new code.
  <br/>
  <img src="https://github.com/DB-S3/Documentation/blob/main/Images/shadow.gif?raw=true" alt="drawing" width="350"/>


## Different deployment infrastructures?

For the deployment infrastructure I had one criteria: the ability to implement continuous
deployment so while there are more options out there a lot of them won’t be able to update
automatically upon a new version of the application.

### Virtual machine:

A virtual machine is a normal computer divided into parts to create multiple servers. This is
great for small applications. Although the vps’s can have limitations.

### Dedicated machine:

A dedicated machine is an entire machine due to which one has full access to the machine.
Due to this freedom, dedicated servers are very expensive.

### Cloud services:

Cloud services people to host applications instead of having to host on servers. This is
usually split into two categories: Serverless hosting and container hosting. The difference
being with serverless the hoster only gets billed when the application is being used and with
container hosting a container is always active resulting in higher costs.


## Best way to deploy a React application?

To deploy the react front end of the application I had two options: hosting the react
application on a VPS using nginx and a docker container or a cloud service. I ended up
choosing a cloud service called netlify. While both options can:
● Host the website.
● Support the ability to continuously update the app.

Netlify excels in certain areas like:
● Netlify has a continuous deployment system using the Blue/Green method meaning
when the main branch on github gets updated netlify will build a new instance and
release it. Unlike the VPS where a system would have to be set up to continuously
update the app.
● Netlify is more scalable due to it being serverless.
● Netlify Has a free tier which allows 7000 visits to the website for free.

## Best way to deploy an ASP.NET application?

For deploying the ASP.NET backend I tested two methods: hosting the ASP.NET application
on a VPS using nginx and a docker container or hosting a container in the cloud. I decided to
use azure due to the free container deployment for students.
The azure cloud due to:
● Automated upscaling.
● Automatic container updating using a Blue/Green meaning that updates will happen
seamlessly without having noticeable impact while using the application.
● Free container deployment for students.


## Conclusion:

To answer the main question “How can I best deploy my CMS application? ” is by using a
Blue/Green deployment method to ensure equal distribution to all users this makes it so no
users are on an old build this can be problematic when a users wants to use a new feature
which isn’t available yet due to not enough new containers having been created.

The infrastructure I will be using to deploy is serverless cloud computing due to the possible
scalability which is something that won’t happen to the application but due to the application
micro service based it is something that should be possible thus I want to implement it.

The service providers i will be using are netlify and azure due to them being free and having
continuous delivery built in according to the Blue/Green method.


## References:

```
Tremel, E. (2021, 25 maart). Six Strategies for ApplicationDeployment. The

New Stack. Geraadpleegd op 8 januari 2022, van

https://thenewstack.io/deployment-strategies/
```
```
Athow, D. (2021, 26 november). What are the differenttypes of web hosting?

TechRadar. Geraadpleegd op 8 januari 2022, van

https://www.techradar.com/web-hosting/what-are-the-different-types-of-web-hosting
```
```
Singh, A. (2020, 10 november). 10 ways to deploy aReact app for free.

LogRocket Blog. Geraadpleegd op 8 januari 2022, van

https://blog.logrocket.com/8-ways-to-deploy-a-react-app-for-free/
```
```
Diagboya, E. (2019, 16 juli). Types of ApplicationDeployment - FAUN

Publication. Medium. Geraadpleegd op 8 januari 2022,van

https://faun.pub/types-of-application-deployment-36772c0adf
```

