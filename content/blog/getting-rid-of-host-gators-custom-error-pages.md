+++
title = "Getting rid of Host Gator's custom error pages"
date = 2011-04-07T16:05:00Z
updated = 2011-04-07T16:05:28Z
blogimport = true 
[author]
	name = "Sean Wesenberg"
	uri = "https://plus.google.com/111523202047342274226"
+++

I don't particularly like HostGator as a company... Considering the inane 404 page they default your website to... But to remove that ad crap...<br /><br />1. Download the .htaccess file from the root of your server...<br /><br />2. Add the following lines (where /403.shtml can be any webpage you want to show for the specified error)<br /><span class="Apple-style-span" style="font-family: Tahoma, kalimati, arial; font-size: 12px;">ErrorDocument 403 /403.shtml</span><span class="Apple-style-span" style="font-family: Tahoma, kalimati, arial; font-size: 12px;"><br style="font-family: Tahoma, kalimati, arial; font-size: 12px;" /></span><span class="Apple-style-span" style="font-family: Tahoma, kalimati, arial; font-size: 12px;">ErrorDocument 404 /404.shtml</span><span class="Apple-style-span" style="font-family: Tahoma, kalimati, arial; font-size: 12px;"><br style="font-family: Tahoma, kalimati, arial; font-size: 12px;" /></span><span class="Apple-style-span" style="font-family: Tahoma, kalimati, arial; font-size: 12px;">ErrorDocument 500 /500.shtml</span><br /><span class="Apple-style-span" style="font-family: Tahoma, kalimati, arial;"><span class="Apple-style-span" style="font-size: 12px;"><br /></span></span><br />3. Upload and overwrite .htaccess<br /><br /><a href="http://support.hostgator.com/articles/cpanel/custom-error-pages">http://support.hostgator.com/articles/cpanel/custom-error-pages</a><br /><br />Don't know why they don't have a cpanel solution, but...<br /><br />Btw, it took me about a week to transfer my domain names from 1and1.com to hover.com... Looks like I won't be going back to 1and1 for anything... That's just ridiculous to ack a request for transfer. On a side note, hover is pretty nice if you're looking for domain name hosting.<br /><br />No need to call me back IT guy. Google &gt; my IT guy.
