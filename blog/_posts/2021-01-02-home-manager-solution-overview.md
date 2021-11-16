---
layout: post
title: "DIY Smart Home - Solution Overview"
author: "Mihai Costea"
tags: [2021]
category: [smart-home]
---

***

In [part one]({% post_url /blog/2020-12-27-diy-smart-home %}) I've described the goals of "Home Manager". Now, let's see how it works.

# Components
![](/assets/img/home-manager-high-level.png)

Being a "smart home" solution, we need to get data from the user and from sensors and control devices, all without using too much power since we'll be using a bunch of small electronics.

## Storage
The storage solution I chose was Timescale DB. Timescale is a PostgreSQL extension for storing and querying time-series data. And because it's basically PostgreSQL, you can use all the advanced software that works with it without too much fuss and you don't need a separate DB to store other application data like sensor types, homes, rooms, etc. If you're working with microservices, you'd probably cringe right now but let's add complexity when we need to :)

## Business logic
Sensor Service and Sensor Listener are the 2 services that make up the application business logic.

**Sensor Service** is the main service that handles data access and also exposes this data through a REST API.

**Sensor Listener** handles communication with sensors and devices through the Message Queue broker and also exposes its own REST API to interface with Sensor Service. This service is not currently exposed externally.

## Sensors and devices
Communication with devices is done via a message broker (RabbitMQ at this time). Sensor Listener uses AMQP for communication while external devices, which are lower powered and have less compute power, use MQTT which is pretty much a standard for IoT devices that use WiFi connections.

Why WiFi? Short answer: because devices are cheap and easily available. The sensors I built are based on a NodeMCU v2 clone (ESP8266) which costs around 8EUR and comes with an onboard WiFi chip.

## User interface
The UI is at this time still under construction without a final solution in place yet. What I do know is that I want this to be available on the Web but also run smoothly on a Raspberry Pi 4 with a 7" touchscreen.

There have been multiple attempts to write this component. I tried a React app, a native Windows 10 IoT (UWP) app and now I'm trying out a Blazor-based solution which seems like a pretty good fit. Time will tell if this will be the winner.
