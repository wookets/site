+++
title = "From Blogger to Hugo"
description = "A guide for importing from blogger to hugo"
date = 2018-03-16T07:21:26-05:00
weight = 20
draft = false
+++

### The tools we will need 

It looks like there are two projects to help with this.

* [blogimport](https://github.com/natefinch/blogimport)
* [blogger-to-hugo](https://bitbucket.org/petraszd/blogger-to-hugo)

### blogimport first

The readme's for both don't look too great, so flipping a coin, let's go with [blogimport](https://github.com/natefinch/blogimport). Apparently [blogger-to-hugo](https://bitbucket.org/petraszd/blogger-to-hugo) also imports images, but I don't have any of those.

It looks like we will have to clone down the repo and run the go file inside. Navigate to a clean directory. 

{{< highlight bash>}}
cd ~/tmp
git clone git@github.com:natefinch/blogimport.git blogimport
{{< / highlight >}}

Now that we have the project copied down we need to execute the go file within it. 

If you don't have go, you can use [homebrew](https://brew.sh/) to easily get it. 

{{< highlight bash>}}
brew install go
{{< / highlight >}}

To execute a go file, simply run go run <file.go>.

{{< highlight bash>}}
go run main.go
{{< / highlight >}}

You should now see some noise in the console.

{{< highlight bash>}}
Usage: /var/folders/y9/pk039rk16t716pqbhz2xttmr0000gn/T/go-build711184690/b001/exe/main [options] <xmlfile> <targetdir>
options:
  -extra string
        additional metadata to set in frontmatter
exit status 1
{{< / highlight >}}

So we need to read from an xml file and dump to a target directory. For the xml file, you can simply dump your blogger posts - they call it "backup" - which is in the settings for your blog and then the other options. 

Here is the command I ran;

{{< highlight bash>}}
go run main.go blog-03-16-2018.xml ../site/content/blog/
{{< / highlight >}}

Which created a whole ton (I had 77 previous blog posts on blogger) of markdown blog posts in my blog folder for hugo. 

Going back to my hugo site to run the following...

{{< highlight bash>}}
hugo serve
{{< / highlight >}}

Results in... 

{{< highlight bash>}}
MacBook-Pro:site wookets$ hugo serve

                   | EN
+------------------+-----+
  Pages            | 111
  Paginator pages  |  31
  Non-page files   |   0
  Static files     |  32
  Processed images |   0
  Aliases          |  12
  Sitemaps         |   1
  Cleaned          |   0

Total in 215 ms
{{< / highlight >}}

Sweet!

Viewing at localhost:1313 and now I have more blog posts than is probably necessary. 