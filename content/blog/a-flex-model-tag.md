+++
title = "A flex [Model] tag"
date = 2011-08-15T14:55:00Z
updated = 2011-08-15T17:07:40Z
tags = ["Code"]
blogimport = true 
[author]
	name = "Sean Wesenberg"
	uri = "https://plus.google.com/111523202047342274226"
+++

If you are unfamiliar with the Presentation Model design pattern (MVVM) or declarative UI, please google and / or read the link below.<br /><br /><a href="http://swizframework.jira.com/wiki/display/SWIZ/Presentation+Model">http://swizframework.jira.com/wiki/display/SWIZ/Presentation+Model</a><br /><a href="http://en.wikipedia.org/wiki/Model_View_ViewModel">http://en.wikipedia.org/wiki/Model_View_ViewModel</a><br /><br />Now, what I've done is taken this design model and made a tag for Swiz flex applications.<br /><br /><a href="http://swizframework.org/">http://swizframework.org/</a><br /><br />Reasons:<br /><br />1. I was sick of declaring prototype beans.<br /><br />2. [Model] is more clear than [Inject]... In terms of making sure people are following the pattern.<br /><br />3. I did not like (but the tag does support) the idea of changing a UI state in the Model code. To me, it seems like the coder is dictating to the UI what it should be doing, instead of the UI reacting to the model and doing it's own thing. There are ways around this, but I felt an event based method (since we are using flex) would be far better than observing a bound property.<br /><br />Here is a sample application:<br /><br /><a href="http://wookets.com/code/flex/ModelTagDemo/APMDemo.html">http://wookets.com/code/flex/ModelTagDemo/APMDemo.html</a><br /><br />(right click to view source as always)<br /><br />Here is a library<br /><br />Swc:&nbsp;<a href="http://wookets.com/code/flex/ModelTag/bin/ModelTag.swc">http://wookets.com/code/flex/ModelTag/bin/ModelTag.swc</a><br /><br />Src:&nbsp;<a href="http://wookets.com/code/flex/ModelTag/">http://wookets.com/code/flex/ModelTag/</a><br /><br /><br />References:<br /><br />swiz framework<br />http://swizframework.org/<br /><br />presentation pattern (aka MVVM)<br />http://swizframework.jira.com/wiki/display/SWIZ/Presentation+Model<br />http://en.wikipedia.org/wiki/Model_View_ViewModel<br /><br />a good custom tag example<br />http://www.ryancampbell.com/2010/03/26/introducing-the-swiz-urlmapping-metadata-processor/<br />http://blog.comtaste.com/2010/05/swiz_framework_custom_metadata.html<br /><br />
