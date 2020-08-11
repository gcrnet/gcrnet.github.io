---
layout: post
title: Jekyll static site generator
feature-img: "https://i.imgur.com/4KpVtQF.png"
date: 11 August 2020
---
Jekyll is really useful for building static websites.
We can use a Jekyll theme and write our posts using markdown using less amount of HTML and CSS and have a awesome responsive good looking website.
If you are a developer and you love crerating websites and want to control every single aspect of the HTML and CSS on your site we can do all that with jekyll. 
Jekyll allows us to create our own themes and layouts etc... we can controll and configure the enire site.

In this tutorial we will go thgrough the basics.
We will know everything to get started with your first jekyll website from creating content to serving them on github pages.


1. [Installation](#install)
2. [Creating a site](#create)
3. [Front matter](#front)
4. [Installing themes](#themes)
5. [Layouts](#layouts)

<a name="install"></a>
## Installation
The Jekyll website provides [installation](https://jekyllrb.com/docs/installation/) instructions that cover all types of operating systems.

<a name="create"></a>
## Creating a site
For this tutorial purpose we will name our website as "test_blog".

open command promt and type - 'jekyll new test_blog' and it will create our new site for us.

![create](https://i.imgur.com/8Yaniqp.png)

Check the files and jekyll will create some default content for us.

![default_content](https://i.imgur.com/i0sydRw.png)

Once the site is created with the basic content we can host it.
We will see how to serve out site on local host.
we need to move to the directory of our site and open command promt and type - 'bundle exec jekyll serve'.
Jekyll will take all the peices of our website and serve them in our browser.

![jekyll-serve](https://i.imgur.com/us5KXsi.png)

As it serves in our local host server we can see that in our browser.

![localhost](https://i.imgur.com/onXxPaB.png)

Coming back to the files on our folder.
We have the root folder "test_blog"
In that we have "posts" floder.
This is the folder where we store all our blog posts.
Then we have "site" folder.
This is basically the final output of our website.
Next important file is "config.yaml". It is essentially the settings of your site. It contains the basic attributes of your site.
"Gemfile" is used to store all the dependecies for the website. 
Rest of the files are just default basic parts of our website.

<a name="front"></a>
## Front matter
In this section we will see about the front matter in jekyll.
Front matter is the information that we store about the pages of our site. All the pages in our site wil have front matter.
Front matter may contain information like Title, Name of the author etc... 

For the default post in our test_blog website has content and front matter.

![front_matter](https://i.imgur.com/kopLTwb.png)

We can see some special information at the top of our post which is different from the content, That is called front matter.
Front matter can be written in two languages, YAML or JSON. (Key value pairs.)

<a name="themes"></a>
## Installing themes
By default we will be having a minima theme for our jekyll website.
If we want a different theme for our website, there are a lot of themes(free) available on the internet.
You can select a theme that you like and copy the name of the theme in the gemfile and intall it with the ocmmand "bundle install".
Then change the theme value in 'config.yaml' file.
Now restart the server and you will see the changes in your website.

Website for free themes:
 * [Jekyll themes](http://jekyllthemes.org/)
 * [Free jekyll themes](https://jekyll-themes.com/free/)

You can find many other good websites on the internet.

<a name="layouts"></a>
## Layouts
Layouts are skeletons of HTML code used to define look and feel of different type of pages or your entire site.

We can see our default test_blog website is looking good and wedid not modify anything yet.
By default jekyll will provide us layouts for our pages.
We can see the front matter and it specifies a attribute in each post or page we write.
If you want to create your own layout.
1. come to the root directory and create "layouts folder".
2. create a html file of your own and you can start making your own layout.
![layouts](https://i.imgur.com/qyDBIPp.png)
After you create you own layout, you can change the layout to the one you just created and it will show up the changes.
