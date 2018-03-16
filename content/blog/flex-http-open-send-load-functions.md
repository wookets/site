+++
title = "Flex HTTP open, send, load functions"
date = 2011-04-07T15:52:00Z
updated = 2011-04-07T15:52:00Z
blogimport = true 
[author]
	name = "Sean Wesenberg"
	uri = "https://plus.google.com/111523202047342274226"
+++

An example of the three different ones. These don't cover any mxml service type things. Maybe later.<br /><br />navigateToUrl - Will open a page with the url specified.<br /><br />sendToUrl - Will send a request behind the scenes, but won't tell you what the response was...<br /><br /><div style="margin-bottom: 0px; margin-left: 0px; margin-right: 0px; margin-top: 0px;">URLLoader - Will allow you listen for a response or know when the request you just sent has been completed (acknowledged).&nbsp;</div><div><br /></div>Example and source:<br /><br /><a href="http://wookets.com/code/flex/SendDataDemo/">http://wookets.com/code/flex/SendDataDemo/</a><br /><br />I should mention that for the URLLoader I had to stick a crossdomain.xml policy file at the root of my web directory. Which you'll need if you get the security sandbox violation error.<br /><br />Another simplistic example, but just needed a refresher myself... One of the next posts should be how to interact with Google's Spreadsheet API, so perhaps that will feel more meaningful than these last few examples.
