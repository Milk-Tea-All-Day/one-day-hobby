---
title: Enter the Umami
date: 2025-01-04 18:25:58
tags: [umami, raspberry pi, web-dev, analytics]
categories:
- [hardware]
- [web-dev, analytics]
---

Ok, got more things going today. I received my Amazon orders last night and just had to wait to finish work today before diving in. As soon as I wrapped up, I switched over and started setting things up.

![Amazon Order](images/25-01-04/amazon-order.jpg)

# Choosing an Analytics Tool
I spent a little time investigating another analytics option a friend from FL shared with me, [GoatCounter](https://goatcounter.com/). I like the ethos of it, but I’m trying to kill two birds with one stone here:
1. Find something useful for me that’s not overwhelming.
2. Have something I could recommend for simple analytics needs at work (since GA is no longer really working for them).

GoatCounter works great for the first goal, but not the second. So, **Umami** it is.

# Setting Up the Raspberry Pi 5
## First Steps with DietPi
I grabbed **DietPi** and got started. This time around, the Pi seemed to crash a lot. With my RPi4 Model B, I could plug it into pretty much any USB-C power source, and it ran fine. I tried the same with the new Pi, but it would inevitably crash after a while. Eventually, I plugged it into a USB-C port that powers my laptop, and it’s been more stable there. Seems like the RPi5 is more sensitive to its power needs? 🤷‍♂️

![The RPi5 Sitting on My Tower](images/25-01-04/rpi5-setup.JPG)

![DietPi Login Screen](images/25-01-04/diet-pi-installed.png)

![Such a mess!](images/25-01-04/chaos-desk.jpg)

## Temperature Observations
The RPi5 also runs hotter in general:
* RPi5: 54–64°C
* RPi4: 34–44°C

It says it’s in the OK range, but I’ll watch that for a while to see if active cooling might be necessary.

# Installing Umami
Getting Umami installed wasn’t too bad. I opted for a manual installation instead of Docker. Here’s what I did:
* Installed PostgreSQL and Node.js.
* Followed the installation steps.
* Ran into some annoyances trying to run everything under my user account. Eventually realized I needed to run things as `sudo` through `pm2`. 🤦‍♂️

The Umami server is now running on my new Pi, not exposed to the world. My web server proxies over to it through the local network, so the web server is the only thing directly accessible, with very specific and limited ports.

# Testing the Setup
I installed the analytics tracker on two of my sites (both on the same domain), and it’s working! I even tested by popping my phone off Wi-Fi, and sure enough, it detected a new user and tracked the pages. Once it was all configured, it was really simple.

![Stats!](images/25-01-04/umami-odh-dashboard.png)

# Wrapping Things Up
Got everything packaged into the vertical stack mount I picked up for the Pis. It can fit four more Pis if I ever want to expand, but I’d need to figure out a better way to power them all first.

![Getting them stacked](images/25-01-04/stack-assembly.JPG)

![The final stack (needs shorter cables!)](images/25-01-04/assembled-stack.JPG)