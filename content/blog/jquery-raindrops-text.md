+++
title = "jQuery raindrops (text)"
date = 2011-07-11T14:14:00Z
updated = 2011-07-11T14:16:27Z
tags = ["Code"]
blogimport = true 
[author]
	name = "Sean Wesenberg"
	uri = "https://plus.google.com/111523202047342274226"
+++

I made a raindrop type effect for my website. Obviously, one could tweak it to get it closer to the desired effect one would be looking to achieve, but... <br /><br />Website: <a href="http://wookets.com">http://wookets.com/</a><br />Archive: <a href="http://wookets.com/archive/wookets-com-july2011/">http://wookets.com/archive/wookets-com-july2011/</a><br /><br />Everything is javascript, so you can right click and view the source. <br /><br />I was having some major problems, but breaking everything out into distinct functions seems to have alleviated those... Notably the generating and the adding of droplets and the dropping. <br /><br />There are many more small tweaks I could do... <br />- Getting rid of the animation to move elements (recycle) to the top of the page. (This should just be a straight move, if you see flickers of words in chrome, this is most likely why) <br />- The effects could be tweaked to be a bit smoother. <br />- The fact that everything drops at once at the start<br />- The resizing of the window... It will eventually handle height resizing, but it doesn't attempt to handle width resizing. <br />- Also note that I'm just changing the font color for the words. I wanted to avoid the CPU burden of doing an alpha mask. I suppose I could use some z coords for this as well, to avoid darker letters appearing before the white letters (but I kinda of like the effect) <br /><br />Take and use as you will.
