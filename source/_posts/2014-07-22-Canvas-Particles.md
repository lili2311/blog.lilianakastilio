---
layout: post
title: HTML5 Canvas Particles System (pt. 1) 
tags: [css,javascript,tutorial,example]
---


Learning to make a simple particle system using HTML5 Canvas and Javascript. 

In this tutorial I will cover:

1. Initialising Canvas
2. Drawing circles
3. Simple animation for particle movement using `SetInterval()`
4. Improving the code using `RequestAnimationFrame()`

####Initialising Canvas

Introduced in HTML5, the HTML  ```<canvas>```  element can be used to draw graphics via scripting in JavaScript. The ``` <canvas>```  element isn't supported in some older browsers, but is supported in recent versions of all major browsers. More information can be found here: [http://caniuse.com/#feat=canvas](http://caniuse.com/#feat=canvas). ```<canvas>``` element requires the closing tag, like so:
{% codeblock lang:html %}<canvas id="myCanvas"></canvas>{% endcodeblock %}
This creates a blank canvas for us to use. You can set the with and height at this point:
{% codeblock lang:html %}<canvas id="myCanvas" width="500" height="300"> JavaScript Particles Canvas </canvas>{% endcodeblock %}
    
If not specified, **width** defaults to **300px** and **height** defaults to **150px**.

Some older versions of browsers do not support the ```<canvas>``` element, we can provide fallback content. We just provide alternate content inside the ```<canvas>``` element. Browsers which don't support ```<canvas>``` will ignore the container and render the fallback content inside it, otherwise they will render the canvas normally:
{% codeblock lang:html %}<canvas id="myCanvas" width="500" height="300"></canvas>{% endcodeblock %}

You can even include a different element inside the canvas element:
{% codeblock lang:html %}<canvas id="myCanvas" width="500" height="300"><img src="img/example.png" width="500" height="300" alt="Example Image"></canvas>{% endcodeblock %}
        

We have now initialized a blank canvas and are ready to draw something. I will cover drawing circles in the [next blog post](http://lili2311.github.io/blog/2014/11/16/HTML5-Canvas-Particle-System-pt2/).
