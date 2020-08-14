---
layout: post
title: Jekyll static site generator
feature-img: "https://i.imgur.com/4KpVtQF.png"
date: 14 August 2020
---
Jekyll is really useful for building static websites. You can use a Jekyll theme to write posts using markdown with less amount of HTML, CSS and have a responsive good looking website. If you are a developer who loves to crerate websites while having control of every single aspect of the HTML and CSS, Jekyll allows for all of that. You can create your own themes, layouts, control and configure the entire site.

We will present enough information to get you started with your first jekyll website, fromcreating content to serving them on github pages.


1. [Installation](#install)
2. [Creating a site](#create)
3. [Front matter](#front)
4. [Installing themes](#themes)
5. [Layouts](#layouts)
6. [Includes](#includes)
7. [Hosting on Github pages](#hosting)

<a name="install"></a>
## Installation
The Jekyll website provides [installation](https://jekyllrb.com/docs/installation/) instructions that covers Windows, Mac and linux operating systems.

<a name="create"></a>
## Creating a site
For this tutorial we will name our website "test_blog". Issue the command below at the terminal to create your new site.
```yml
jekyll new test_blog
```

![create](https://i.imgur.com/8Yaniqp.png)

Jekyll creates some default content for the new site.

![default_content](https://i.imgur.com/i0sydRw.png)
Change directory into the `test_blog` directory
```yml
cd test_blog
```
Run the command below at the terminal and Jekyll will take all the peices of our website and serve them in our browser. Browse the displayed server address `http://127.0.0.1:400/` to see the content of the website. You can also stop the display with the command `ctrl-c`
```yml
bundle exec jekyll serve
```	 
![jekyll-serve](https://i.imgur.com/us5KXsi.png)

The local host server now display the new website from the browser.

![localhost](https://i.imgur.com/onXxPaB.png)

Define the files in the root directory.                                        
`test_blog`: the root directory                      
`_posts`: folder with all the blog posts.   
`_site`:  folder with the final output of the website.   
`_config.yaml`: file with the settings and basic attributes of the site.    
`Gemfile`: holds all the dependecies for the website.    
The rest of the files are just default basic parts of our website.

<a name="front"></a>
## Front matter
Front matter is the information like `Title` and `Name of the author` that is kept on the pages of our site. All the pages on our site have front matter. The default post in our test_blog website has content and front matter.

![front_matter](https://i.imgur.com/kopLTwb.png)

We see some special information at the top of our post which is different from the content, That is called front matter.


<a name="themes"></a>
## Installing themes
By default we will be having a minima theme for our jekyll website. If we want a different theme for our website, there are lots of freely available themes on the internet. Select a theme that you like and write its name in the gemfile then install it with the command below
```yml
bundle install
```
Change the theme value in `_config.yaml` file.
Now restart the server, with the command below, and you will see the changes on your website.
```yml
bundle exec jekyll serve
```
Website for free themes:
 * [Jekyll themes](http://jekyllthemes.org/)
 * [Free jekyll themes](https://jekyll-themes.com/free/)

You can find many other good websites on the internet.

<a name="layouts"></a>
## Layouts
Layouts are skeletons of HTML code used to define the looks and feels of different pages or your entire site.

By default jekyll will provide layouts for our pages. If you want to create your own layout.
1. Go to the root directory and create `layouts` folder.
2. Create a html file of your own and start making your own layout.
![layouts](https://i.imgur.com/qyDBIPp.png)
After you create your own layout, you can switch your site layout to it, which will then show up.

<a name="includes"></a>
## Includes
Includes allows us to take certain components of our site such as the header, the footer or a navigation list and abstract them into their own html files. That means we can have a html file that describes the header or footer for the entire site. We can have a navigation list designed and include that in any page WE want on the site. Follow the steps below to create your own layout.
1. Go to the root directory and create `includes` folder.
2. Create a html file of your own and start to make components of your website.
![layouts](https://i.imgur.com/1FkVA5D.png)
The include file, can be included in any part of your website.

<a name="hosting"></a>
## Hosting on Github pages
Github pages (gh-pages) is a service that Github offers and allows you to build and host a static website completely for free. Jekyll integrates with gh-pages very well.

Setting up and hosting a static site in gh-pages:
1. Create a Github account.
2. Install git on your computer.
3. Create a new repository and name that, `test_blog`. Do not initiliaze a readme file.
![new_repo](https://i.imgur.com/jfAcGzh.png)
4. After creating the repository, we need to edit a variable in config.yaml file.
   *Edit `baseurl` attribute.
   *Add the website name into the base url, in this case it is `test_blog`.
   *If you are planning on using a custom  domain name you need to put that in the base url.
![baseurl](https://i.imgur.com/6I8L9WA.png)
5. Set up a Github repository inside of Jekyll project and upload it into github.

Git commands for creating repository and uploading all files to github :
1. `git init` <br>
This will initialize an empy repository.
2. `git chechout -b gh-pages` <br>
We need to store our files on gh-pages branche on our repository. The above command will checkout gh-pages branch.
3. `git add .` <br>
This will add all our files to staging.
4. `git commit -m "initial commit"`<br>
This is an initial commit.
5. `git remote add origin "add your repository address here"`<br>
6. `git push origin gh-pages` <br>
This will upload all the files to gh-pages.

![upload](https://i.imgur.com/iouj7zZ.png)

After you upload you will see all the files in github

![hosted](https://i.imgur.com/QYJaz66.png)

You can go to settings tab and scroll down you will see "your site is published."

![published](https://i.imgur.com/bGBg8UH.png)

You can use that link to visit your static website.