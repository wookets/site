+++
title = "Does anyone use A-Records anymore?"
date = 2011-11-07T13:42:00Z
updated = 2011-11-07T13:43:31Z
tags = ["Thoughts"]
blogimport = true 
[author]
	name = "Sean Wesenberg"
	uri = "https://plus.google.com/111523202047342274226"
+++

My blog keeps trying to ping my Amazon S3 account to serve content. FYI, my main page <a href="http://wookets.com/">wookets.com</a> is &nbsp;hosted on Amazon S3 in a bucket. The bucket is web enabled with a policy file (see previous post). However, this blog is hosted on Google's blogger.com.<br /><br />My Hover DNS settings had three A-Records for my blog that resolved to google's server, but checking out the latest Google blogger docs it seems like those A-Records are now defunct. Instead c-names are used. Which, I personally find a bit better about. Though it does take away SSL, but blogs really don't need SSL.<br /><br /><br />Resources:<br /><br /><a href="http://www.google.com/support/blogger/bin/static.py?page=ts.cs&amp;ts=1233381">http://www.google.com/support/blogger/bin/static.py?page=ts.cs&amp;ts=1233381</a><br /><br /><a href="http://www.hover.com/">http://www.hover.com</a><br /><br /><a href="http://aws.amazon.com/">http://aws.amazon.com</a>
