---
layout: post
title: Fixed On Scroll Animated Header with CSS and JavaScript
categories: css javascript tutorial example 
---

In this post I will explain how to create an animated sticky header, with CSS3 and JavaScript. So we are going to have a header that will behave normally until we have to scroll and then it will become smaller but still stick to the top of the viewport.

####The HTML

For this example all we need is a header with an h1 and the main div which holds the content that we can scroll over.

{% codeblock lang:html %}<body>
  <header>
    <h1>Animated Sticky Header</h1>
  </header>
  <div id="main">
      <p> Curabitur quam neque, malesuada sit amet justo ut, posuere pretium quam. In laoreet nunc velit. Nam mattis erat et leo mollis, sed pulvinar lectus volutpat. Phasellus mi eros, sollicitudin non elit sed, molestie viverra eros. Nullam facilisis mauris ante, sed vulputate sapien efficitur quis. Curabitur vitae lorem eros. Fusce orci odio, eleifend et sem luctus, bibendum viverra nibh. Proin vitae libero egestas, consequat orci id, facilisis ex. Quisque lectus dui, mattis non lectus ac, finibus facilisis velit. Integer mauris nibh, suscipit eu egestas nec, placerat scelerisque purus. Nulla facilisi. Proin eleifend, lectus eget rutrum luctus, dolor nunc luctus ex, sed consequat urna nisi ac ipsum.In hac habitasse platea dictumst.<p>
  </div>
</body>{% endcodeblock %}

####The CSS

In order to make the header sticky we have to fix it's position to the top of the viewport, hide any overflow and make sure it is always visible by setting the ```z-index``` of the header:
{% codeblock lang:css %}overflow: hidden;
position: fixed;
top: 0;
left: 0;
z-index: 999;{% endcodeblock %}

This will now keep the header always at the top and visible.


The animation of the header can be achived by having a different style rule for when the user has scrolled down -```.smaller``` class. We cna detect if the user has scrolled down using JavaScript (described below) and apply the ```.smaller``` class to the ```<header>```. When the header is smaller, we are reducing its height and the font size of the ```<h1>```. This is now the full CSS:

{% codeblock lang:css %}html,
body {
  margin: 0;
  padding: 0;
  height: 100%;
  min-height: 100%;
}

header {
  background: #F58065;
  padding: 0.75em;
  height: 4em;
  color: #fcfcfc;
  overflow: hidden;
  position: fixed;
  top: 0;
  left: 0;
  z-index: 999;
  width: 100%;
}

h1 {
  max-width: 70%;
  margin: 0 auto;
  font-size: 2em;
}

.smaller {
  height: 2em;
}

.smaller h1 {
  font-size: 1em;
}

p {
  max-width: 70%;
  margin: 0 auto;
  min-height:700px; /**this is just to force scrolling since we don't have much content**/
}

#main {
  display: block;
  padding-top: 8em;
}{% endcodeblock %}


####The JavaScript

As mentioned above, in order to animate the header we have to detect of the user is scrolling. This can be achieved by checking if the ```pageYOffset``` or the value received from the ```document.documentElement.scrollTop``` the returned value is the distance scrolled in pixels. 

{% codeblock lang:javascript %}function init() {
window.addEventListener('scroll', function(e){
  var distanceY = getScrollTop(),
      shrinkOn = 20,
      header = document.querySelector("header");
  if (distanceY > shrinkOn) {
    header.setAttribute("class","smaller");
  } else {
      header.removeAttribute("class");
  }
});
}

function getScrollTop() {
  if(typeof pageYOffset != 'undefined'){
      //most browsers except IE before 9
      return pageYOffset;
  }
  else {
      var B = document.body; //IE 'quirks'
      var D = document.documentElement; //IE with DOCTYPE
      D = (D.clientHeight)? D: B;
      return D.scrollTop;
  }
}
window.onload = init();{% endcodeblock %}
