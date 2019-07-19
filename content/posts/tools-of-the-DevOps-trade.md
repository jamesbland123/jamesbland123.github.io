---
title: "Tools of the DevOps Trade - Source Code Control" 
date: 2019-07-05T10:35:01-07:00
draft: true
---

Every trade and profession has its tools, DevOps is no different.  In fact, the number of tools in the DevOps toolchain can be a bit overwhelming.  I will try and break down some of the more popular toolsets and describe where they fit in the DevOps engineer arsenal.  With this post, I will discuss source code control systems (SCCS).

Most people simply think that the only purpose of SCCS is to store source code for a software product that the company works on.  This is definitely one thing that source code control does, but its far from the only thing. In the DevOps toolchain, the SCCS is an integral part and the first major component in the workflow.

Based on experience one of the biggest decisions that need to be made is what SCCS product to use.  I am partial to git based systems and especially Github as it aligns with the fundamental philosophies of DevOps.  Github in particular fosters speed, agility, and communications.  If you don’t have a background with other SCCS you will need to take my word that Github is by far one of the best choices.

I have seen large organizations let antiquated policies dictate the SCCS product and implementation.  This is a bad approach for such a key decision in moving towards DevOps.  It’s like trying to run in a race with your legs tied together.  What I mean by this is that DevOps requires the organization to think differently and if you are going to continue to do what you have always done, why would you expect a different outcome.

SCCS’s are the starting point of the DevOps workflow.  In environments, I have been part of, we check in anything we can to SCCS.  The obvious is source code for software products, but also scripts and configuration should be checked into the SCCS.  Every admin and operations person can attest to changing scripts and configuration on the fly and within a couple of weeks forgot exactly what changed and why.  In large environments, this problem is amplified hundreds of times when you have lots of admins and operations personnel.

A good SCCS also serves as a collaboration tool that can help promote quality in code.  With Github, settings can enforce code reviews with pull requests.  Engineers are only human and enforcing code reviews lead to better quality.  The interface to Github provides a detailed view where reviewers can leave comments and suggestions.  If an SCCS does not support collaboration then it is not a DevOps tool.

What makes SCCS the starting point is that anything that is checked in becomes a trigger for automated building, testing, and deployments.  Which is a major component in the CI/CD pipeline.  The SCCS needs to be well integrated with the rest of the pipeline and should have easy integrations with other vendors.  You will not be able to get away with and SCCS that can run your entire pipeline so you will need integrations with other products and development hooks.

As you can see the SCCS is an important decision and product in the DevOps toolchain.  Whatever tool you choose needs to promote speed, agility, and collaboration.  I’m partial to Github, but that’s because the product is widely used and supported by every other product in the DevOps toolchain.  If for some reason you can’t use Github you might want to try Bitbucket as it is also a great SCCS.  I would personally stay away from roll-your-own and run-your-own type products.  DevOps is about speed and agility, don’t encumber yourself with trying to run and maintain systems.  That time is better spent rolling out new business features.


