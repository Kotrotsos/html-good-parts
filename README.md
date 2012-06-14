HTML (And CSS) The Good Parts
===============

This is by no means as good as Javascript- the Good Parts by Douglas Crockford. However I wanted a place to highlight some of the
lesser known niceities that come with HTML. 

When talking about HTML, I do mean HTML and not XHTML.

This all will serve as a placeholder until there is enough content to structure.

Image not found detection
If you knew the following was possible, congratulations- you belong to a very select group.

    <img onerror="{doSomeJavascript}" src="image.jpg>
    
If the image returns an error (404)- the javascript statement will fire. The Javascript could contain an alert, but- also 
a placeholder image for instance. 

One way to do this:

      <img onerror="$(this).attr('src','http://ragecomics.com/-img/4f03e7fb1861333a8400308f.png');" src="deadimage.jpg">

So when deadimage.jpg cannot be found, it will show a nice little rage comic.

### Void elements.
Brings me to the following, and that is that the img element is a void element. That means you never need to close it.
    
    <img src="image.jpg" /> <!-- Invalid -->

There are many more void elements. Like ...