---
layout: post
title: HTML5 Canvas Particle System (pt. 2)
categories: css javascript tutorial example
---

This is a Part 2 of a tutorial post [HTML5 Canvas Particles System (Pt. 1)](http://lili2311.github.io/blog/2014/07/22/Canvas-Particles/). In this tutorial I will cover:

1. Initialising Canvas (covered in [Pt. 1](http://lili2311.github.io/blog/2014/07/22/Canvas-Particles/))
2. Drawing circles in Canvas
3. Simple animation for particle movement using `SetInterval()`
4. Improving the code using `RequestAnimationFrame()`

####Drawing Circles in Canvas

Now that we have initialized a blank canvas, we can begin to draw in it. For our particle system we will need to draw the individual "particles", each one will be drawn as a circle. In order to draw a circle in Canvas we need to first get the canvas element using `GetElementById` and set the width and height to the browser window, then specify that we are working in 2D using `getContext`:
{% codeblock lang:javascript %}var c = document.getElementById("myCanvas");
var ctx = c.getContext("2d");
c.width = window.innerWidth;
c.height = window.innerHeight;{% endcodeblock %}
We can now define our `draw()` function and then call it:
{% codeblock lang:javascript %}function draw() {
	x = 90; // x co-ordinate
	y = 70; // y co-ordinate
	r = 60; // radius of a circle
	c = "#ef5da1"; // fill colour

	ctx.beginPath();
	ctx.arc( x, y, r, 0, 6);
	ctx.fillStyle = c;
	ctx.fill(); 
}
draw();
{% endcodeblock %}

And here is our first circle:

![](http://www.lilianakastilio.co.uk/images/canvas-particle-circle.png)


We can now create an array of particles for us to draw. First let's initialise some variables that we will need available globally:
{% codeblock lang:javascript %}var ps = [];// initialize an empty particle array
var MAX_NUM = 500; // this is the maximum number of particles we want to generate and draw
var colors = [ '#69D2E7', '#A7DBD8', '#E0E4CC', '#F38630', '#FA6900', '#FF4E50', '#F9D423' ]; // this is an array of colour that the particles can be{% endcodeblock %}

In order to generate all particles we will create a `spawn()` function and call it. Here we are populating the empty `ps[]` array with randomly generated values, within the given bound (in this case the width and height of the browser window):
{% codeblock lang:javascript %}function spawn() { 
	for(var i = 0; ps.length < MAX_NUM; i++) {
		ps[i] = { x: Math.random() * window.innerWidth,
		          y: Math.random() * window.innerHeight,
		          r: Math.random() * 5,
		          c: colors[Math.floor(Math.random() * colors.length)]
		        };                  
		}
}
spawn();{% endcodeblock %}

We now need to modify our `draw()` function to loop over all the particles and draw them:
{% codeblock lang:javascript %}function draw() {
	for(var i=0; i < ps.length; i++) {
	ctx.beginPath();
		ctx.arc( ps[i].x, ps[i].y, ps[i].r, 0, 6);
		ctx.fillStyle = ps[i].c;
		ctx.fill(); 
	}
}
draw();{% endcodeblock %}

If we run the code now, we should see something like this:

![](http://www.lilianakastilio.co.uk/images/canvas-particle-multiple.jpg)

This is the full script:
{% codeblock lang:javascript %}var ps = [];
var MAX_NUM = 500;
var colors = [ '#69D2E7', '#A7DBD8', '#E0E4CC', '#F38630', '#FA6900', '#FF4E50', '#F9D423' ];

var c=document.getElementById("myCanvas");
var ctx=c.getContext("2d");
c.width = window.innerWidth;
c.height = window.innerHeight;

// create the particles
function spawn() {
  for(var i=0; ps.length < MAX_NUM; i++) {
    ps[i] = { x: Math.random()*window.innerWidth,
              y: Math.random()*window.innerHeight,
              r: Math.random()*5,
              c: colors[Math.floor(Math.random()*colors.length)]
            };                  
   }
}
function draw() {
	for(var i=0; i < ps.length; i++) {
	ctx.beginPath();
		ctx.arc( ps[i].x, ps[i].y, ps[i].r, 0, 6);
		ctx.fillStyle = ps[i].c;
		ctx.fill(); 
	}
}
spawn();
draw();{% endcodeblock %}

####Simple Animation Using SetInterval()

We are now ready to animate our particle system. We will need to write an `update()` function, which will update the `x` and `y` values of each particle on each frame. On each update we also need to reset the `width` and `height` to clear the canvas (Tip: remove this to see what happens if the canvas is not cleared):
{% codeblock lang:javascript %}function update() {
	c.width = window.innerWidth;
	c.height = window.innerHeight;
    for(var i=0; i < ps.length; i++) {
        ps[i].y += 1;
        ps[i].x += -1 + (Math.random() * 3);
    }
}{% endcodeblock %}

We can now call this function on each frame using `SetInterval()` and then draw the particles with the updated co-ordinates:
{% codeblock lang:javascript %}setInterval(function() {
  update();
  draw();
}, 30);{% endcodeblock %}

You may have noticed that the particles simply dissapear once they have reached the bottom of the brower window, if you would liek to animation to keep on running we could reset the `x` and `y` of each aprticles if it leaves the screen to start all over again:
{% codeblock lang:javascript %}function reset() {
    //reset the x and y coordinates if a particle leaves the canvas
    for(var i=0; i < ps.length; i++) {
        //reset if y or coordinate has left the canvas
        if(ps[i].y > c.height) {
            ps[i].y = Math.random()*window.innerHeight;
            ps[i].color = colors[Math.floor(Math.random() * colors.length)];
        }
        //reset if x or coordinate has left the canvas
        if(ps[i].x > c.width || ps[i].x < 0){
          ps[i].x = Math.random()*window.innerWidth;
          ps[i].color = colors[Math.floor(Math.random() * colors.length)];
        }
    }
}
{% endcodeblock %}
Now we have to call this new `reset()` function on each frame:
{% codeblock lang:javascript %}setInterval(function() {
  update();
  draw();
  reset();
}, 30);{% endcodeblock %}

Now you have a never ending animation of colourful particles slowly making their way down the screen. The full `particles.js` can be found here:
{% codeblock lang:javascript %}// declare vars
var ps = [];
var MAX_NUM = 500;
var colors = [ '#69D2E7', '#A7DBD8', '#E0E4CC', '#F38630', '#FA6900', '#FF4E50', '#F9D423' ];

var c=document.getElementById("myCanvas");
var ctx=c.getContext("2d");
c.width = window.innerWidth;
c.height = window.innerHeight;

spawn();

//create the particles
function spawn() {
  for(var i=0; ps.length < MAX_NUM; i++) {
    ps[i] = { x: Math.random()*window.innerWidth,
              y: Math.random()*window.innerHeight,
              r: Math.random()*5,
              c: colors[Math.floor(Math.random()*colors.length)]
            };                  
   }
}

function update() {
    c.width = window.innerWidth;
    c.height = window.innerHeight;
    for(var i=0; i < ps.length; i++) {
        ps[i].y += 1 ;
        ps[i].x += -1 + (Math.random() * 3);
        //ps[i].r = Math.random()*5;
    }
}

function reset() {
    //reset the x and y coordinates if leaves the canvas
    for(var i=0; i < ps.length; i++) {
        //reset if y or coordinate has left the canvas
        if(ps[i].y > c.height) {
            ps[i].y = Math.random()*window.innerHeight;
            ps[i].color = colors[Math.floor(Math.random() * colors.length)];
        }
        //reset if x or coordinate has left the canvas
        if(ps[i].x > c.width || ps[i].x < 0){
          ps[i].x = Math.random()*window.innerWidth;
          ps[i].color = colors[Math.floor(Math.random() * colors.length)];
        }
    }
}
 
function draw() {
  for(var i=0; i < ps.length; i++) {
    ctx.beginPath();
		ctx.arc( ps[i].x, ps[i].y, ps[i].r, 0, 6);
		ctx.fillStyle = ps[i].c;
		ctx.fill(); 
  }
}

setInterval(function() {
  update();
  draw();
  reset();
}, 30);{% endcodeblock %}

Live demo [here](http://www.lilianakastilio.co.uk/particles/particles.html).

In Pt.3, I will cover how we can improve our animation using `RequestAnimationFrame()`(Pt.3 can be found [here]()).
