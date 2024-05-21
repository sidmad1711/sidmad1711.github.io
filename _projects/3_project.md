---
layout: page
title: Ad Blockers and Online Privacy
description: Evaluating the effectiveness of different ad blockers using OpenWPM
img: assets/img/ad_blocker.jpeg
# redirect: https://unsplash.com
importance: 3
category: Cybersecurity
---

## Objective

The main objective of this project is to perform a comprehensive evaluation of the effectiveness of several popular ad blockers in mitigating various online tracking mechanisms employed by websites and third-party entities. The study utilizes the [OpenWPM](https://github.com/openwpm/OpenWPM) platform to conduct large-scale measurements across a diverse set of website categories.

## Methodology and Analysis

1. **Data Collection**: The study examines five categories of websites: Entertainment, Gaming, E-commerce, Sports, and the Tranco list (a curated list of top websites). For each category, the top 300 most visited websites are crawled using OpenWPM in two modes: a "vanilla" mode without any ad blocker and multiple "non-vanilla" modes, each with a specific ad blocker enabled (uBlock Origin, Privacy Badger, Ghostery, and AdLock).
2. **Browser Automation**: OpenWPM automates the browsing process using Selenium, interacting with Firefox browser instances. Separate browser profiles are created for each crawling mode to ensure isolation and prevent interference between configurations.
3. **Data Extraction**: The crawling process generates SQLite databases containing browsing data, including HTTP requests, JavaScript executions, and cookie management. Custom Python scripts are used to extract and analyze relevant tracking vectors from these databases, such as third-party cookies, HTTP requests, and JavaScript API calls.
4. __Effectiveness Evaluation__: The study quantifies the effectiveness of each ad blocker by comparing the number of distinct third-party domains identified during the "vanilla" mode crawls (without ad blockers) to those observed in the respective "ad blocker" mode crawls. A significant reduction in the number of third-party domains indicates stronger protection against online tracking.
5. **Analysis and Observations**: The study analyzes the collected data to evaluate the relative performance of each ad blocker across the three tracking vectors (cookies, HTTP requests, and JavaScript API calls) and across different website categories. It also identifies the top third-party domains commonly used for tracking purposes.

## Summary

The paper aims to provide insights into the current state of online tracking mechanisms and the relative effectiveness of popular ad blockers in mitigating these threats. By quantifying the strengths and limitations of these tools, this study highlights gaps in existing privacy protections and provides actionable recommendations for enhancing user privacy defenses, guiding tool developers, and informing policymakers on addressing invasive online tracking practices.

Link to the [paper](https://sidmad1711.github.io/assets/pdf/Ad_blocker.pdf).