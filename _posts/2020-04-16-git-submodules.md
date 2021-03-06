---
layout: post
title:  'Today I Learnt: Git Submodules'
date:   '2020-04-16'
categories: stories
tags: ['Git']
comments: true
---
It often happens that while working on one project, you need to use another project from within it. For that, we can make use of git submodules.

Submodules are a reference to another repository withing a parent repository. You can make a submodule point to any arbitrary revision of the other repo.

Today I learned how messy git submodules could be! 😾

Using submodules needs many disciplines. Every developer using repo always need to update submodules using git submodule update --init --recursive. Failing to update can lead to very hard to debug and silent errors. And that's not all if you forget to update the submodules, then git commits the old version of the submodule. This effectively undoes the submodule update done by another developer. And git log doesn't even show such an update 😓.

Submodules need references to the URL that git should fetch. We all use SSH authentication in git. To make submodules experience frictionless, we point submodules using another SSH URL. When you start consuming this repo in CI such as Jenkins, which uses https to clone, everything breaks 😢 , so either you force your CI to clone ssh and set up its authentication or force your ci to pull everything in https, which is not possible in all scenarios. Now we are left with a decision to choose between frictionless CI or frictionless development experience. 😕

Also, there are many stories about submodules getting lost during merge conflicts, submodules not supported by some UI tools, etc. which makes them pure evil.

Some people say submodules are "Sobmodules." 🤣

Originally Posted at https://todayilearnt.xyz/posts/nancy/git_submodules/ 
