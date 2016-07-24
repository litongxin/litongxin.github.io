---
layout: post
title: "CSS3 property: object-fit and its polyfill"
description: "CSS3 is the latest standard for CSS."
---

Object-fit is a new CSS3 property which aims to control the aspect ratio of  replaced elements like img/video during screen resizing.  

#### Basic Introduction
Method of specifying how an object (image or video) should fit inside its box. object-fit options include "contain" (fit according to aspect ratio), "fill" (stretches object to fill) and "cover" (overflows box but maintains ratio), where object-position allows the object to be repositioned like background-image does.
![How object-fit works](http://www.w3.org/TR/css3-images/img_scale.png)

#### Advance Skills
Browser support: http://caniuse.com/#feat=object-fit  
From the previous support page, **not all browsers** support this new CSS3 feature. So we need its polyfill to make it work in non-supported browser.  
There is one [polyfill](https://github.com/anselmh/object-fit) in github. And it's simple to use, just download and include the CSS file *polyfill.object-fit.css* and the JS file *polyfill.object-fit.min.js*.
But you still need to write the trigger JS file. The polyfill's README just suggest to add the following js code:
{% highlight javascript %}
<script>
    objectFit.polyfill({
        selector: 'img', // this can be any CSS selector
        fittype: 'cover', // either contain, cover, fill or none
        disableCrossDomain: 'true' // either 'true' or 'false' to not parse external CSS files.
    });
</script>
{% endhighlight%}
But this doesn't work on ie9. So I made my own triggger js adding the missing css style for the **x-object-fit** tag.
{% highlight javascript %}
$(window).load(function(){
  objectFit.polyfill({
      selector: '.hero-img img',
      fittype: 'cover',
      disableCrossDomain: 'true'
  });

  $("x-object-fit").css({"width":"100%","height":"100%","overflow":"hidden"});
});
{% endhighlight%}
