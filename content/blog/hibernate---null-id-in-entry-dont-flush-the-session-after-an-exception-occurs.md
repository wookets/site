+++
title = "Hibernate - null id in entry (don't flush the Session after an exception occurs)"
date = 2011-06-13T14:27:00Z
updated = 2011-06-19T17:30:22Z
tags = ["Code"]
blogimport = true 
[author]
	name = "Sean Wesenberg"
	uri = "https://plus.google.com/111523202047342274226"
+++

Exception:<br />null id in entry (don't flush the Session after an exception occurs)<br />I was getting the above exception in spring hibernate junit jpa type test when trying to persist an entity. You actually get the exception after the entity is 'persisted'. The error is thrown because of a validation type error with the database table (property not set when DB needs it to be set or something), but hibernate keeps chugging along and holds the object in session in a weird quasi not-persistent, but still in session state. Not sure why...<br /><br />Anyway, double check the properties you are setting on the last entity (before the exception) that you are attempting to save to the db. See reference link below for more help.<br /><br /><br />Reference:&nbsp;<a href="http://bchavez.bitarmory.com/archive/2007/11/14/nhibernate---null-id-in-entry-dont-flush-the-session.aspx">http://bchavez.bitarmory.com/archive/2007/11/14/nhibernate---null-id-in-entry-dont-flush-the-session.aspx</a>
