+++
title = "Swiz Framework Post Construct Order of Events"
date = 2011-05-02T13:05:00Z
updated = 2011-05-02T13:26:10Z
blogimport = true 
[author]
	name = "Sean Wesenberg"
	uri = "https://plus.google.com/111523202047342274226"
+++

Example and source:<br /><br /><a href="http://wookets.com/code/flex/SwizPostConstruct/">http://wookets.com/code/flex/SwizPostConstruct/</a><br /><br />I'm trying to figure out why Swiz is actually firing events in the exact opposite order that it says in the documentation. The application startup [PostConstruct] is fired after creationComplete, but the [PostConstruct] of views and objects is happening before creationComplete. Not sure why it's working like this. It was working fine before. Or so I thought.<br /><br />Anyway... A good reason to never trust the firing order of events in flex.<br /><br />References:<br /><a href="http://swizframework.jira.com/wiki/display/SWIZ/Bean+Life+Cycle+Management#BeanLifeCycleManagement-SwizandFlexLifeCycleSteps">http://swizframework.jira.com/wiki/display/SWIZ/Bean+Life+Cycle+Management#BeanLifeCycleManagement-SwizandFlexLifeCycleSteps</a><br /><br /><a href="http://swizframework.org/">http://swizframework.org/</a>
