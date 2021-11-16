---
layout: post
title: "Docker Desktop Alternative for Mac"
author: "Mihai Costea"
tags: [2021]
category: [tutorial]
---

{:.header}
![](/assets/img/horizontal-logo-monochromatic-white.png)

Docker have [changed their service agreement](https://www.docker.com/blog/updating-product-subscriptions/) effective August 31, 2021, requiring every company with more than 250 employees or more than $10 million in annual revenue to get a paid subscription. There is a grace period until January 31, 2022 after which companies need to have valid licenses to use Docker Desktop.

This should not be a problem for most people but as of the day of publishing this, there is no official alternative to run Docker on a MacOS system. Docker Desktop is the only official way to go.

Fortunately, Docker is still based on a lot of open source code so if you can do without the fancy GUI there is a pretty good alternative out there that gives you a working Docker and Kubernetes environment on your MacOS machine: [minikube](https://minikube.sigs.k8s.io/docs/)!

Here's how you install it:

1. ```bash
$ brew install hyperkit
```
2. ```bash
$ brew install minikube
```
3. ```bash
$ minikube config set driver hyperkit
```
4. ```bash
$ minikube start
```
5. ```bash
$ brew install docker # this is only the Docker CLI, not a full Docker Desktop install
```
6. ```bash
$ eval $(minikube -p minikube docker-env)
```
7. ```bash
$ docker ps
```

You are now running Docker in a linux VM using hyperkit (the virtualization engine behind Docker Desktop) and you get your development single-node Kubernetes cluster together with it.

There are a few caveats to note:
1. Volumes won't work as you might expect: you cannot easily bind a local folder on your machine to a container because the container is running inside an isolated VM. You could tweak the hyperkit config to mount a local disk in the VM but that's an exercise for the reader
2. The containers will not be bound to your host network when you run them. That means that you won't be able to access a container on `http://127.0.0.1:8080`, you'll need to use `$ minikube ip` to get the IP address of the minikube VM and access it using that.

That's it. Enjoy!

