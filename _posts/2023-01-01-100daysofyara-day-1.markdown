---
layout: post
title: "100 Days of YARA - Day 1"
date: 2023-01-01 00:00:00 -0000
categories: yara
---

# 100 Days of YARA
I'm a big fan of [YARA](https://github.com/VirusTotal/yara). It's a tool that makes it possible for anyone interested to write static signatures, whether to classify specific strains of malware, perform broader threat hunting, or even parsing files.

In 2022, [Greg Lesnewich](https://twitter.com/greglesnewich) started #100DaysofYARA; an initiative, similar to #100DaysOfCode, to engage with YARA for the first 100 days of the year. This can either be writing YARA rules, contributing to the source code, creating tools to help automate YARA, or generally learning more about the tool/helping teach others.

Last year, I didn't contribute to the full 100 days, but was inspired by the event to create a module in YARA to parse LNK files: [https://github.com/VirusTotal/yara/pull/1732](https://github.com/VirusTotal/yara/pull/1732)

This year, I'd like to highlight this module and what it's capable of, as well as trying to contribute on as many of the days that I can!

![I love YARA memes](/assets/2023-01-01-always-has-been.jpg)

To start with, I'd always recommend starting by looking through the YARA documentation to see how to write rules. This is a document I spend a lot of time in: [https://yara.readthedocs.io/en/stable/writingrules.html](https://yara.readthedocs.io/en/stable/writingrules.html)

I'd also recommend checking out [Florian Roth's guide for YARA performance](https://github.com/Neo23x0/YARA-Performance-Guidelines), which can give some good insight into why rules like the following are not great:
```
import "math"

rule CPU_Eater {
    meta:
        description = "Please don't actually use this rule, it's realllllly bad"
        
    condition:
        for all j in (0 .. filesize) : (
            for all i in (0 .. j) : (
                math.entropy(i, j) > 0
            )
        )
}
```

And with that terrible rule out of the way, we can start moving on to more useful content from today onwards!