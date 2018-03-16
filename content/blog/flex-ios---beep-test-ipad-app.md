+++
title = "Flex iOS - Beep Test iPad App"
date = 2011-04-04T21:26:00Z
updated = 2011-04-04T21:26:53Z
blogimport = true 
[author]
	name = "Sean Wesenberg"
	uri = "https://plus.google.com/111523202047342274226"
+++

<div>I'm making my soccer team run the <a href="http://en.wikipedia.org/wiki/Multi-stage_fitness_test">beep test</a> this Saturday, so I decided to code up an iPad app to help.&nbsp;</div><div><br /></div><div>The app is written using a flex 4.5 hero build. I have&nbsp;already tested it on my iPad 2 using the Air 2.6 ADT packager. Besides a hiccup when playing the very first beep, it runs silky smooth and feels stable.&nbsp;</div><br /><div><a href="http://www.wookets.com/code/flex/BeepTest/">http://www.wookets.com/code/flex/BeepTest/</a></div><div><div><br /></div><div>App dimensions are... width="1024" height="768" (iPad dimensions)</div><div><br /></div><div>This will eventually be included in my other iPad coaching app, but I'm still waiting for Adobe to release Burrito to see if it speeds / fixes some things, before I have to rewrite the app for optimization purposes. Specifically, lists, animations, state changes...&nbsp;</div></div><div><br /></div><div>PS - flex 4 state changes in iOS are SLOOOOOW.... Makes sense given what a state change is actually doing. I originally wrote the app to use flex 4 states (they are nice), but changing between states is just a fraction of a second unresponsive enough to be unusable. Certainly not usable by Steve's standards.&nbsp;</div><div><br /></div><div>Let me know if you're interested in the source code. I'll probably submit this to the app store to give those apple employees something to do this week. The app took me about 2 days to write. Probably 12 hour in total. That includes 1 rewrite. The hardest part being the shifting levels and shuttles.&nbsp;</div><div><br /></div><div>Also note that the shuttle intervals are actual using a Math.ceil() function. This makes it easier / faster for the timer to check to see if the next shuttle is hit. One could change things to ensure a little more precision, but... I'm too tried to change it now... Will probably modify before an app store release.&nbsp;</div>
