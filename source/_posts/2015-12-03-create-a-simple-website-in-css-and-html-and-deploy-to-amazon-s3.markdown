---
layout: post
title: "Part 1: Create a Simple Website in CSS/HTML and deploy to Amazon S3"
comments: true
categories: css html tutorial
---

This is Part 1 of a tutorial post [Create a Simple Website in CSS/HTML and deploy to Amazon S3](http://blog.lilianakastilio.co.uk/blog/2015/12/03/create-a-simple-website-in-css-and-html-and-deploy-to-amazon-s3/), it is aimed at a completele beginner. 

In this tutorial I will briefly cover:

1. What is HTML?
2. HTML Basics
3. Create a Simple HTML Page
4. What is HTML5 and how is it different?
5. HTML Exercisesb

####1. What is HTML?
**HTML - HyperText Markup Language** is the standard language used to create web pages. Web browsers can read HTML files and render them into visible web pages.
HTML documents are described by HTML tags, these are enclosed in angular brackets `<>`.
HTML tags can be considered to be “keywords” that the browser can understand and render/draw in the browser appropriately when viewing the page. 
Each browser has default ways of interpreting each element, these can later be “styled” to look how you prefer with the help of CSS, which will be explained a little further on.

####2. HTML Basics

We will create a very basic HTML page that will load and simply display “Hello World”. It will look like this:

{% codeblock lang:html %}<!DOCTYPE html>
<html>
    <head>
        <title>Page title goes here</title>
    </head>
    <body>
    	<h1>Hello World</h1>
    	<p>This is my first website!</p>
    </body>
</html>
{% endcodeblock %}

* The `DOCTYPE` is a declaration and tells the browser which 'language' we are talking in so it knows how to render it.
* The text between `<html>` and `</html>` describes an HTML document
* The text between `<head>` and `</head>` provides information about the document
* The text between `<title>` and `</title>` provides a title for the document
* The text between `<body>` and `</body>` describes the visible page content
* The text between `<h1>` and `</h1>` describes a heading
* The text between `<p>` and `</p>` describes a paragraph

####3. Create a Simple HTML Page

1. [Install Sublime](http://www.sublimetext.com/) or use your preferred text editor
2. Create a new folder in your `Documents` folder for this workshop, let’s call it `website`.
3. Now open the text editor and save an empty file called `index.html`, you can press `Cmd + S` (Mac) or `Ctrl + S` (WIndows)
	* `index.html` is a special name and this is a file that the server will look for by default when a certain url is requested (link e.g. `http://website.com`).
	* Each simple website is basically a “directory” of files, the `index.html` is the first file the web browser will access and from here you can specify how to reach other files via writing hyperlinks.
	* The default file can be configured to be called something else if required, but for the purpose of this workshop we will only concentrate on simple defaults.
4. Type out the code below: {% codeblock lang:html %}<!DOCTYPE html>
<html>
    <head>
        <title>Page title goes here</title>
    </head>
    <body>
    	<h1>Hello World</h1>
    	<p>This is my first website!</p>
    </body>
</html>
{% endcodeblock %} 
5. Open your web browser, then press `Ctrl + O` (Windows) or `Cmd + O` (Mac) to open the file we have just created. You should see “Hello World” and the text you added as the paragraph, something like this:

![](http://www.lilianakastilio.co.uk/images/2015-12-03-create-a-simple-website-in-css-and-html-and-deploy-to-amazon-s3/preview.png)


####4. What is HTML5 and how is it different?


`HTML5` is simply a newer version that is supported by most  modern browsers. HTML5 introduced some more awesome elements/tags we can use: such as `<canvas>`, `<video>`, `<audio>`, `<footer>` and many more to bring the HTML language more in-line with modern times. 

####5. HTML Exercises

We can add more to the page at this stage or later, [here is a list](http://www.htmldog.com/references/html/tags/) of `html` and new `html5` tags you can use.

1. Add an image `<img>`:
	* Type out the following and modify the `src` to point to an image you like: 
	{% codeblock lang:html %}
	<img src="https://www.example.com/image.png " alt="Image description">{% endcodeblock %}
	* `width="100"` and  `height="90"` are optional, play around with the numbers.
	* [Read more](http://www.htmldog.com/references/html/tags/img/) about image `<img>` tag and it's use.
2. Add a link `<a>` to your favourite website:
	* Type out the following and modify it to link to point your favourite website:
	{% codeblock lang:html %}
	<a href="https://www.example.com ">Link Text</a>{% endcodeblock %}
	* [Read more](http://www.w3schools.com/html/html_links.asp) about link `<a>` tag and it's use.
3. Add a footer `<footer>`. These usually sit at the bottom of the page, but sometimes have to be styled to stay at the bottom if there is not enough content to fill the page:
	* Type out the following and modify it to say anything you want:
	{% codeblock lang:html %}
	<footer> This is a footer </footer>{% endcodeblock %}
	4. Now try to add a link within the footer to point to a url of your choice, e.g. http://google.com
	* [Read more about footer `footer` tag and it's use](http://www.htmldog.com/references/html/tags/footer/)
5. Add a comment, which says `“This is my first website!”`:
	* Have a look at the example below and modify it as needed:
	{% codeblock lang:html %}
	<!-- Comment text, this will not be visible on the page -->{% endcodeblock %}	* [Read more about comments](http://www.tutorialspoint.com/html/html_comments.htm)
6. Add an unordered list of 3 things you love (use previous examples to get the format right):
	* Unordered list is started using the tag `<ul>` and closed using `</ul>`
	* Within the list declaration mentioned above you can add in list items, these are defined by: `<li>` `</li>`
	* You can have as many list items in the unordered list as you want
	* Within each item you can add other elements, such as: paragraph, link, images, another list.
	* Play around with this one, it is very useful especially for menus
	* [Read more about unordered list `ul` tag and it's use](http://www.htmldog.com/references/html/tags/ul/)

**Further reading and things to try:**

* [Mozilla: HTML Tags](https://developer.mozilla.org/en-US/Learn/HTML/HTML_tags)
* [Codeacademy: Web Beginner](https://www.codecademy.com/courses/web-beginner-en-HZA3b/0/1?curriculum_id=50579fb998b470000202dc8b)
* [Tutorialspoint: HTML](http://www.tutorialspoint.com/html/)
* [Codepen](http://codepen.io/pen/ )


