---
layout: page
title: Network Instrusion Detection System
description: Detected and logged malicious executable files flowing through the network
img: #assets/img/12.jpg
importance: 1
category: Cybersecurity
# related_publications: true
---

## Objective
The objective of this project is to develop a network-based intrusion detection system (NIDS) that can detect and analyze potentially malicious executables being transferred over a network. The project involves setting up three virtual machines (VMs) - 'mal', 'vicky', and 'sandy' - and automating the process of detecting, transferring, and analyzing executable files across these VMs.

## Working

1. The 'mal' VM acts as the malicious host, sending executable files to the 'vicky' VM over FTP.
2. The 'vicky' VM acts as the victim host, receiving the executables from 'mal'. A Snort rule is configured on 'vicky' to detect and log any incoming executable files.
3. An automated script runs on 'vicky' to continuously monitor the Snort log files. Whenever a new log file is created (indicating a received executable), the script transfers the log file to the 'sandy' VM over FTP.
4. The 'sandy' VM acts as the sandbox environment for analyzing the received executables
5. A Linux kernel module (LKM) with system call hooking capabilities is loaded on 'sandy' to monitor and log any potentially malicious system calls made by the executable.
6. An automation script runs on 'sandy' to extract the executable from the received log file and execute it within the sandbox environment, with the LKM loaded to monitor its behavior.
7. The LKM logs any potentially malicious system calls made by the executable to a separate log file _(/var/log/ids_alerts.log)_ using the rsyslog daemon.
8. The NIDS is extended to analyze the logged system calls and classify the executable as malicious or benign. Benign executables can then be transferred back to 'vicky', while malicious ones are dropped.

## Summary

The project covers various aspects of setting up a NIDS, including configuring FTP servers, writing Snort rules, automating file transfers, hooking system calls using an LKM, and configuring the rsyslog daemon for logging. It involves scripting, kernel programming, and configuring various security tools to build a comprehensive NIDS capable of detecting and analyzing potentially malicious network traffic.

<!-- Every project has a beautiful feature showcase page.
It's easy to include images in a flexible 3-column grid format.
Make your photos 1/3, 2/3, or full width.

To give your project a background in the portfolio page, just add the img tag to the front matter like so:

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/1.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/3.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/5.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Caption photos easily. On the left, a road goes through a tunnel. Middle, leaves artistically fall in a hipster photoshoot. Right, in another hipster photoshoot, a lumberjack grasps a handful of pine needles.
</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/5.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    This image can also have a caption. It's like magic.
</div>

You can also put regular text between your rows of images, even citations {% cite einstein1950meaning %}.
Say you wanted to write a bit about your project before you posted the rest of the images.
You describe how you toiled, sweated, _bled_ for your project, and then... you reveal its glory in the next row of images.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/6.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/11.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    You can also have artistically styled 2/3 + 1/3 images, like these.
</div>

The code is simple.
Just wrap your images with `<div class="col-sm">` and place them inside `<div class="row">` (read more about the <a href="https://getbootstrap.com/docs/4.4/layout/grid/">Bootstrap Grid</a> system).
To make images responsive, add `img-fluid` class to each; for rounded corners and shadows use `rounded` and `z-depth-1` classes.
Here's the code for the last row of images above:

{% raw %}

```html
<div class="row justify-content-sm-center">
  <div class="col-sm-8 mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/6.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
  </div>
  <div class="col-sm-4 mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/11.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
```

{% endraw %} -->
