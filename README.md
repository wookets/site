
# Site

This is simply the source code for wookets.github.io. This project is used to keep the source code and do local dev. Travis-ci is used to build and take that ouput and put it into the wookets.github.io repo for hosting the gh-page.

## Usage

To see stuff locally;
```bash
hugo serve
```

To make a new document;
```bash
hugo new projects/patent-buddy.md
```

Hugo is smart enought to crawl around in the archetypes folder and see that you already defined a layout for projects and apply those settings. 

## Behind the Scenes

This project uses [hugo](https://gohugo.io/) which is a go-lang based static site generator. It's super fast, has theming, support for blogging, and will let you import from other websites - for me it helped me move off of Google's blogger. 

I'm using the [Kube](http://kube.elemnts.org/) theme for this project which supports all major browsers and is mobile-first. 