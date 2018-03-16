+++
title = "Flex - Load apps within an app"
date = 2011-04-02T11:19:00Z
updated = 2011-04-02T11:19:55Z
blogimport = true 
[author]
	name = "Sean Wesenberg"
	uri = "https://plus.google.com/111523202047342274226"
+++

Example and source:<br /><br /><a href="http://wookets.com/code/flex/AppLoaderDemo/">http://wookets.com/code/flex/AppLoaderDemo/</a><br /><br />It should be noted that setting or trying to bind the source on the SWFLoader doesn't work properly. As you change states within the parent app, you need to load and unload the whole app. This is best for memory management, but if you want to cache the app... well, it doesn't seem to work for me between states unless I load and unload the whole thing.<br /><br />If you're thinking; "why don't you just use modules?" My problem with modules is that Flash Builder keeps crashing on my big projects. Modules help the end user, but what about my workspace? Another point is that I need apps to run standalone or support by a dock or app management system. Also, I did a quick unvetted test of the final release build swf size for an application and for a module. They end up being the same at the start (around 40kb). I may have missed some optimization for the module, but 40kb not something I'm going to fret over. Now, I would assume over time, the size gap will become more apparent, but I doubt how much more so... And for my purposes, the separate apps that I'm loading really shouldn't be sharing any code but a tiny domain model class or two.<br /><br />PS - All apologies for the simplistic examples. Expect far more challenging architectures to come. These examples literally take 5 min to crank out.
