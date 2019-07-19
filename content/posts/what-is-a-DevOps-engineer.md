---
title: "What is a DevOps Engineer & How Do I Become One"
date: 2019-06-14T10:14:59-07:00
draft: true
---

Most people in the technology field has heard the word DevOps before, but base on my observations of how people describe it there seems to be a lot of confusion around what it actually is. If you ask a developer they will say an Ops guy and if you ask an Ops person they will say an automation person. Based on these vague descriptions no one really comes close to describing DevOps.

## So what is DevOps?

Doing a search online for the phrase “what is DevOps” yields some pretty interesting results, most of which don’t even come close to what DevOps really is. If anything you will become more confused on what DevOps actually is. The definition I find the most succinct is from Wikipedia
> DevOps (a clipped compound of “development” and “operations”) is a software development methodology that combines software
> development (Dev) with information technology operations (Ops). The goal of DevOps is to shorten the systems development life cycle
> while delivering features, fixes, and updates frequently in close alignment with business objectives.

The second sentence is the key and describes in very few words that DevOps is a “Goal”. So now that we understand that DevOps is a goal we can define what a DevOps engineer does and how to work on becoming one.

## So what is a DevOps Engineer?

In very simple terms, a DevOps engineer is a person that aligns with the goal of DevOps. An engineer in the practice will wield skills and technology to help an organization shorten the systems development life cycle. The DevOps engineer is typically a person with a background in development who has honed their skills in operations or an operations engineer (SysAdmin) who has honed skills in development. There is a debate on if there really is such a thing as a DevOps engineer and in my opinion, there is such a thing. Plus, a quick job search on any of the major job boards will list a plethora of jobs for DevOps, which only means that market demand truly defines whether DevOps is real or not. From an organizational level, there can be goals and philosophies, but if you don’t have champions and practitioners, the goal of DevOps quickly becomes just a dream.

## What skills are needed for a DevOps Engineer?

Regardless of the definition of DevOps or what the definition of a DevOps engineer is we have to look at market demand to define the skills that are necessary to enter or excel within the field. So I don’t simply make this stuff up I decided to do some analysis with job postings for DevOps on Dice. I chose Dice because it was easy to web scrape and similar to all the other job boards in terms of postings. Click here for GitHub gist of the crude web scraper I used. As for the analysis I used a text output of the scraper and found an online word frequency analysis tool. Normally I use python nltk, but I recently upgraded my MacBook and broke some of the python libraries I normally use. Here is a condensed version of the word analysis for approximately 64 job descriptions.

Based on the word analysis the top 5 highest frequency of 2-word phrases are **devops engineer, best practices, configuration management, release management, experience working**. This is somewhat interesting as we can discern two basic categories. Best practice and working experience go hand in hand, while configuration management and release management are closely related. Typically, configuration management in the context of DevOps means the configuration of servers and systems, while release management is the deployment of software on to those servers and systems.

The top 5 word-frequency for single word count has a similar theme to the 2-word phrases. The top words are **experience, management, infrastructure, release, and development**. Experience, management, and release seem to be important for DevOps candidates.

## Top Tools and Technologies

* 38 AWS
* 26 Scripting
* 24 Monitoring
* 24 Linux
* 22 Chef
* 22 Kubernetes
* 20 Python
* 18 Azure
* 18 Terraform
* 18 Puppet
* 18 Windows
* 16 CI/CD
* 16 Java
* 16 Jenkins
* 14 Ansible
* 10 Go
* 10 Docker
* 8 Powershell

## Top Skills

* 94 Management
* 82 development
* 68 Cloud
* 44 Automation
* 22 Test
* 22 Deploy
* 20 Communication
* 18 Integration

## How do I get a job as a DevOps Engineer?

I would personally focus on learning the first few tools and technologies then start making your way down the stack. Because the top ones appear more often in job postings they are going to be the most important to hiring managers. You will want to group certain skills as they have overlap or even potential competing solutions in solving the same problem. As an example AWS and Azure fill the same need. No need to learn both, unless you have time, but if frequency is any indication of demand AWS is what I would learn first as it is in higher demand.

The lists above also provide insights into the hot areas of the field. Scripting, monitoring, Linux, Chef, Kubernetes, and Python all relate to the top skills as they are top tools or areas for development, cloud, automation, test, and deployments. In terms of honing top skills spend time reading about management of large infrastructures, the development process, and automating the release process.

Experience is the best way to gain a lot of these skills and if you are already in an IT related field gaining these skills can already be in your grasp. Remember that DevOps is a goal so if your management desktop systems, as an example, try using a tool such as Chef/Puppet/Ansible to orchestrate the management of those desktops. Even better, convince your manager to let you install the server for tooling on AWS or Azure. This way you can pick up experience with a cloud service and an orchestration tool at the same time.

For those trying to break into the field from a non-IT role will find it difficult, but still not impossible. The difficulty will come as you will need to spend non-working hours trying to gain the skills and experience necessary to break into the field. If you really want in, don’t give up. Find opportunities by helping a small opensource project. Even small projects need help with CI/CD and who can refuse a volunteer.

As a final mention, there are implied skills and technology that everyone in DevOps should know. Take the opportunity to work on these skills and become proficient at it. Learn and become proficient in Git (GitHub), development IDE (VSCode), your desktop OS (Mac, Windows), and an analysis tool such as Excel, but bonus points for using tools such as Tableau or Qlik . Hit me up if you have an earnest desire to break into DevOps and need a few more tips and helpful suggestions. You never know, I might be interested in mentoring you 🙂

I hope you have found this post interesting and informative. Please feel free to leave comments or constructive criticism to help make these posts useful and better.
