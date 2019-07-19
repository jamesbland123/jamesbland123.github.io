---
title: "Docker: The Ideal Tools Container"
date: 2019-06-28T10:26:35-07:00
draft: true
---
Besides the obvious use as a container for an application, docker works really well as a tools container that can be shared with developers, DevOps engineers, and operations folks.  Just recently I was trying to share a bash wrapper script that I use to execute terraform with a windows developer and this effort quickly became an exercise in futility.

I didn’t have a lot of time so I told the developer to try Cygwin and see if it worked.  I’ve used Cygwin in the past with mixed results and in most cases, it works well until it doesn’t.  In this particular case, it didn’t work and I didn’t want to spend a lot of time on a solution I don’t care much for.  I decided the best approach was to build a tools container.  Basically, everything needed to successfully run all the terraform, packer, make, etc…

### Dockerfile:
```
## Dockerfile
FROM python:3.6.7-alpine3.8

RUN apk update && apk add wget zip bash make nano

RUN pip install --upgrade awscli

RUN wget -nv https://releases.hashicorp.com/terraform/0.11.10/terraform_0.11.10_linux_amd64.zip \
&& unzip terraform_0.11.10_linux_amd64.zip \
&& mv terraform /usr/local/bin/terraform \
&& rm terraform_0.11.10_linux_amd64.zip

RUN wget -nv https://releases.hashicorp.com/packer/1.3.2/packer_1.3.2_linux_amd64.zip \
&& unzip packer_1.3.2_linux_amd64.zip \
&& mv packer /usr/local/bin/packer \
&& rm packer_1.3.2_linux_amd64.zip

WORKDIR /my-repo

CMD ["/bin/bash"]
```

I start with the python:3.x.x alpine image and use apk to add in a few things I need.  Alpine maintains small images which is why I need to add in wget and bash, which tends to be in most builds.  Next I install aws cli, terraform, and packer.  The image defaults to start in /bin/bash, but it really doesn’t matter as this is started from docker run.

### Run docker build:
```
$ docker build -t tools .
```
Here we build the docker file and name the image tools.  Don’t forget the “.” on the end.

### Docker run:
```
$ docker run --rm -it -v ${PWD}:/my-repo -v \
~/.aws:/root/.aws tools /bin/bash
```

With this we run the docker image we built earlier and mount the current directory to /my-repo and mount your aws credentials and profile to be available in the running container.  The mounts assume your Dockerfile and repo are part of your current directory.

### A Note for windows users:

You will not be able to use the docker run as mentioned above.  Replace the ${PWD} and ~/.aws with absolute paths such as C:\windows\users\me\my-repo.  Don’t worry about the C: and :/my-repo, two “:”.  Docker knows you are on a windows machine and figures it out.

The other thing for windows users with git repos.  You will need to set your line endings otherwise bash scripts shared from your repo into the container will not run properly.  In your .gitattributes you will need to set shell line endings.
```
# Force LF line endings for Bash scripts.   
# On Windows, source files will typically 
# have CR+LF endings (Git default on Windows), 
# but Bash scripts need to have LF endings 
*.sh text eol=lf
```

With the above, windows, mac, and linux users can share tools without having to jump through a bunch of hoops and hurdles. Not to mention it should make providing instructions to team members consistent.
