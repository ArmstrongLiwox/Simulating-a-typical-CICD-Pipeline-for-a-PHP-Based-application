# Simulating a typical CI/CD Pipeline for a PHP Based application.
---

As part of the ongoing infrastructure development with Ansible started from a previous a project, we will create a pipeline that simulates continuous integration and delivery. 

Target end to end CI/CD pipeline is represented by the diagram below. 

![1](images/2.png)

It is important to know that both Tooling and TODO Web Applications are based on an interpreted (scripting) language (PHP). 
It means, it can be deployed directly onto a server and will work without compiling the code to a machine language.

The problem with that approach is, it would be difficult to package and version the software for different releases. 

And so, in this project, we will be using a different approach for releases, rather than downloading directly from git, we will be using Ansible uri module.
---

## Set Up

This project is partly a continuation of our Ansible project, so e will simply add and subtract based on the new setup in this project. 

It will require a lot of servers to simulate all the different environments from ***dev/ci*** all the way to production. 

There will be quite a lot of servers altogether.

But won't create them all at once. Only create servers required for an environment you are working with at the moment.

For example, when doing deployments for development, do not create servers for integration, pentest, or production yet.

We will try to utilize our AWS free tier as much as we can. To minimize the cost of cloud servers, we will not create all the servers at once, we will simply spin up a minimal server set up as you progress through the project implementation and have reached a need for more. 

> Alternatively, we can use Google Cloud (GCP) to rent virtual machines from this cloud service provider - you can get $300 credit here or here (NOTE: Please read instructions carefully to get your credits)  ***NOTE***: All we need here is virtual machines that can be accessed over SSH.
---

## SIT & UAT

* SIT - For System Integration Testing 
* UAT - User Acceptance Testing 

To get started, we will focus on these environments initially.

• Ci 

• Dev

• Pentest

Both SIT and UAT require a lot of extra installation or configuration. They are basically the webservers holding our applications. 

But ***Pentest*** - For Penetration testing is where we will conduct security related tests, so some other tools and specific configurations will be needed. 

In some cases, it will also be used for Performance and Load testing. 

Otherwise, that can also be a separate environment on its own. It all depends on decisions made by the company and the team running the show.

What we want to achieve, is having Nginx to serve as a reverse proxy for our sites and tools. Each environment setup is represented in the below table and diagrams.

![2](images/4.png)

### CI environment

![4](images/5.png)

## Other environments from lower to higher

![3](images/6.png)
