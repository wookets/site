+++
title = "Less (CSS) Grid Example"
date = 2011-12-11T10:48:00Z
updated = 2011-12-11T10:57:41Z
tags = ["Code"]
blogimport = true 
[author]
	name = "Sean Wesenberg"
	uri = "https://plus.google.com/111523202047342274226"
+++

One of the main reasons for using a language like <a href="http://lesscss.org/">Less</a> is to move away from using 'span10' or 'col10' when using a grid based html layout for your webpage.<br /><br />After all...<br /><br />&lt;div class="row"&gt;<br />&nbsp; &lt;div class="span10"&gt;Main Content&lt;/div&gt;<br />&nbsp; &lt;div class="span4"&gt;Side Content&lt;/div&gt;<br />&lt;/div&gt;<br /><br />Doesn't seem right... But...<br /><br />&lt;div class="content"&gt;<br />&nbsp; &lt;div class="main"&gt;Main Content&lt;/div&gt;<br />&nbsp; &lt;div class="side"&gt;Side Content&lt;/div&gt;<br />&lt;/div&gt;<br /><br />Seems a little better...<br /><br />The problem is, how do we apply .span10 to .main and achieve the same effect?<br /><br />Less <a href="http://lesscss.org/#-mixins">Mixins</a> can certainly help. Suddenly, we can do the following...<br /><br />.main {<br />&nbsp; .span10;<br />}<br /><br />And Less will compile the properties that make up .span10 into our .main css. However, be careful, because some frameworks (such as Bootstrap) use class name based selectors to add further styles (namely inline).<br /><br />Demo: <a href="http://archive.wookets.com/examples/html5/lessgrid/">http://archive.wookets.com/examples/html5/lessgrid/</a><br /><br />Source:&nbsp;<a href="https://github.com/wookets/lessgrid">https://github.com/wookets/lessgrid</a><br /><br />Btw, if you're on OSX and want to easily compile Less, check out <a href="http://incident57.com/codekit/index.php">Codekit</a>.<br /><br />All of this being said, be careful. Things break really easily if you don't know what you're doing, which in that case it might be better to stick with span# in your html... You know, for stableness.<br /><br />Resources:<br /><br />- Twitters Bootstrap Framework -&nbsp;<a href="http://twitter.github.com/bootstrap/">http://twitter.github.com/bootstrap/</a><br /><br />- Less -&nbsp;<a href="http://lesscss.org/">http://lesscss.org/</a><br /><br />- Codekit -&nbsp;<a href="http://incident57.com/codekit/index.php">http://incident57.com/codekit/index.php</a>
