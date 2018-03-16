+++
title = "How to Hugo"
description = "An overview of the steps to create a statically generated site with Hugo, Github, Travis-ci."
date = 2018-03-13T22:09:55-05:00
weight = 20
draft = false
bref = "An overview of the steps to create a statically generated site with Hugo, Github, Travis-ci"
toc = true
+++

### Disclaimer

I had some help;
* https://www.metachris.com/2017/04/continuous-deployment-hugo---travis-ci--github-pages/

### Intro to Hugo

[Hugo](https://gohugo.io/) is a static website generator. In my case, I was looking for a blog + some doc stuff. It's always helpful to have an easy way to create pages. Sure, I looked at [Jekyll](https://jekyllrb.com/), but Hugo turned out to be a bit easier. The reality is, it depends a bit on the [theme](https://themes.gohugo.io/) you choose as well. 

### Setting it all up

Follow the [hugo quick setup](https://gohugo.io/getting-started/quick-start/).

Installing a theme can be a little tricky. I recommend following the quick setup method. However, be aware this will clone down a git repo, so you'll want to wipe out .git from that, otherwise it won't commit and you may be wondering why only have your static files are building when you go to deploy. 

Once you have your theme installed you'll need to pull files up to your root project and recreate some folders. Essentially, if the theme doesn't find the file in the root, it will default back down into the theme folder. In this way, you can own the theme without touching the original files. 

### Adding a new post or doc

Sure, you can manually create new blog and doc files, but you should just use the command line "hugo new --king blog blog/first-post.md"