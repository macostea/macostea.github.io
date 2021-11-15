---
layout: post
title: "Docker Desktop Alternative for Mac"
author: "Mihai Costea"
tags: [2021]
category: [tutorial]
---

1. ```$ brew install hyperkit```
2. ```$ brew install minikube```
3. ```$ minikube config set driver hyperkit```
4. ```$ minikube start```
5. ```$ brew install docker```
6. ```$ eval $(minikube -p minikube docker-env)```
7. ```$ docker ps```


Volumes don't work as you might expect (can't easily bind local folders inside containers)
Use minikube ip to get the address of the host.
