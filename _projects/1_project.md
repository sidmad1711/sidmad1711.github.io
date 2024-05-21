---
layout: page
title: Network Instrusion Detection System
description: Detected and logged malicious executable files flowing through the network
img: #assets/img/12.jpg
importance: 1
category: Network Defense
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
7. The LKM logs any potentially malicious system calls made by the executable to a separate log file _/var/log/ids_alerts.log_ using the rsyslog daemon.
8. The NIDS is extended to analyze the logged system calls and classify the executable as malicious or benign. Benign executables can then be transferred back to 'vicky', while malicious ones are dropped.

## Summary

The project covers various aspects of setting up a NIDS, including configuring FTP servers, writing Snort rules, automating file transfers, hooking system calls using an LKM, and configuring the rsyslog daemon for logging. It involves scripting, kernel programming, and configuring various security tools to build a comprehensive NIDS capable of detecting and analyzing potentially malicious network traffic.