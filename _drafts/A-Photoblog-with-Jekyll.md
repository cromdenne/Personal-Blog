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
Pages](https://pages.github.com/){: .underline-effect}{:target="blank"},
[Bootstrap](http://getbootstrap.com/){: .underline-effect}{:target="blank"} and 
[Flickr](http://www.flickr.com/){: .underline-effect}{:target="blank"}. I 
wanted to document this process for myself, and if you also find it useful 
that's great!
<br>
<br>
<hr>
<br>
### Jekyll Collections
Let's assume we already have a functional Jekyll blog, and we're pushing to a
GitHub repo. If not, [pause to catch
up](https://help.github.com/articles/setting-up-your-github-pages-site-locally-with-jekyll/){:.underline-effect}{:target="blank"}.  

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
<code>~/website/_<!--_-->config.yml</code>
  </div><!-- /.header -->
  <div class="code"><code>
    collections:<br>
    &nbsp;&nbsp;photos:
  </code></div><!-- /.code -->
</div><!-- /.code-block -->

There are some other settings we can modify here in the config file, but for
now we don't need to add anything else. However, we can't forget to restart our 
Jekyll server so that changes to the `_config.yml` file will take effect!

Now we're ready to add photos to our collection. Each photo will be represented
by a single markup file, which will hold metadata for the photo. I don't keep 
my images inside the website repo because [GitHub doesn't like it when a repo 
is larger than
1GB](https://help.github.com/articles/what-is-my-disk-quota/){:target="blank"}{:
.underline-effect}. Instead, I use a free Flickr account to host my photos. Any
service could be used because we'll just be linking back to the photos from
each of our markdown metadata files.

Let's go ahead and add a few photos to our collection so that we can work with
them when styling our masonry layout. It's best to keep our photos organized,
so let's choose a naming convention and stick with it.

<div class="code-block">
  <div class="header">
Create a new photo markdown file for our collection<br>
<code>~/website/_<!--_-->photos/sf-port.md</code>
  </div><!-- /.header -->
  <div class="code"><code>
  ---<br>
  image_path: https://c1.staticflickr.com/your-image-url.jpg<br>
  title: Port of San Francisco<br>
  location: San Francisco, CA<br>
  time: April 2018<br>
  camera_make: Sony<br>
  camera_model: ILCE-6000<br>
  focal_length: 30<br>
  aperture: 2.0<br>
  shutter_speed: 1/50<br>
  iso: 400<br>
  ---<br>
  <br>
  Lorem ipsum dolor sit amet.
  </code></div><!-- /.code -->
</div><!-- /.code-block -->

Many of these fields are custom and not required. We do need an `image_path`
(or similarly-named) field, but beyond that we can get creative — the metadata
we use here depends on what we'd like to display in our gallery. I include 
photo EXIF data for my blog, but we can use as many or as few fields as we want.

Outside of the file's frontmatter we can also add content. We could use this
area for photo captions or stories.

Let's create a few more photos now. We could even use Google or
[Unsplash](https://unsplash.com/){: .underline-effect}{:target="blank"} to
grab some placeholder photos while we're working with the layout. Five is
probably enough for us to get started.

<div class="code-block">
  <div class="header">
Add a few more photos toour collection<br>
<code>Mac terminal prompt</code>
  </div><!-- /.header -->
  <div class="code"><code>
  [website (master)]$ ls _<!--_-->photos/<br>
  sf-baybridge.md<br>
  sf-californiastreet.md<br>
  sf-goldengatebridge.md<br>
  sf-port.md<br>
  sf-pyramid.md
  </code></div><!-- /.code -->
</div><!-- /.code-block -->

We've got a `_photos` collection with several photos in markdown format, so now
we're ready to move on and create our gallery page.
<br>
<br>
<hr>
<br>
### Masonry with Bootstrap
Bootstrap 4.0 has a great built-in feature that makes it easy to create a
masonry layout — [card
columns](https://getbootstrap.com/docs/4.0/components/card/#card-columns){:
.underline-effect}{:target="blank"}. With card columns we can also include
captions or other text with our images, allowing for a lot of flexibility.

If we don't have Bootstrap integrated with our project yet, [let's do that
now](https://getbootstrap.com/docs/4.0/getting-started/introduction/){:
.underline-effect}{:target="blank"}.

Next, let's create a gallery page and add the basic card column components.

<div class="code-block">
  <div class="header">
Create a gallery page and add card columns<br>
<code>~/website/gallery/index.html</code>
  </div><!-- /.header -->
  <div class="code"><code>
  ---<br>
  layout: default<br>
  title: Website<br>
  ---<br>
  <br>
  <pre>
&lt;div class="container-fluid"&gt;
  &lt;div class="card-columns"&gt;
    &lt;div class="card"&gt;
      &lt;img class="card-img" src="/images/image_url.jpg" alt="alt text"&gt;
    &lt;/div&gt;<span class="comment">&lt;!-- /.card --&gt;</span>
  &lt;/div&gt;<span class="comment">&lt;!-- /.card-columns --&gt;</span>
&lt;/div&gt;<span class="comment">&lt;!-- /.container-fluid --&gt;</span>
  </pre>
  </code></div><!-- /.code -->
</div><!-- /.code-block -->
