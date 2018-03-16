+++
title = "Auditing Page Performance"
date = 2017-08-26T08:10:00Z
updated = 2017-08-26T08:10:18Z
blogimport = true 
[author]
	name = "Sean Wesenberg"
	uri = "https://plus.google.com/111523202047342274226"
+++

If you are on the latest Chrome (59/60) you may have noticed that google as integrated <a href="https://github.com/GoogleChrome/lighthouse">lighthouse v2</a> into the Audits tab. This is a wonderful tool if you are looking to see how your site stacks up to google's on standards - and hopefully enlighten you to new technologies and tools you can use to optimize your website.   https://github.com/GoogleChrome/lighthouse  This tool is awesome because they offer a lot of different ways in. There is a CLI, which you can run with a standard node install. There is the tab in chrome to make it quick to run an audit. And even better, you can npm install lighthouse and use their core API to kick of reports without human intervention - even better you can pass in custom configs, gatherers, audits, test cases, dump to json or create your own report... It's really pretty extensible.   If you take a look at my <a href="https://github.com/wookets/lighthouse-sandbox">github lighthouse sandbox</a>, I'm simply looping over a set of web pages and dumping out reports to a results folder. But, since this is all programatic, future plans would be to start generating tickets for devs to get cracking on fixes. Or a week-over-week comparison dashboard - are we making progress? - This report also looks pretty solid as a health report to upper management and makes it easy to help prioritize some outstanding tech debt.     PS - Yeah, it seems google is setting the standards for what a "good" website looks like, but they do also own the SEO rankings and the browser that will be tailoring all of these tweaks to promote your pages, so... for now we are just going to have to play along.  
