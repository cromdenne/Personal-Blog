---
layout: post
title: A Photoblog with Jekyll
hero: https://c1.staticflickr.com/1/909/27324202137_9dd276b960_b.jpg
heroAlt: soccer ball at sunset
author: Cory Romdenne
excerpt_separator: <!-- end_excerpt -->
---

*I wanted a platform to share things.* Not a traditional social media platform —
I'm a relatively introverted guy and I've always felt strange posting on 
Facebook or Twitter. No, I wanted a platform where I could share on my own
terms.
<!-- end_excerpt -->
*I wanted to build something that was my own.* Although I'm quite the
amateur, I enjoy designing and coding things. I find inspiration in the
projects that others bring to life.

Those were the two criteria I had when deciding where I'd start this journey. I
had recently completed a project using Vim and GitHub, and now I wanted to 
create a personal blog as an outlet for the random stuff I do. In particular, I
wanted to be able to share photos, write about travel and experiences, and 
document useful coding tricks.

I discovered Jekyll, and the rest fell into place.

What follows is a broad overview of the photography features I created on this 
blog using [Jekyll](https://jekyllrb.com/){: .underline-effect}{:target="blank"}, [GitHub
Pages](https://pages.github.com/){:target="blank"},
[Bootstrap](http://getbootstrap.com/){:target="blank"} and 
[Flickr](http://www.flickr.com/){:target="blank"}. I wanted to document this 
process for myself, and if you also find it useful that's great!
<br>
<br>
<hr>
<br>
### Jekyll Collections
Let's assume we already have a functional Jekyll blog, and we're pushing to a
GitHub repo. If we're not already at that point, [pause to catch
up](https://help.github.com/articles/setting-up-your-github-pages-site-locally-with-jekyll/){:target="blank"}.  

Let's start by creating a new `_photos` collection at the root of our jekyll
site.

<div class="code-block">
  <div class="header">
Create a new folder for our photos collection<br>
<code>Mac terminal prompt</code>
  </div><!-- /.header -->
  <div class="code"><code>
    [website (master)]$ mkdir _photos
  </code></div><!-- /.code -->
</div><!-- /.code-block -->

Next, we need to tell Jekyll that we have a new collection. Let's update our
`_config.yml` file (or create one if we haven't yet).

<div class="code-block">
  <div class="header">
Update our config file so Jekyll knows about our new collection<br>
<code>~/website/_config.yml</code>
  </div><!-- /.header -->
  <div class="code"><code>
    collections:<br>
    &nbsp;&nbsp;photos:
  </code></div><!-- /.code -->
</div><!-- /.code-block -->

There are some other settings we can modify here in the config file, but for
now we don't need to add anything else.
