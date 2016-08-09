---
layout: post
title: "Frontend automation with Grunt"
comments: true
categories: grunt frontend
---
####1. What is Grunt?

[Grunt](http:/gruntjs.com/) is a JavaScript task runner. Grunt lets you automate tasks like HTML minification, copying files, compiling CSS, deploying to AWS etc. 

####2. Download Node.js
Grunt and Grunt plugins are installed and managed via [npm](https://npmjs.org/) the [Node.js package manager](https://nodejs.org/en/).
First of all if you will need to download [Node.js](https://nodejs.org/en/download/) (npm will be installed with it).

####3. Basic Command Line Commands 

If you have not used command line terminal before you here are some basic commands: 

`ls`

**Description**: Lists the names of the files in the working directory. 
For more complete information use `ls –alF`

`cd directoryname`

**Description**: Changes the working directory to the one you named.

`cd ..`

**Description**: Brings you up one directory level.

`cd`

**Description**: Returns you to your home directory.

`pwd`

**Description**: Displays the pathname of the current directory.

`mkdir newdirectoryname`

**Description**: Makes a new directory

####4. Install Grunt

1. Open your preferred terminal or install [iTerm](https://www.iterm2.com/). 
2. Install Grunt **globally**: instructions below will install grunt client globally on your machine, if you already have Grunt installed skip this step. For a more detailed explanation see the official [documentation](http://gruntjs.com/getting-started). 
4. Install Grunt **locally**: Now we will install Grunt locally specifically for this project. Go to your project folder. Replace the path after `cd` with the path to your folder: 
{% codeblock lang:bash %}
cd Documents/workshop/
{% endcodeblock %}
In the terminal type out the below command to get to the project folder (if you have saved the workshop folder elsewhere adjust the path):{% codeblock lang:bash %}
npm install grunt --save-dev
{% endcodeblock %}

####5. Configure
To configure the project, within your project folder type `npm init` in the terminal and follow the instructions:
![](http://www.lilianakastilio.co.uk/images/automation-with-grunt/npminit.png)

####6. Grunt AWS Plugin
We will now install Grunt AWS Plugin. Grunt uses different plugins to perform certain tasks, in order to deploy to Amazon S3 we will use the [grunt-aws-s3 plugin](https://github.com/MathieuLoutre/grunt-aws-s3).

In your project folder we can install this using the command below: {% codeblock lang:bash %}
npm install grunt-aws-s3 --save-dev
{% endcodeblock %}

We now have the plugin installed and we can configure grunt to use this task to deploy our project without having to manually upload the files every time.

In order for us to use this plugin  and deploy to S3 in the command line we need to create a file called `s3settings.json`, here we will keep all the login details and bucket information. **This file MUST be kept secret, do not commit it to github or any other version control system. It should be excluded in `.gitignore`file if you are using git. It is important to take care as if these details are made public your account may be accessed and used by someone else, leaving you with a bill to pay**:

![](http://www.lilianakastilio.co.uk/images/automation-with-grunt/s3json.png)

The `key` and `secret` are available in the user credentials file you downloaded when [creating an IAM user](http://blog.lilianakastilio.co.uk/blog/2016/03/05/create-new-iam-users-and-permissions-in-aws/). Bucket must be exactly what you called the bucket on Amazon S3 and the same for region.

The second file we need to create is `Gruntfile.js` this is a default file Grunt will look for locally within the project folder. Here is where we configure the tasks.

Using your text editor or command line, create a new file within the workshop folder called `Gruntfile.js`, the content of it should be the following:
{% codeblock lang:js %}module.exports = function(grunt) {
grunt.loadNpmTasks('grunt-aws-s3');
 
grunt.initConfig({
	pkg: grunt.file.readJSON('package.json'),
	s3settings: grunt.file.readJSON('s3settings.json'),
		aws_s3: {
		    options: {
		    	accessKeyId: '<%= s3settings.key %>',
		    	secretAccessKey: '<%= s3settings.secret %>',
		    	region: '<%= s3settings.region %>',
		    	uploadConcurrency: 5, 
		        downloadConcurrency: 5
	    },
	    live: {
	        options: {
	            bucket: '<%= s3settings.bucket %>',
	            differential: true //Only uploads the files that have changed
	        },
	        files: [
	            {expand: true, cwd: 'deploy/', src: ['**'], dest: ''},
	            ]
	        },
	    });
	grunt.registerTask('deploy', ['aws_s3:live']);
};
{% endcodeblock %}

[Full code to copy is here.](http://pastebin.com/m3cK4EcC)

Here we have configured the plugin to upload to Amazon S3 all files in the folder deploy, so we would now have to create this folder within the project and copy any files we want uploaded.

We have also created a task called `deploy` which can be run in command line within the project folder to upload all files within deploy folder to Amazon S3, to the bucket specified in the `s3settings.json` file.

####7. Use Grunt to deploy to S3
Go to the project folder in the terminal. You can now run the deploy command by typing: {% codeblock lang:bash %}grunt deploy{% endcodeblock %}

And we are done!






