---
layout: post
section-type: post
title: A community named Apertium
category: GSoC
tags: [ 'apertium', 'hfst', 'morphology', 'transducer', 'fst', 'gsoc' ]
---

[![Community Bonding Period](https://learncodethehardway.org/images/peeps.png)](https://summerofcode.withgoogle.com/dashboard/timeline/)

---

## Community Bonding Period

_"Communication leads to community, that is, to understanding, intimacy and mutual valuing."_  
― [Rollo May](http://webspace.ship.edu/cgboer/may.html)

Now that GSoC projects are already announced, the community bonding period has started in Apertium. Apertium has selected a total of 14 student developers giving them a great opportunity to make the most out of their summers by having a beautiful learning experience while coding for the organisation. The sudents selected in the Apertium organisation are Anna Kondratjeva, Sardana Ivanova, Marc Riera Irigoyen, Nikolay Aleksandrov, Anna Zueva, Memduh Gokirmak, Anastasia Kuznetsova, Vidyadheesha D N, Evgenii Glazunov, Elena Sokur, Arghya Bhattacharya, Kevin Murphy, Claude Balaguer and myself.

[![Organisation Page](/img/post_images/people_selected.png)](https://summerofcode.withgoogle.com/organizations/5779930604896256)

As I had already spent a considerable time communicating with the org members previously and was not new to the organisation, introducing myself to the community part was already done before the commencement of this period. Therefore, I spent most of the community bonding period understanding the codebase of lttoolbox and hfst, in the best possible manner I could. I also fixed a bug in the lexc2dix package, and am working on scraping important information from the comment part in the lexc files to be restored in the dix files.

Also Francis (a.k.a. spectie) has helped me a lot in carving a roadway for the implementation of weights in lttoolbox. He has created two issues on which I am currently working. The first one of them is to have a minimal implementation of weight based analyses in the `att_compiler`, as we do not have to deal with minimization and decomposition algorithms in the att format. I have got to add this important feature without causing any breakage in the existing package. The second of them deals with having an option in lttoolbox for returning the N best analyses based on their weight values, a feature similar to the one already present in hfst.

After discussion with my mentor Tommi (a.k.a. Flammie) regarding the implementation of morphographemics in lttoolbox, I have submitted a post in the apertium-stuff mailing list requesting other developers to help me finalize a syntax for the rule entries in the dix files.

[![Apertium stuff Mailing List](/img/post_images/apertium_stuff_rule_syntax.png)](https://sourceforge.net/p/apertium/mailman/apertium-stuff/?page=1)
