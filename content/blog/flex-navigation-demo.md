+++
title = "Flex Navigation Demo"
date = 2011-07-21T19:43:00Z
updated = 2011-07-22T09:04:24Z
tags = ["Code"]
blogimport = true 
[author]
	name = "Sean Wesenberg"
	uri = "https://plus.google.com/111523202047342274226"
+++

Demo and Source (right-click):<br /><br /><a href="http://wookets.com/code/flex/NaviDemo/FlexNaviDemo.html">http://wookets.com/code/flex/NaviDemo/FlexNaviDemo.html</a><br /><br />A very simple navigation demo.<br /><br />The crux is... Define your views at the root of the application. Then use a contextual class to update the root view a generic 'goto' function. This is done view the static Navi class, but could certainly be done using IoC or a Singleton type pattern. FYI, this is using states, but one could also use a viewstack (there is a flex 4 version somewhere around here)...<br /><br />More presentation model pattern next.
