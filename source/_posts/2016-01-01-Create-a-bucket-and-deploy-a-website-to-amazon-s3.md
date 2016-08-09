---
layout: post
title: "Part 3: Create a Bucket and Deploy a Website to Amazon S3"
comments: true
categories: tutorial aws
---

This is Part 3 of a tutorial post [Create a Simple Website in CSS/HTML and deploy to Amazon S3](http://blog.lilianakastilio.co.uk/blog/2015/12/03/create-a-simple-website-in-css-and-html-and-deploy-to-amazon-s3), it is aimed at a completele beginner. 

**Note:**  Here you can look over [Part 1: HTML](http://blog.lilianakastilio.co.uk/blog/2015/12/03/create-a-simple-website-in-css-and-html-and-deploy-to-amazon-s3/) and [Part 2: CSS](http://blog.lilianakastilio.co.uk/blog/2015/12/30/create-a-simple-website-in-css-and-html-2/) of this tutorial.

In this tutorial we will cover:

1. Create a free account on Amazon S3
2. Creating a bucket on Amazon S3
3. Uploading your website to Amazon S3


####1. Create a free account on Amazon S3
Amazon has a free tier which will be enough for most small websites.

**1.** Go to [Amazon S3](https://aws.amazon.com/s3/)

**2.** Click on “Try Amazon S3 for Free”:

![](http://www.lilianakastilio.co.uk/images/2015-12-03-create-a-simple-website-in-css-and-html-and-deploy-to-amazon-s3/amazonsignup1.png)

**3.** Enter your email address or phone number. Then select  “I am  New User” and click “Sign in using our secure server”:

![](http://www.lilianakastilio.co.uk/images/2015-12-03-create-a-simple-website-in-css-and-html-and-deploy-to-amazon-s3/amazonsignup2.png)

**4.** Fill out required info:

![](http://www.lilianakastilio.co.uk/images/2015-12-03-create-a-simple-website-in-css-and-html-and-deploy-to-amazon-s3/amazonsignup3.png)

**5.**  Fill out credit card info

**6.**  Confirm your identity via a call:

![](http://www.lilianakastilio.co.uk/images/2015-12-03-create-a-simple-website-in-css-and-html-and-deploy-to-amazon-s3/amazonsignup4.png)

####2. Creating a bucket on Amazon S3

**1.** Sign in to the [Amazon console](https://aws.amazon.com/s3/)

![](http://www.lilianakastilio.co.uk/images/2015-12-03-create-a-simple-website-in-css-and-html-and-deploy-to-amazon-s3/amazonconsole-s3.png)

**2.** Click on **S3**
![](http://www.lilianakastilio.co.uk/images/2015-12-03-create-a-simple-website-in-css-and-html-and-deploy-to-amazon-s3/s3-signed-in.png)

**3.** Click "Create a new bucket"
![](http://www.lilianakastilio.co.uk/images/2015-12-03-create-a-simple-website-in-css-and-html-and-deploy-to-amazon-s3/create-new-bucket.png)

**4.** Click "Create a new bucket"
![](http://www.lilianakastilio.co.uk/images/2015-12-03-create-a-simple-website-in-css-and-html-and-deploy-to-amazon-s3/create-new-bucket.png)

**3.** Fill out the bucket name (example yourname.com)

####3. Uploading your website to Amazon S3

**1.** Click into the bucket name you have just created

**2.** Select “Actions” →  “Upload”
![](http://www.lilianakastilio.co.uk/images/2015-12-03-create-a-simple-website-in-css-and-html-and-deploy-to-amazon-s3/upload.png)

**3.** Click “Set Details” → “Set permissions”

**4.** Tick “Make everything public”
![](http://www.lilianakastilio.co.uk/images/2015-12-03-create-a-simple-website-in-css-and-html-and-deploy-to-amazon-s3/makepublic.png)

**5.** Click “Start Upload”

**6.** Select the file index.html and click “Properties”

**7.** Click on the link
![](http://www.lilianakastilio.co.uk/images/2015-12-03-create-a-simple-website-in-css-and-html-and-deploy-to-amazon-s3/index.png)

**8.** Thats it! Your website is now live and accessible online via this link at any time.

If you would like to learn how to automate this deploy and make it easier for continuous development watch out for the next blog post where I will talk about using [Grunt](http://gruntjs.com/).


