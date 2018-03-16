+++
title = "Amazon S3 Website Hosting DNS Gotchya"
date = 2012-01-09T15:13:00Z
updated = 2012-01-09T15:13:06Z
tags = ["Code"]
blogimport = true 
[author]
	name = "Sean Wesenberg"
	uri = "https://plus.google.com/111523202047342274226"
+++

Recently, while setting up a website on Amazon's S3 (see <a href="http://aws.typepad.com/aws/2011/02/host-your-static-website-on-amazon-s3.html">here</a>), I was also attempting to set the mx records of the domain to point to google apps (see <a href="http://support.google.com/a/bin/answer.py?hl=en&amp;answer=33352">here</a>). But, the mx records were not updating.<br /><br />I thought this was a <a href="http://hover.com/">hover.com</a> problem. Btw, I've never had a company answer my phone call faster than these guys. It is actually quite freaky and I was unprepared with my question. Literally took less than a second to reach and start talking to a human being. Amazing.<br /><br />Anyway, I'm on the phone with hover and they tell me that the cname that is pointing to amazon is returning a faux mx record / screwing something up with the name server. I was a bit stunned about how this could be. Why would a cname screw up mx records. But it was true and my hover helper was right.<br /><br />Apparently, if you have a cname record @ that points to Amazon's S3, any custom mx records never reach the DNS.<br /><br />@ - domain - s3 website<br /><br />can't be used with<br /><br />@ - domain - mx records<br /><br />Well, that solves that problem I guess. And I suppose this problem may not be isolated to amazon and is probably some unknown dns protocol that I attempted to violate. Wish it would warn me though.<br /><br /><br />
