HTML (And CSS) The Good Parts
===============

This is by no means as good as (Or has anything to do with) Javascript- the Good Parts by Douglas Crockford. However I wanted a place to highlight some of the
lesser known niceities that come with HTML. It is not complete- I just started writing.

When talking about HTML, I do mean HTML and not XHTML.

This all will serve as a placeholder until there is enough content to structure.


### the HTML5 Doctype

[todo]

### Image not found detection
If you knew the following was possible, congratulations- you belong to a very select group.

    <img onerror="{doSomeJavascript}" src="image.jpg>
    
If the image returns an error (404)- the javascript statement will fire. The Javascript could contain an alert, but- also 
a placeholder image for instance. 

One way to do this (I'm using jQuery here, but you can use anything)

      <img onerror="$(this).attr('src','http://ragecomics.com/-img/4f03e7fb1861333a8400308f.png');" src="deadimage.jpg">

So when deadimage.jpg cannot be found, it will show a nice little rage comic.

### Void elements.
Brings me to the following, and that is that the img element is a void element. That means you never need to close it.
    
    <img src="image.jpg" /> <!-- Invalid -->

There are many more void elements. HTML5 recommendation outlines the following elements as beeing void:

area, base, br, col, command, embed, hr, img, input, keygen, link, meta, param, source, track, wbr

So it's perfectly ok to do

`<br>` instead of `<br/>` 

(which is actually XHTML) or `<input value="x">` instead of closing it. 

This creates a nice little bridge to the wbr element (also beeing a void element)

### wbr

According to the W3C recommendation, wbr represents a word break oppertunity. This means that, wherever this tag is inserted in
a long word- the word will break if needed on that spot.

So

    This text has a very long word in it, jabbarwocky<wbr>jockyjoo
    
Will break right after jabbarwocky, and jockyjoo will continue on the next line. 

Small example usage here http://dabblet.com/gist/2930298
Keep in mind though, that the use of wbr is considered bad practice these day's. However there are situations where it will come
in handy- possibly when using a CMS and you don't have control over textflow.

### hidden attribute (Currently a W3C Working Draft) 

"The hidden attribute is a boolean attribute. When specified on an element, it indicates that the element is not yet, or is no longer, relevant. 
User agents should not render elements that have the hidden attribute specified."

This attribute is meant to denote an element that has a state of visible or hidden (and not relevant anymore)- across all presentations. Like a display:none; on steroids.
It will be hidden- in any case, no matter what, until a change in state has occured. For instance, for a login box. 

    <p id="loggedin" hidden>This will only be visible when the state is loggedIn</p>

You can hide or show the element using the (when supported) corresponding method

    document.getElementById('loggedin').hidden = false;​// or true
    
### Protocol relative URL (i.e. never show security messages anymore when using mixed http and https content) ###

    <script src="//ajax.googleapis.com/ajax/libs/jquery/1.4.2/jquery.js"></script>
    
It is getting more and more popular, but it's worth mentioning here that if you omit the protocol from the URL, so instead of writing

    http://ajax ... 
    https://ajax ...
    
you write it like mentioned before- the browser figures out which protocol (http or https) to use. 

So if  you have http content (or content served from non https locations) and the page expects https. You will get that 'not secure content ... etc' error message.

There are edge-cases where this does not work as expected (Calling IE6 an edgecase here) but for the most part it will work just fine.

