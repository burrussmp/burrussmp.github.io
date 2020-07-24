---
date: 2020-03-30
last_modified_at: 
title: "DeepNNCar: A Testbed for Autonomous Algorithms"
header:
  teaser: "/assets/images/DeepNNCar.png"
excerpt: "This is my first blog post on Medium! The goal of this post, and the theme of the blog in general, is to help make technology accessible…"
category:
  - Computer Vision
  - Machine Learning
  - Other
redirect_url: https://medium.com/analytics-vidhya/deepnncar-a-testbed-for-autonomous-algorithms-b0db1ec4770c?source=friends_link&sk=f31dccd91645a467623fce8bd74f2801
---

This is my first blog post on Medium! The goal of this post, and the theme of the blog in general, is to help make technology accessible and interesting. Computer science is everywhere in our lives, yet to many it still remains unapproachable. However, the true fun in computer science isn’t intentionally confusing people with terminology and details, but equipping them with the tools to imagine, explore, and ultimately create. Technology can’t answer every problem in the world, but you might as well give it a good shot.

Like many new things, the hardest part is often getting started. So for the first blog post, I am going back to a project that helped me get started: **DeepNNCar**. By the end of the post, you should have a basic understanding of how to design and drive your own autonomous vehicle which you can train at your house! To help with this, we have also made our [code repository public](https://github.com/scope-lab-vu/deep-nn-car.git).

This project has been supported by DARPA Assured Autonomy Grant and National Science Foundation US Ignite Grant’s REU Supplement. Also, I would like to give a special thanks to Dr. Abhishek Dubey, Shreyas Ramakrishna, Gabor Karsai, Ohad Beck, and the rest of my colleagues at the [SCOPE-lab](https://scope-lab.org/) at Vanderbilt University‘s Institute for Software Integrated Systems who have used DeepNNCar in the following publications:

- [Dynamic-Weighted Simplex Strategy for Learning Enabled Cyber Physical Systems](https://arxiv.org/abs/1902.02432)
- [DeepNNCar: A Testbed for Deploying and Testing Middleware Frameworks for Autonomous Robots](DeepNNCar: A Testbed for Deploying and Testing Middleware Frameworks for Autonomous Robots)

## Section 1. What is DeepNNCar?
DeepNNCar is the combined words of deep neural network car. I designed DeepNNCar during my sophomore year at Vanderbilt’s Institute for Software Integrated Systems (yes ISIS) as part of a research program. In general, **DeepNNCar is just an remote-controlled (RC) car that has been hacked to explore different autonomous algorithms**.

<figure style="display: block;text-align: center;margin:0px;">
  <img style="width:20em;height:auto;" src="https://miro.medium.com/max/700/1*bXw9ZQvjtDLxfpqHr1ThiQ.png"/>
  <figcaption >Figure 1. DeepNNCar Components</figcaption>
</figure>

## Section 2. DeepNNCar: The “Hard” Stuff
If you have no interest in the hardware, feel free to skip this section. This section is to provide a quick overview of the hardware and also a few of the necessary mechanical aspects of DeepNNCar to understand how we can provide steering and acceleration controls to autonomously drive.

### Part 1. Hardware
DeepNNCar is built on the framework of the Traxxas Slash RC vehicle which can actually go faster than 60 mph. So, for a quick disclaimer, if you try this at home, you probably don’t want to go that fast. However, in reality, any RC car will likely ~work~ with this system as they all have similar controls. Voltage requirements may be your only restriction. So for the parts list below, the Traxxas Slash RC is preferred but not required. Furthermore, if you want to swap the computer (I use a Raspberry Pi 3) feel free.

- **RC Vehicle:** Traxxas Slash 2WD 1/10 RC Car (ASIN B07GBR4B66) ($230)
- **Computer:** Raspberry Pi 3 (Model# 4328498196) ($30)
- **Camera:** Generic USB Webcam (30 FPS recommended) ($20)
- **Wires:** Jumper wires (Part# B0040DEI9M) ($8–10 for a pack)
- **Computer Power Source:** Portable Power Charger (20,000 mAh) ($8–10)
- **Storage:** 16 GB Micro SD Card & USB Flash Drive ($30)
- **(Optional) Speed Sensor:** IR Slot-Type Coupler (Part# 723585712433) ($1)
- **(Optional) LIDAR:** Any suitable USB Lidar (ASIN B07L89TT6F) ($150 or greater)

Substituting the Traxxas Slash vehicle with a smaller RC vehicle can easily bring this project just around $100.