+++
title = "Using Amplify.js to Mock Service Calls"
date = 2012-02-09T13:48:00Z
updated = 2012-02-15T09:49:37Z
tags = ["Code"]
blogimport = true 
[author]
	name = "Sean Wesenberg"
	uri = "https://plus.google.com/111523202047342274226"
+++

<b>your-view-model.js</b><br /><br /><script src="https://gist.github.com/1782351.js?file=login.coffee"></script><br /><b>services.js</b><br /><br /><script src="https://gist.github.com/1782351.js?file=services.coffee"></script><br /><b>mock-services.js</b><br /><br /><script src="https://gist.github.com/1782351.js?file=mock-services.coffee"></script><br /><br /><b>What's happeing?&nbsp;</b><br /><br />We are simply overriding out service.js with mock-services.js. So... simply include the mock-service.js script AFTER you include the service.js script... And once you don't want to mock and more, simply comment out...<br /><br /><b>Resources</b><br /><br /><ul><li><a href="http://api.jquery.com/jQuery.ajax/">http://api.jquery.com/jQuery.ajax/</a></li><li><a href="http://speakerdeck.com/u/dougneiner/p/streamline-your-ajax-requests-with-amplifyjs-and-jquery">http://speakerdeck.com/u/dougneiner/p/streamline-your-ajax-requests-with-amplifyjs-and-jquery</a></li><li><a href="http://amplifyjs.com/api/request/#url_substitution/routing">http://amplifyjs.com/api/request/#url_substitution/routing</a></li></ul>
