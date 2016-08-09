---
layout: post
title: "Part 4: Create new IAM users and permissions in AWS"
comments: true
categories: aws iam tutorial
---
This is **Part 4** of a tutorial post [Create a Simple Website in CSS/HTML and deploy to Amazon S3](http://blog.lilianakastilio.co.uk/blog/2015/12/03/create-a-simple-website-in-css-and-html-and-deploy-to-amazon-s3/).

**Note:**  Here you can look over [Part 1: HTML](http://blog.lilianakastilio.co.uk/blog/2015/12/03/create-a-simple-website-in-css-and-html-and-deploy-to-amazon-s3/), [Part 2: CSS](http://blog.lilianakastilio.co.uk/blog/2015/12/30/create-a-simple-website-in-css-and-html-2/) and [Part 3: Deploy to AWS](http://blog.lilianakastilio.co.uk/blog/2016/01/01/Create-a-bucket-and-deploy-a-website-to-amazon-s3/) of this tutorial.


####1. Create a new User

1. Sign in to the [AWS Amazon console](https://console.aws.amazon.com/console/home?nc2=h_m_mc)
2. Click on **Identity & Access Management**
![](http://www.lilianakastilio.co.uk/images/2015-12-03-create-a-simple-website-in-css-and-html-and-deploy-to-amazon-s3/iam.png)
3. Click on **User** on the left hand-side menu  
![](http://www.lilianakastilio.co.uk/images/2015-12-03-create-a-simple-website-in-css-and-html-and-deploy-to-amazon-s3/user.png)
4. Click **Create New User**
![](http://www.lilianakastilio.co.uk/images/2015-12-03-create-a-simple-website-in-css-and-html-and-deploy-to-amazon-s3/create-new-user.png)
5. Enter username `testuser`
![](http://www.lilianakastilio.co.uk/images/2015-12-03-create-a-simple-website-in-css-and-html-and-deploy-to-amazon-s3/new-user-name.png)
6. Click **Create**
7. Download the credentials. These will include User Name, Access Key Id, Secret Access Key. Keep these secret as they are tied to your account and can be used for malicious purposes if not kept safely. Remember that your account is tied to your credit card.           

####2. Set user permissions

1. You should now see your user created in the user dashboard.
2. Click your newly created user `testuser`
3. Click on **Permissions → Attach Policy** 

![](http://www.lilianakastilio.co.uk/images/2015-12-03-create-a-simple-website-in-css-and-html-and-deploy-to-amazon-s3/attach-policy.png)

4. Select **AmazonS3FullAccess → Attach Policy**:
![](http://www.lilianakastilio.co.uk/images/2015-12-03-create-a-simple-website-in-css-and-html-and-deploy-to-amazon-s3/amazons3fullaccess.png)
5. Done!
![](http://www.lilianakastilio.co.uk/images/2015-12-03-create-a-simple-website-in-css-and-html-and-deploy-to-amazon-s3/user-complete.png)


