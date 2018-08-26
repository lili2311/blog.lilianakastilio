---
layout: post
title: "Stop wasting time logging into GitHub on command line every time you push: just set up SSH keys"
date: 2016-10-30 23:54:37 +0000
comments: true
categories: git ssh
---

##1. Does GitHub always ask you for your password? There is a fix, read on :)

If you recently started using Git & Github in your workflow it is likely you are sick and tired of constantly having to type in your username and password every single time you want to push some chnages! Well that ends today as in this blog post I will show you how to tell Github to trust your laptop and just let you get on with coding without any fuss of logging in all the time.

In order for this to work we will use something called SSH keys.

##2. What are SSH keys?

SSH keys are a means of identifyng yourself to a server without having to type in your username and password every time. It can be though of as a passwordless login. Instead of a user name and password the a pair of keys is used that is exchanged between your laptop and the server. They keys live on your laptop and on the other side, this way every time you talk to that server it will realise that you are already knowkn to it and who you are.


##3. Do you already have SSH keys?

Before we make a new key, lets check if you have lying around already.

### Windows

In command promt type in:
{% codeblock lang:bash %}cd %userprofile%/.ssh{% endcodeblock %}

Now lets see if there is a key in there:
{% codeblock lang:bash %}dir id_*{% endcodeblock %}

If you see and error something like "No such file or directory" then you don't have a key and need to make one. Next section describes hwo to do this.

### Mac & Linux
Open your preffered terminal and run the command below:

{% codeblock lang:bash %}ls -al ~/.ssh{% endcodeblock %}

This will list all the files currently present in the `~/.ssh` directory, which is a special directory where all keys are stored by default. The filenames to look out for are:

1. id_rsa.pub
2. id_rsa
3. id_dsa.pub
4. id_ecdsa.pub
5. id_ed25519.pub

Check the content of the file that looks similar to the example above by using the `cat` command:

{% codeblock lang:bash %}cat ~/.ssh/id_rsa.pub{% endcodeblock %}

There will be a whole lot ot stuff in that file including your email.

If you did not find anything in there, not to worry we will make a new SHH key!


##4. Generate a new SSH key.

So if you found no keys form steps before then we should make one. Lets go back to the terminal and run the command that will generate us a new key:

{% codeblock lang:bash %}ssh-keygen -t rsa -C "your-email@example.com"{% endcodeblock %}

1. Just press Enter when prompted for a filename
2. Create and enter a passphrase as requested.
3. Tada you now have a shiny new key ready to be used.

Note that the ssh-keygen command is only available if you have already installed Git (for Windows that would be Git with Git Bash).

##5. Adding a new SSH key to your GitHub account.

We now need to share the new key with Github in order to enjoy passwordless login when pushing code:

1. Log in to your [GitHub account](https://github.com/)
2. Click on your profile photo (in the top right corner) → "Settings"
3. In the sidebar click on "SSH and GPG keys" → "New SSH Key"
4. Give it a title/name (perhaps this is the key for you work laptop)
5. You now need to copy and paste the entirety of the key into here. So all the text your saw with your email that was generated during the previous step all of that is a key. If you had a key already, simply open the file and copy paste the entire contents into here.
6. Save!

##5. Try it out!

You can now go back to your project and try pushing some code, you should no longer be prompted for the password and username every time.



