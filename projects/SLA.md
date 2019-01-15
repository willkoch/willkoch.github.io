---
layout: project
type: project
image: images/oath.png
title: Slack SLA Management Reminder Tool
permalink: projects/SLA
# All dates must be YYYY-MM-DD format!
date: 2018-06-01
labels:
  - Google Apps Script
  - Slack
  - SLA
  - ITSM
summary: I created a tool to monitor SLAs for internal communications and notify those required to follow them in Slack.
---

<img class="ui medium right floated rounded image" src="https://www.joetheitguy.com/wp-content/uploads/blog-images/minified/SLA-tips-min.jpg">

My job prior to enrolling in the M.S. program at UH Manoa was that of Incident Management at Oath, a technology company owned by Verizon and comprised of names such as Yahoo, AOL, Huffington Post and more. My job duties fell under the umbrella of IT Service Management, managing user or revenue impacting outages and documenting them, among other things.

Each of these outages, or incidents as we referred to them, had a variety of SLAs that had to be met. SLAs are Service Level Agreements, basically a time guideline that must be followed by a service provider. For us there were SLAs for the time it took to engage engineering, time for them to start triage, time for total resolution, as well as many more. If an action did not take place prior to the time limit for that SLA, it was said to have breached SLA, which we wanted to avoid.

One particular aspect of our job governed by SLAs was sending out internal communications. In particular there was a notification that must be sent out to stakeholders stating that a given incident had breached its ordained "time to resolution." As lower priority incidents  could take days or weeks to resolve, and would change ownership many times as shifts rotated, I found that my team was having difficulty sending out these communications in a timely manner.

Using an API call to Service Now (our ticket tracking software) to pull ongoing incidents into Google Sheets, I was then able to use formulas to derive the exact times of SLA breach. Using Google Apps Scripts, it would check every X minutes for incidents that were close to breaching or had already breached SLA. At that time, a Slack message was sent by the script, utilizing the Slack API, to the incident manager responsible for that incident currently. 

This project ended up a boon for the entire team, decreasing delays in communication dramatically, and it was a great learning opportunity for myself. I tried many things for the first time and experienced a variety of challenges, from proper JSON formatting to making API requests. To date this is the most practical and successful project I have undertaken.
