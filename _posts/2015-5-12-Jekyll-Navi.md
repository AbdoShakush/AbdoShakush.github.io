---
layout: post
title: How to fix the Jekyll post-relative navigation
---

I wanted to add a blogging feature to my site, but did not want the overhead of having a separate Wordpress site for it. I set my eyes on Jekyll, but I found out that it can't live in a sub-folder as I wanted. After many, many problems with themes and folder structures, I had a mostly working Jekyll blog.. for one exception - the navigation did not work. What would happen is, when you opened a post and wanted to use the navigation it would insert the link after the post, like this:

```
http://shakush.me/<postname>/index.html
```

which of course doesn't work and leads to a 404 Page Not Found.

# What I tried

The first thing I tried was to hard-code the links in the default-layout, which resulted in the same thing happening.


I hoped that this would fix it, but it didn't. It just appended the links to after the post in the URL.

```
<a href="http://shakush.me/">Home</a>
<a href="http://shakush.me/Blog.html">Blog</a>
<a href="http://shakush.me/About.html">About</a>
```


# How to actually fix it

Start off by adding the baseurl in the _config.yml. Mine looks like this:

```
baseurl: "http://shakush.me"
```

This is important because it will be prepended before the page.


And in the default.html layout:

```
<a href="site.baseurl/">Home</a>
<a href="site.baseurl/Blog.html">Blog</a>
<a href="site.baseurl/About.html">About</a>
```

**Note: Encase site.baseurl in double curly braces on each side. I removed the to be able to display them and not turn into the baseurl itself.**

This way no matter what, your navigation will work and will not be added after the post name.


I hope this helped you. It took me a while to figure out what was happening.