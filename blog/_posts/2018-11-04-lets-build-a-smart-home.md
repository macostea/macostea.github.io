---
layout: post
title: "Let's Build a Smart Home - Intro"
author: "Mihai Costea"
---

We're doing it! Almost everything is connected to the internet nowadays.

TV seems to be the first one to go. Try buying a 4K TV today and see if you can find one that has absolutely NO smart features. It's basically impossible to do that. Features like Wi-fi, Netflix integration or "Smart Remotes" are always listed in the TV's feature list. You can't buy a dumb screen anymore.

That, of course, has pros and cons but we'll focus more on the pros now.

Everything is connected to the internet so now we can make everything aware of everything else. My TV can now be aware that I also have an iPad and smart lights in my house. That means that the integrations between them could lead to amazing results, limited only by our imagination. For example, my TV could learn my viewing habits and by checking if my phone is connected to the local network could turn on by itself and switch to the right channel so I could watch my favourite show.

Well, it's not really like that, is it?

I mean, we have *some* level of integration but it's far from perfect and it requires a whole lot of setup and specific knowledge. I can set up my lights to automatically turn off when everyone is out to save power and I can program them to turn on when the first person arrives and it's dark out. I need a phone (or tablet) to install the smart lights app and go through a complicated setup procedure that will work to some extent but will drain my phone's battery because of the always on location services. Or, I could use the feature built into my phone to do this if I'm lucky enough to have my smart devices compatible with that specific protocol. Even then, at least from my experience, the probability for this kind of setup to work is about 50%. So I might as well just turn off my damn lights manually when I leave and turn them back on when I arrive. So 2018!!!

Looking at the state of IoT devices built for consumer use right now it seems that everyone is trying to build their own thing, their own protocols, their own hubs, their own control devices, etc. This is usually a sign that a technology is only just starting to gain traction and it will take some time until companies join forces to build standard procedures and protocols.

However, I believe that this is only part of the story. I think the real issue here is who controls the **data**. Data has always been super important for businesses, governments, military forces and so on. But nowadays, data is the main driver for many businesses as opposed to being a decision making tool. Data has become the currency in which businesses operate. We sell data to other businesses (advertisers) that will, in turn, sell you stuff. The irony here is that while advertisers have a ton of data to work with, ads are still pretty stupidly targeted. But that's for another time.

Where do I get this idea, you might ask. I have a few smart things in my home: a smart TV, Chromecast, Google Home and a few Philipps Hue lights. I wanted to check if the rumours that these things send data back home is true. So I converted a Raspberry Pi I had lying around into a router. All the network traffic was being router through it so I could check it.

The results were pretty interesting: Apple devices are constantly in touch with the Apple servers (I guess that makes sense since all notifications are pushed through Apple's servers and all the devices in my house have iCloud sync enabled), Google seems to be keeping their promise to only send data when you activate Google Home with the wake-up phrase (I don't know what data it is sending since the connections are encrypted but the timings check out: the connection time and the connection durations look like Google Home is only sending out the data you are giving it as opposed to the popular tinfoil-hat opinion that it's always listening) and the Hue lights are constantly in touch with the servers back home. This last one was quite a shock to me as I cannot, for the life of me, understand why. I know that the Hue Bridge is connected to my network and it could scan for ips and hostnames on the network (you could get quite a lot of info from this) but other than that I don't understand the business value of always sending out the status of my Hue lights. Even when there is no interaction with them. Nevertheless, it felt creepy.

So what are we gonna do about it? We're gonna build our own thing of course :)

Our thing, codename Foxey Lady, will be yet another device connected to your home. But one that will gather the data that is gathered by your devices and sent home without you knowing. And you get to see it, use it and make the integrated home you always wanted.

Excited? I sure am!

Stay tuned for part 2 of this series where we'll talk about the design and the features of Foxey Lady.

