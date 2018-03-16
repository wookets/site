+++
title = "Error handling with Express 3.x"
date = 2013-01-03T15:51:00Z
updated = 2013-02-05T16:08:22Z
tags = ["node", "errors", "express"]
blogimport = true 
[author]
	name = "Sean Wesenberg"
	uri = "https://plus.google.com/111523202047342274226"
+++

Here is a quick middleware error handler. It essentially follows the express document to a T. It should however be noted that exceptions in the code will not be caught by this, since they will break the whole server. For that, you need to use node domains, which are new in 0.8.x and should be in an upcoming post. <br /><div class="gistLoad" data-id="4447616" id="gist-4447616">Loading...</div><script src="https://raw.github.com/moski/gist-Blogger/master/public/gistLoader.js" type="text/javascript"></script>
