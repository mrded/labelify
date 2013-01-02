labelify
========
_a jQuery plugin to add labels to your textboxes_

A fairly common design pattern in web forms is to have some explanatory help text for a textfield appear inside the text field, and then remove it when the user clicks into that field. It has the benefit of putting the help precisely where the user's looking.

##This is _fork_
Original _1.3 version_ from _25th June 2008_ by __Stuart Langridge__ located [here](http://www.kryogenix.org/code/browser/labelify/).

##What's the difference?
* jQuery object that has been passed into the IIFE (Immediately Invoked Function Expression)
* Password input type support.

##How to use the plugin

1. Since this is a [jQuery](http://jquery.com) plugin, it requires jQuery itself. You can either [download jQuery](http://jquery.com/) and make it part of your project, or for simplicity just use the Google edge-cached version by adding this to your HTML:

    `<script type="text/javascript" src="http://ajax.googleapis.com/ajax/libs/jquery/1.2.6/jquery.min.js"></script>`

2. Next, download jquery.labelify.js and add it to your project with

    `<script type="text/javascript" src="jquery.labelify.js"></script>`

3. You need to specify which text fields you want to have labels. By default, the plugin uses the title attribute of the input text field as the label. So change your text fields from

    `<input type="text" name="whatever">`

to

    <input type="text" name="whatever" title="Help text goes here">

4. Finally, you need to tell the plugin to lability your fields:

    `<script type="text/javascript">
      $(document).ready(function(){
        $(":text").labelify();
      });
    </script>`

You can of course add this to your existing document-ready code block.

##What if I don't want to use the title attribute as the text source?

The plugin is customisable. When you call lability, you can pass an options object. To change the source of the text that's used to add a label to your input box, pass a different value for text:

    $("input").labelify({
      text: "label"
    });

The value "label" for text will fetch the input's "tooltip" from that input's associated label:

    $("input").labelify({ text: "label" });
    ...
    <label for="myinput">Your favourite colour</label>
    <input id="myinput" type="text">
    
Note that this does not remove the text from the label itself; if you want that to happen then you can hide it in CSS.

If "label" isn't what you want either, then you can pass a function as text. The function is called with your input field as a parameter and can use that to return whatever it likes:

    $("input").labelify({ text: function(input) { return "kryogenix.org"; } });
    ...
    <input type="text">
    
##How can I make the label look different?

You'll note that in the examples on this page, user-entered text in the boxes is black but the label that's added is a light grey. To do this, pass another parameter in the options list, labelledClass. This will set class="labelledClass" on the input box when it contains the help text label, and remove that class when the input box contains user input.

    $("input").labelify({ labelledClass: "labelHighlight" });
    ...
    <style type="text/css">
    input.labelHighlight { color: red; }
    </style>
    ...
    <input name="someinput" type="text" title="Helpful text">
    
##Why should I use _this_ lability script?

Lots of people, as noted above, have written scripts that do this. You might want to use this one for the following reasons...

1. It copes with users who fill in some text while the page is still loading, and doesn't overwrite their entry with the label once the page is loaded
2. It can be customised to pick up your input box label text from wherever you want; it's not hardcoded to use a <label> element, or the title attribute, or any similar thing
3. It caters for browsers "remembering" the values in a field

##Why might I not want to use it?

1. It's a jQuery plugin. If you're not already using jQuery in your project, then I wouldn't pull it in just for this. On the other hand, if you're doing any DOM scripting then you'll almost certainly find jQuery useful; it's the best JavaScript library out there.
2. Perhaps you like pain. I don't know.
