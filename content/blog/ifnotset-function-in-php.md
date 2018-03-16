+++
title = "ifnotset function in php"
date = 2011-08-03T17:22:00Z
updated = 2011-08-03T17:22:46Z
tags = ["Code"]
blogimport = true 
[author]
	name = "Sean Wesenberg"
	uri = "https://plus.google.com/111523202047342274226"
+++

Here is a simple php function that acts like a ternary if-else operator, but is a bit shorter. I believe groovy has something similar, that is; native support for what I'm trying to do...<br /><br />The crux:<br /><br />// old school<br />if(var1 == null) {<br />&nbsp; var1 = var3;<br />} else { // this else is really&nbsp;unnecessary<br />&nbsp; var1 = var1;<br />}<br />// modified above example<br />if(var1 == null) var1 = var3;<br /><br />or<br /><br />if(!var1) var1 = var3;<br /><br />// ternary<br />var1 = var1 == null ? var3 : var1;<br /><br />// ternary shorthand<br />var1 = var1 ?: var3;<br /><br />The problem with all of the above examples is that php complains if a variable isn't set or defined. At least php 5.3 does on standard settings. And you are still repeating var1.<br /><br />The real way this should be done, and I believe this is how groovy does it is the following...<br /><br />var1 ?= var3;<br /><br />But, my function syntax is...<br /><br />setifnot(var1, var3);<br /><br />This function uses isset (so no php complaining about undefined variables) and uses a pass by reference to the function, so we only need to write out the variable once. I don't know, I prefer to stay within the confines of the native syntax, but I also don't like repeating myself / nor turning off error messages / nor declaring variables at the top of the file and nulling them out. I suppose my CS prof would be thrilled, but I'm lazy.<br /><br />See source below:<br /><br /><pre class="brush:php">&lt;?php<br /><br />// ternary type expression<br />function setifnot(&amp;$value, $defaultValue) {<br /> $value = isset($value) ? $value : $defaultValue;<br />}<br /><br />$setvar = "5";<br />setifnot($setvar, "7");<br />echo "Nothing changed with setvar [" . $setvar . "] because it was already set.";<br /><br />echo "&lt;br /&gt;\n\r";<br /><br />setifnot($unsetvar, "8"); <br />echo "Unsetvar is now set to [" . $unsetvar . "]";<br /><br />?&gt;<br /></pre>
