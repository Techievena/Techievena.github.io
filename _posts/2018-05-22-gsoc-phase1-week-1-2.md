---
layout: post
section-type: post
title: Weight ≠ Mass × Gravity
category: GSoC
tags: [ 'apertium', 'hfst', 'morphology', 'transducer', 'fst', 'gsoc', 'weights' ]
---

[![Weight ≠ Mass × Gravity](http://all-funny.info/wp-content/uploads/2014/06/isaac_newton-steve_jobs.jpg)](https://summerofcode.withgoogle.com/dashboard/timeline/)

---

_"Our life is the sum total of all the decisions we make every day, and those decisions are determined by our priorities."_
― [Myles Munroe](http://www.cbn.com/700club/guests/bios/Myles_Munroe_043012.aspx)

## Introduction

Well you all must be thinking What The F&$k is this blog title? This moron now thinks that he has somehow disproved **THE Newton** and is sitting on his couch blogging instead of claiming the Nobel prize. Then hold on to your brakes guys. This blog is entirely about some different kind of weights, well priorities to be exact; but I needed a fun title to grab you here.

Not every task we perform in a day deserves or gets exactly the same amount of attention from our part. We prioritize our decisions and actions based on our necessities and abilities. Same should be the case with Apertium. All the morphological transductions performed in Apertium must be done based on the priorities. This will make the machine translation process more efficient and humanly. Priorities in Apertium are to be calculated on the basis of the weight values associated with each step of the transduction. Geeky stuff resumes in 1... 2... 3...

## Coding begins!!!

After a month long bonding period, finally the first phase of the coding period for Google Summer of Code 2018 has arrived. All the developers at Apertium recieved a welcome and congratulatory mail from Ilnar Salimzianov a day before the commencement of the period. His welcome note stated all the rules and code of conduct all the student developers must follow for the smooth execution of the GSoC program in Apertium. The mail also listed all the mailing lists all the students must subscribe to stay updated on all the developments and discussions in Apertium. He also asked we continue to interact with each other as we might need each other's help in the completion of our our project.

## Bengaluru is On!!!

[![Bengaluru](https://qz.com/wp-content/uploads/2017/08/bangalore1-reuters-traffic-moves-along-a-road-in-the-southern-indian-city-of-bangalore-december-14-2005.jpg)](https://en.wikipedia.org/wiki/Bangalore)

By this time I have also moved to Bangalore for completing the compulsory 2 credit summer training of my college. Students have come forward to create groups in various social media for interacting and helping other developers with their doubts and queries. People are also planning various social gatherings and organizing meetups to interact with each other and share their experience. It has been a journey pumped with fun and excitement till now.

## Implementation of weights

I continued with the basic implementation of weights in Apertium i.e. ignoring the minimization or determination algorithms part for now. Well the implementation of this feature without breaking the existing code seems to be a task easier said than done. I have to tickle the entire lttoolbox codebase including the tests to get this task done.

As there was no response in the apertium-stuff mailing list to my previous mail for suggestions of syntax for twol rules in lttoolbox, I reported the same to my mentor Tommi. After a discussion, he has asked me to move on and submit a sample syntax for the twol rules and archiphonemes in the monodix files.

[![Apertium stuff Mailing List](/img/post_images/apertium_stuff_rule_syntax.png)](https://sourceforge.net/p/apertium/mailman/apertium-stuff/?page=1)