+++
title = "Reeldata"
description = "Proxy cache your API calls"
author = "wookets"
date = 2018-04-19T22:17:45-05:00
weight = 20
draft = false
bref = "Proxy cache your API calls"
toc = true
+++

The point of reeldata is to hit a live API, but then cache the result, so that you can work offline or even store the data locally and right tests against it. Once you write your tests against the data, you can rerun reeldata to pull down fresh data and rerun your tests to see if the data contract changed. 

This obviously works best for read heavy APIs. 

[Reeldata Source](https://github.com/wookets/reeldata)