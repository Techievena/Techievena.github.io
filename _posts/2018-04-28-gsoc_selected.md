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

_"There are at least two other more serious problems for endangered languages, more acute than just lack of mother-tongue transmission. There are languages whose last fluent speakers are already gone or are about to go. At a meeting at Glorieta near Santa Fe, New Mexico, a few months ago, we had actually the last living speaker of one of the languages come. It was a very sad experience for everyone, not just for that woman. And perhaps the saddest thing is that she cannot even talk to her sister anymore, who was the next-to-last speaker before she recently died. She can not call up anybody. The only person for her to talk to is a linguist and that is no fun."_

The above quote very well describes the importance of machine based language translation in today's world. Well I could go on and on about why it is, but this post is not about that.

## How I all started

Well this beautiful journey with Apertium started about an year ago when I was working with coala organisation. While I was working on an issue to develop the [ApertiumlintBear](https://github.com/coala/coala-bears/tree/master/bears/apertium) for the purpose of linting monolingual or bilingual dictionaries with the help of coala, there was an issue with the original linter which needed a fix. The name of the configuration file was hard-coded in apertium-lint which therefore needed a few modifications in the linter itself, to support a general configuration file. For solving that issue, Kevin Brubeck Unhammer became my first point of contact in Apertium. I had a few mail exchanges with him until the issue was resolved completely and we released a new version of apertium-lint.  

Unfortunately I couldn't qualify GSoC that year but later was selected as a mentor for **Google Code-in 2017** for coala during the course of which I contacted Kevin for suggesting me a project to work on; for which I can submit a proposal for Google Summer of Code 2018. He provided me few links which were very helpful in understanding the working of Finite State Transducers and get acquainted with the workflow of Apertium.

## Extend lttoolbox to have the power of HFST

The aim of this project is to implement the support for morphographemics and weights in the lttoolbox transducer. The proposal focuses on extending lttoolbox to perform the complex morphological transformations and weight based analyses currently done in HFST and writing a module that translates the current HFST format to the new lttoolbox format.  

This idea looked quite fascinating and intriguing to me for which I submitted a proposal for the implementation of this idea with the help of mentors and experienced developers at Apertium. My proposal eventually got accepted in **Google Summer of Code 2018** and thus I was selected as a GSoC student for Apertium.  

## What do I plan next?

[![Extend lttoolbox to have the power of HFST](/img/post_images/selected.png)](https://summerofcode.withgoogle.com/projects/#4841842567282688)

Getting selected in Google Summer of Code is like a dream come true opportunity for me. I am looking forward to a very exciting and productive summer this year. Under the guidance of my mentor **Tommi Pirinen**, I will put my best effort to produce a solid proof of concept that will be helpful to the community and to the users of Apertium as well.  

[![Project Details](/img/post_images/project_view.png)](https://summerofcode.withgoogle.com/projects/#4841842567282688)

Every fortnight I will be posting the updates of my progress here. So, stay tuned!!! :smile:
