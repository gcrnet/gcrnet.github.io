---
layout: post
title: Jekyll static site generator
feature-img: "https://i.imgur.com/4KpVtQF.png"
date: 11 August 2020
---
Jekyll is really useful for building static websites.
You can use a Jekyll theme and write posts using markdown with less amount of HTML, CSS and have a awesome responsive good looking website.
If you are a developer who loves to crerate websites and wants to control every single aspect of the HTML and CSS on your site you can do all of that with jekyll. 
Jekyll allows you to create your own themes and layouts etc... You can control and configure the enire site.

In this tutorial we will go thgrough the basics of Jekyll.
We will present enough information to get you started with your first jekyll website, from creating content to serving them on github pages.


1. [Installation](#install)
2. [Creating a site](#create)
3. [Front matter](#front)
4. [Installing themes](#themes)
5. [Layouts](#layouts)
6. [Includes](#includes)
7. [Hosting on Github pages](#hosting)

<a name="install"></a>
## Installation
The Jekyll website provides [installation](https://jekyllrb.com/docs/installation/) instructions that cover all types of operating systems.

<a name="create"></a>
## Creating a site
For this tutorial purpose we will name our website as "test_blog".

Open your command promt and type - 'jekyll new test_blog' and it will create our new site for us.

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
In that we have "posts" folder, where we store all our blog posts.
Then we have "site" folder, the final output of our website.
Next important file is "config.yaml",the settings of your site and contains the basic attributes of the site.
"Gemfile" is used to store all the dependecies for the website. 
Rest of the files are just default basic parts of our website.

<a name="front"></a>
## Front matter
Front matter is the information that we store about the pages of our site. All the pages on our site have front matter.
Front matter may contain information like Title, Name of the author and many more. Front matter can be written in two languages, YAML or JSON. (in a Key value pairs format.) 

The default post in our test_blog website has content and front matter.

![front_matter](https://i.imgur.com/kopLTwb.png)

We see some special information at the top of our post which is different from the content, That is called front matter.


<a name="themes"></a>
## Installing themes
By default we will be having a minima theme for our jekyll website.
If we want a different theme for our website, there are a lot of freely available themes on the internet.
Select a theme that you like and write its name in the gemfile and install it with the command "bundle install".
Change the theme value in 'config.yaml' file.
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

<a name="includes"></a>
## Includes
Includes allows us to take certain components of our site may be a header or footer or a navigation list and abstract them into their own html files. That means we can have a html file that describes the header or footer for the entire site. or we can have a navigation list designed and we can include that in any page you want in the site.
If you want to create your own layout.
1. come to the root directory and create "includes folder".
2. create a html file of your own and you can start making a component of your website.
![layouts](https://i.imgur.com/1FkVA5D.png)
After you create your own include file, you can include that component in any part of your website.

<a name="hosting"></a>
## Hosting on Github pages
Git hub pages is service that Github offers and allows you to serve and host a static website completely for free.
Jekyll intergrates with gh-pages very well.

Prerequisites for you to host your statc site in gh-pages are 
1. You need to have git installed in your pc.
2. You need to have a github account.

Steps to host your static website are
1. Create a new repository and we can name that, for this case I will be naming that test_blog. Do not initiliaze a readme file.
![new_repo](https://i.imgur.com/jfAcGzh.png)
2. After creating the repository, we need to edit a variable in config.yaml file.
We will edit baseurl attribute. We will add our website name into the base url, in this case it is "test_blog".
If you are planning on using a custom  domain name you need to put that in the base url.
![baseurl](https://i.imgur.com/6I8L9WA.png)
3. We will set up a github repository inside our jekyll project and upload it into github.

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