---
title: "How to Fix Release and Deployment Pain"
date: 2019-07-19T09:57:50-07:00
draft: true
---

Regardless of the size of the organization, anyone who has done more than 2 releases or deployments knows about the pains involved. Sometimes the deployment fails right away and you spend hours trying to figure out the problem so you don’t have to roll back. Other times it’s a wakeup call at 2:00 AM to tell you the service is down. Regardless of how it happens, it’s always painful.

## Resist adding more control and process

I was with an organization that was plagued with release issues.  There was hardly a week that went by that didn’t have some sort of outage or user impact.  It seemed like the harder we tried to reduce issues the more likely we were to have them.  The organizational fix/reaction was to add more process and control.

The organization added another layer to the already chaotic change control process for approvals and added two additional meetings per week for change reviews.  With the added process came added paperwork on the order of 4x more forms and a powerpoint deck that had to be prepared for all releases.  To measure success, uptime was used for the new change process.

Initially, this seemed to reduce outages and downtime, but that was only a side effect that releases had pretty much stopped due to the added overhead of the new process.  After a short time of bliss, the outages and release pain actually got worse.  Thinking back on it now, it makes complete sense why things didn't improve.  When the overhead to release or deploy is increased, teams try and stuff more changes into a single release, which ultimately increases the risk and probability of failure.  So no longer did we have several weeks of changes, we had several months of changes in a single release.  Plus the bigger the release the slower the recovery time when problems are encountered.

## Release more often

For the untrained eye or company, one would assume that you simply need more testing or planning. But unfortunately, in most organizations, you can’t mandate quality, quality needs to be engrained in the organizational culture.  The actual solution is to release more often.  This may seem counter-intuitive but it forces a few things to happen that promotes good deployment behavior.

**Releasing more often makes releases faster.**  Uh, wait that sounds like some self-fulfilling mumbo jumbo.  From two of my favorite books, The Goal and The Phoenix Project, reducing batch sizes increase flow.  In The Goal, they are referring to something that is well known in manufacturing processes, which is that smaller batch sizes increase the throughput of the entire production system.  In the context of IT systems increasing the number of releases would naturally mean decreasing the size or complexity of the release, which in turn allows developers, testers, and administrators to work in smaller less complex deployments that are faster. So releasing more often makes releases faster.

**Reducing batch size reduces deployment risk.**  Smaller releases are easier to test and plan for.  Getting test coverage in a release with a single change is much easier for everyone involved in the process than with a release with multiple changes.  Smaller releases are also easier to troubleshoot if something does go wrong.  Ideally, if you have one change in a release, more than likely it was the change that caused the issue.

**Practice makes perfect/permanent.** Just like an athlete who trains for a game its the practice that allows the athlete to perform well in the competition.  Releasing more often gives the team more practice in releasing and the more practice a team gets the better they become.  I’ve worked on teams that released once a quarter and I can tell you that releases were always painful on that team.  I don’t recall a single release on that team where things didn’t go sideways.  Because we also only did releases once a quarter no one wanted to roll back as it would take another 3 months to get in the features that the business was asking for.

## How?

There is no silver bullet.  The most effective way I have found is to simply set a goal and have everyone behind trying to achieve that goal.  I have personally set goals for daily deployments to production and if your a team suffering from a lot of pain during releases this may seem impossible, but it’s achievable.  If you are currently releasing quarterly, try every two weeks, do that for a couple of releases and move it up to weekly and eventually daily.

Trying to release more often will uncover gaps with your release process.  You will need to solve these problems and automate everything you can.  I actually find it fun to prove the naysayers wrong that daily releases are not possible.  To me, large organizations suffer from this as a form of learned helplessness.  You can tell when the reasoning is that “our process” requires change approval, or the change board only meets once a week to approve.  As a realist, it’s not an easy thing to take on and will require working with people that will be skeptical if not downright oppose what you are trying to do.

## Conclusion

Alleviating or eliminating the issues that come with releases and deployments starts by setting a goal to release more often.  You will need to work with everyone in the release workflow and don’t be surprised if you are looked on with a bit of skepticism.  Work tirelessly to reduce the batch size and release more often.  At first, it’s expected that you will struggle, but as the team gains practice and works through the issues each release will become easier and easier.  Eventually, you will reap the rewards of zero pain releases and faster business value to the end user and customer.
