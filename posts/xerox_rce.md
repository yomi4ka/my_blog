---
date: 2025-02-20
layout: post
title: Inside Xerox WorkCentre: Two Unauthenticated RCEs
---

![Xerox WorkCentre Vulnerability](../static/xerox.png)

## What’s the Tea? 
Okay besties, imagine your office printer just sitting there, looking all innocent… but plot twist: it’s totally vulnerable to hackers. Yeah, you heard me right. Security researchers just found **two unauthenticated Remote Code Execution (RCE) vulnerabilities** in **Xerox WorkCentre** printers. Basically, someone could just waltz in and take over your printer—no password needed. That is *not* the kind of open access we like!

## The Vulnerabilities: What Went Wrong? 

### 1. The `configrui.php` Drama
- **The Issue?** This little PHP file doesn’t check inputs properly, so hackers can sneak in malicious commands. 
- **How?** They just send a **crafted HTTP POST request** to `/support/remoteUI/configrui.php` and boom—instant printer takeover. Like, seriously? No validation at all? 

### 2. Preprocessor Directive Injection—Messy!
- **The Issue?** Some PHP files in the firmware handle preprocessor directives like a bad relationship: *no boundaries*.
- **How?** Hackers send a sneaky request, and before the script even fully loads, **their commands are already running**. That’s like handing over your phone unlocked and hoping for the best. 

## Why You Should Care 
- **Who’s at risk?** Anyone with a Xerox WorkCentre that hasn’t been updated since, like, 2016. Yikes.
- **How bad is it?** **Super bad.** Hackers can:
  - Fully control the printer.
  - Snatch up sensitive scanned docs.
  - Use the printer as a launching pad to hack other devices. 

## How to Keep Your Printer Secure & Cute 
- **Update Firmware** – Like, *immediately*. Don’t be that person who ignores updates. 
- **Restrict Access** – Only let the *right* people reach the printer’s web interface.
- **Monitor Traffic** – Keep an eye on logs, just like you keep an eye on your DMs. 
- **Segment Your Network** – Don’t let your printer chill on the same network as your *actually* important systems. 

## Final Thoughts 
Printers aren’t just paper-spewing dinosaurs anymore—they’re fully networked computers, and they **need real security**. If your office has a Xerox WorkCentre, fix this mess now before some hacker decides to have fun at your expense.

---

*References:*  
- [Raphaël Rigo, 2020](https://airbus-seclab.github.io/xerox/INFILTRATE2020-RIGO-Xerox-final.pdf)
