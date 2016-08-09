---
layout: post
title: HTML5 Canvas Particle System (pt. 3)
categories: css javascript tutorial
---
This is a Part 3 of a tutorial post [HTML5 Canvas Particles System (Pt. 1)](http://lili2311.github.io/blog/2014/07/22/Canvas-Particles/). In this tutorial I will cover:

1. Initialising Canvas (covered in [Pt. 1](http://lili2311.github.io/blog/2014/07/22/Canvas-Particles/))
2. Drawing circles in Canvas (covered in [Pt. 2](http://lili2311.github.io/blog/2014/11/16/HTML5-Canvas-Particle-System-pt2/))
3. Simple animation for particle movement using `SetInterval()` (covered in [Pt. 2](http://lili2311.github.io/blog/2014/11/16/HTML5-Canvas-Particle-System-pt2/))
4. Improving the code using `RequestAnimationFrame()`

####Using RequestAnimationFrame() instead of SetInterval()

Instead of using `SetInterval()` we can animate only when we need to using `RequestAnimationFrame()`. This helps improve performance as we re-draw only when something has changed. We can define to call `spawn()`, `draw()` and `update()` on load, after which we would have to modify the `update()` method to trigger the `RequestAnimationFrame()`.

Here is what we are using instead of `SetInterval()`:
{% codeblock lang:javascript %}window.requestAnimFrame = window.requestAnimationFrame ||
                          window.webkitRequestAnimationFrame ||
                          window.mozRequestAnimationFrame ||
                          window.oRequestAnimationFrame ||
                          window.msRequestAnimationFrame ||
                          function(e){
                            window.setTimeout(e,1e3)
                          };{% endcodeblock %}

And adding an on load function:

{% codeblock lang:javascript %}// We should create, draw and start updating on load. 
window.onload = function() {
    c.width = c.width;
    c.height = c.height;
    spawn();
    draw();
    update();
}{% endcodeblock %}


We can now modify `update()` to look like this which now:

{% codeblock lang:javascript %}function update() {
    reset();
    c.width = window.innerWidth;
    c.height = window.innerHeight;
    for(var i=0; i < ps.length; i++) {
        ps[i].y += 1 ;
        ps[i].x += -1 + (Math.random() * 3);
        //ps[i].r = Math.random()*5;
    }
    draw();
    window.setTimeout(requestAnimFrame(update),1e3);

}{% endcodeblock %}

And that is it!



