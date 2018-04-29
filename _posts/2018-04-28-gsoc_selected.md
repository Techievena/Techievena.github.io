---
layout: post
section-type: post
title: Finally.... GSoC!!!
category: GSoC
tags: [ 'apertium', 'hfst', 'morphology', 'transducer', 'fst' ]
---

[![Google Summer of Code](https://www.opportunitiesforafricans.com/wp-content/uploads/2018/03/google-summer-of-code-2018-696x414.png)](https://summerofcode.withgoogle.com/)

---

## Apertium

_"There are at least two other more serious problems for endangered languages, more acute than just lack of mother-tongue transmission. There are languages whose last fluent speakers are already gone or are about to go. At a meeting at Glorieta near Santa Fe, New Mexico, a few months ago, we had actually the last living speaker of one of the languages come. It was a very sad experience for everyone, not just for that woman. And perhaps the saddest thing is that she cannot even talk to her sister anymore, who was the next-to-last speaker before she recently died. She can not call up anybody. The only person for her to talk to is a linguist and that is no fun."_ ― [Source](http://www.ncela.gwu.edu/pubs/stabilize/conclusion.htm)

The above quote very well describes the importance of machine based language translation in today's world. Well I could go on and on about why it is, but this post is not about that.

## How I all started

Well this journey started about an year ago when I was working with coala organisation. While I was working on an issue of developing the [ApertiumlintBear](https://github.com/coala/coala-bears/tree/master/bears/apertium) for the use of coala, the name of the configuration file was hard-coded in apertium-lint which therefore needed a few modifications in the linter itself, to support a general configuration file. For solving that issue, Kevin Brubeck Unhammer became my first point of contact in Apertium. I had a few mail exchanges with him until the issue was resolved completely and we released a new version of apertium-lint. Unfortunately I couldn't qualify GSoC that year but was selected as a mentor for **Google Code-in 2017** for coala during which I contacted Kevin for suggesting me a project to work on for which I can submit a proposal for Google Summer of Code 2018. He provided me few links which were very helpful in understanding the working of Finite State Transducers.

## Extend lttoolbox to have the power of HFST

The aim of this project is to implement the support for morphographemics and weights in the lttoolbox transducer. The proposal focuses on extending lttoolbox to perform the complex morphological transformations and weight based analyses currently done in HFST and writing a module that translates the current HFST format to the new lttoolbox format.  

This idea looked quite fascinating to me for which I submitted a proposal for this idea, which eventually got accepted in **Google Summer of Code 2018**.  

## What to do next?

Getting selected in GSoC is like a dream come true opportunity for me. I am looking forward to a very exciting and productive summer this year. Under the guidance of my mentor Tommi Pirinen, I will put my best effort to produce a solid proof of concept that will be helpful to the community and to the users of Apertium.  

I will be posting the weekly updates of my progress here. So, stay tuned!! :smile:
