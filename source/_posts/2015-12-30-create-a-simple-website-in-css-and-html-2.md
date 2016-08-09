---
layout: post
title: "Part 2: Create a Simple Website in CSS/HTML and deploy to Amazon S3"
comments: true
categories: css tutorial
---

This is Part 2 of a tutorial post [Create a Simple Website in CSS/HTML and deploy to Amazon S3](http://blog.lilianakastilio.co.uk/blog/2015/12/03/create-a-simple-website-in-css-and-html-and-deploy-to-amazon-s3/), it is aimed at a completele beginner. 

In this tutorial we will briefly cover:

1. What is CSS?
2. CSS Basics
3. Create a Stylesheet
4. Link HTML and CSS
5. Basic CSS Properties
6. CSS Exercises

####1. What is CSS?
**Cascading Style Sheets (CSS)** is a style sheet language used for describing what the html elements should “look like”. It is used to describe whether an html element should be of certain height, width, if the text should be bold, text colour etc. We will try this shortly.

<!-- CSS allows us to separate the document structure from document appearance, it also allows certain styles to be re-used. For example if all buttons should look the same, it allows us to style them once and not repeat ourselves
 -->
####2. CSS Basics
This is a **rule**:
{% codeblock lang:css %}h1 {
	color: red;
}
{% endcodeblock %}

* This rule starts with `h1`, which is a *selector*.
* The part inside the curly braces is the *declaration*.
* `color` is a *property*.
* `red` is a *value*.
* `color: red;`  is a *property-value pair*.
* The `;` after the *property-value pair* separates it from other *property-value pairs* in the same *rule*, for example:

{% codeblock lang:css %}h1 {
	color: red;
	text-align: center;
}{% endcodeblock %}
We will refer to those definitions throughout this class.

####3. CSS Basics

When the browser reads the CSS file, it finds each *selector* and works out if it applies to any elements in the HTML.
If it does, it uses the *properties* within the matching rule.

A **style sheet** consists of a list of **rules**.
Each **rule** or **rule-set** consists of one or more selectors.
**Selectors** allow you to SELECT all elements that match:

* a certain tag name e.g. `<h1>`
* a certain element inside another element e.g. all `<li>` within a `<ul>`

<!-- in addition to tag names, you can use attribute values in selectors and for example select all items that are `h1` but have a class `.red` (More info on classes later)
 -->
####4. Create a Stylesheet

1. [Install Sublime](http://www.sublimetext.com/) or use your preferred text editor
2. Create a new file in the same folder as the `index.html` and name it `style.css`
3. Type out the code below and save in in your `style.css` file:
{% codeblock lang:css %}
h1 {
	color: red;
	text-align: center;
}{% endcodeblock %}

Here you created a rule that says:
*All `h1` elements have the following properties:  text alignment is `center` & the text colour is `red`.*
	
**Exercise:** Now use the example above to do the same for `<p>`. Clue: create a new rule and replace `h1` with `p`.


####5. Link HTML and CSS

Now that we have our first stylesheet, we can tell the html document `index.html` to use the stylesheet `style.css` so that the browser knows what the page should look like.

1. Add the following line in your `index.html` file underneath the `<title>` tag:{% codeblock lang:html %}
<link rel="stylesheet" href="style.css">
{% endcodeblock %}
2. Reload the file in the browser or open it again: Open your web browser, then press `Ctrl + O` (Windows) or `Cmd + O` (Mac) to open the file we have just updated. You should see “Hello World” and the text you added in the paragraph with the added style.

####6. Basic CSS Properties    

`color`

* **Description**: this is the text colour, this is used to style elements that have text e.g. `h1`, `p`, `h2`.
* **Example**: `color: white;`
* **More Info**: [MDN: color](https://developer.mozilla.org/en/docs/Web/CSS/color)

`background-color`

* **Description**: this is used to define the background color of a particular element.
* **Example**: `background-color: blue;`
* **More Info**: [MDN: background-color](https://developer.mozilla.org/en/docs/Web/CSS/background-color)

`font-size`

* **Description**: this is used to set the size of a font in px or other units.
* **Example**: `font-size: 16px;`
* **More Info**: [CSS font size units](https://www.google.com/url?q=http://kyleschaeffer.com/development/css-font-size-em-vs-px-vs-pt-vs/&sa=D&usg=AFQjCNFv60g9JwR8d5c6QMP-e9IraqjfNA)

`background-image`

* **Description**: this is used to set an image as a background of an element.
* **Example**: `background-image: url(http://examplelink.com);`
* **More Info**: [CSS-tricks: background-image](https://css-tricks.com/almanac/properties/b/background-image/)

`text-align`

* **Description**: this is used to align text.
* **Example**: `text-align: left;`
* **More Info**: [Quirksmode: text-align](http://www.quirksmode.org/css/text/textalign.html)

`padding`

* **Description**: sets the padding of the element. See the **Box Model picture** below for
an explanation of what padding is and how it will affect the look of the element.
* **Example**: `padding: 10px 10px 10px 10px;` or `padding: 10px;`
* **More Info**: [MDN: padding ](https://developer.mozilla.org/en/docs/Web/CSS/padding)

`margin`

* **Description**: this is used to set the margin of the element. See the **Box Model 
picture** below for an explanation of what padding is and how it will affect the
look of the element.
* **Example**: `margin: 10px;`
* **More Info**: [MDN: margin](https://developer.mozilla.org/en/docs/Web/CSS/margin)

#####6.1 CSS Box Model

In a document, each element is represented as a rectangular box.
This model describes the content of the space taken by an element. Each box has four edges:

1. `margin` edge
2. `border` edge
3. `padding` edge
4. `content` edge (in blue)

![](http://www.lilianakastilio.co.uk/images/2015-12-03-create-a-simple-website-in-css-and-html-and-deploy-to-amazon-s3/CSSBoxModel.png)

You can read more about [CSS Box Model here](https://www.google.com/url?q=https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Box_Model/Introduction_to_the_CSS_box_model%23padding&sa=D&usg=AFQjCNFnLGpiKkdw0tpeCMcxLd6Zd5sW0A).

####5. CSS Exercises

We can add more to the `style.css` at this stage or later, [here is a list of CSS properties available](https://www.google.com/url?q=https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Properties_Reference&sa=D&usg=AFQjCNGs3Xcq6WpTsShEmATiE4-XHERnug).

1. Try out all the properties from the **Basic CSS Properties** section and see what they all do.
2. You can also style the `<body>` element, try setting a background image on the <body> element and see what that does.
3. Make an image to also be a link, ie make the image clickable that will take you to a different website. Tip: you can add some elements inside of other elements,try and add an `img` within the `a`.
4. Align left or center all the text on the page.
