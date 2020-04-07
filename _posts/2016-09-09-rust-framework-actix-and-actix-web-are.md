---
title: 'Rust framework actix and actix-web are dead'
date: 2020-01-20T07:53:00+01:00
draft: false
---

![](https://avatars0.githubusercontent.com/u/32776943?s=400&v=4 "actix-web/README.md at master · actix/actix-web · GitHub")  

[](https://github.com/actix/actix-web/blob/master/README.md#actix-project-postmortem)Actix project postmortem
=============================================================================================================

Another day, another "unsafe shitstorm”, I guess I get used to it.

It is interesting how easy to move comment out of context and how hard to comment with very clear intention (especially if you are not native speaker) What was the patch? It was very strait forward, simple, uncreative change, intention was just to remove unsafe not to fix existing code. I believe software development is one of the most creative work we do, and creativity is part of why we love software development, why it is fun. Especially if you combine it with real world projects constraints. “creative constrains” could be source of very interesting solutions. Being on the edge of your abilities is super fun. So uncreative change felt boring (oh! And author gave up copyright claims for that patch (a bit irony and sarcasm)). I’ve never used unsafe unintentionally, I use it because I believe usage is safe. There was no any malicious intentions. I believed it held mutable aliasing invariant and I was very happy that someone found real problem. I wanted to solve the problem, just with a bit of creativity. And use RefCell solution only if it would be not possible to solve it with any other way. Btw, I like the solution I found, it is in master and solves the problem at least one from the issue. If you want to push boundaries you have to touch this boundaries and sometimes you push too hard.

Be a maintainer of large open source project is not a fun task. You alway face with rude and hate, everyone knows better how to build software, nobody wants to do home work and read docs and think a bit and very few provide any help. Seems everyone believes there is large team behind actix with unlimited time and budget. (Btw thanks to everyone who provided prs and other help!) For example, async/await took three weeks 12 hours/day work stint, quite exhausting, and what happened after release, I started to receive complaints that docs are not updated and i have to go fix my shit. Encouraging. You could notice after each unsafe shitstorm, i started to spend less and less time with the community. You felt betrayed after you put so much effort and then to hear all this shit comments, even if you understand that that is usual internet behavior. Anyway, removing issue was a stupid idea. But I was pissed off with last two personal comments, especially while sitting and thinking how to solve the problem. I am sorry for doing that.

It’s been three years since I started actix project (time flies). I learnt a lot, i meet new people, I found language that I really like and want to use it fulltime, I found fun job. But damage to the project's reputation is done and I don’t think it is possible to recover. Actix always will be “shit full of UB” and “benchmark cheater”. (Btw, with tfb benchmark I just wanted to push rust to the limits, I wanted it to be on the top, I didn’t want to push other rust frameworks down.) Everything started with actix, then actix-web and then actix-net. It took a lot of time to design api and architecture. Each of this projects was rewritten from scratch at least 4-5 time. I hope I expanded some boundaries and found few new patterns, I hope other developers will check source code and find inspiration to move even further. Nowadays supporting actix project is not fun, and be part of rust community is not fun as well.

I am done with open source.

P.S. I moved actix-net and actix-web project to my personal github account. I will make decision during next couple days what to do. I don’t want to see the project becomes ghost of what it was. Maintainers must understand how everything work, but don’t anyone who does and those who could are busy with other projects. At the moment I am planing to make repos private and then delete them (will remove benchmarks as well), unless others suggest better ideas.

Everything has to come to the end. It was fun trip but now is time to move on. Life should be fun.

  
  
from Hacker News https://github.com/actix/actix-web/blob/master/README.md