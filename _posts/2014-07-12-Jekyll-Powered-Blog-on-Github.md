---
layout: post
title:  Jekyll Powered Blog on Github
keywords: Jekyll, blog, github
quote: 
---

Before I wrote this article, I asked myself why I choose to host my blog on Github. However, I cannot find a satisfying reason to convince everyone. There are so many choices there. For instance, [Wordpress.com](http://www.wordpress.com) and [Blogger](https://www.blogger.com/) are two free good blogging platforms. If you prefer Markdown editing, [Ghost](https://ghost.org/) and [Logdown](http://logdown.com/) provide good solutions for editors. There is no sliver bullet by Jekyll powered Blog. So, who is the potential user of Jekyll powered Blog on Github?

First of all, you have some basic ideas of web programming and Markdown editing. Second, you only blog on some specific machines. Third and most importantly, *you want to control every code on your blog*. If you meet all of those, you should go through this article and give the Jekyll powered blog a try.

<!--more-->

> The instructions in this article are summarized from [Github Help](https://help.github.com/), [Jekyll](http://jekyllrb.com/), and [JekyllBootstrap](http://jekyllbootstrap.com/). I assume that you have some ideas about Git.

## Create the repository environment

Github provides each user/business account a page on your user name (ex: your_username.github.io), and infinite project pages under your personal domain name (ex: your_username.github.io/project_name). Those two are only different in this part, and I will introduce the way of building their environments separately.

### User/business page

- Create a new repository, and name it as: `your_username.github.io`.

> your_username here is your login name. You can also create `your_username.github.com`, which is an alias of your_username.github.io.

- Clone this repository from github
^
	git clone https://github.com/your_username/your_username.github.io.git

### Project page

For each project, Github read contents in gh-pages branch to generate the page, and this is the only difference.

- Create a new repository if you don't have a project yet. You can choose any name as you want, and assume it as `your_project`.

- Clone this repository from github
^
	$ git clone https://github.com/your_username/your_project.io.git

- Create an orphan branch to hold all your files
^
	$ git checkout --orphan gh-pages

- Remove all contents in this branch
^
	$ git rm -rf *

Now, you have an empty directory, which is used to store all you web contents. We will commit contents later.

## Install Jekyll

Jekyll is an interpreter, which makes you review your website in your locate machines. Here, we follow the instructions from Github to install Jekyll.

- Install ruby, please take a look [the instructions](https://www.ruby-lang.org/en/downloads/). (If you are using OS X, you can skip this step.)

- Install the package manager Bundler
^
	$ gem install bundler

- Create configuration file

	Create a file called `Gemfile`, and add followings into this file.
^
	source 'https://rubygems.org'
	gem 'github-pages'

- Install Jekyll
^
	$ gem install github-pages
	
## Run Jekyll

Since we installed Jekyll from bundler, we can launch Jekyll from bundler. Use the command 

	$ bundle exec jekyll serve 

in your root of the repository to compile the website. Then, you can check your website in the location `http://localhost:4000`. Since we have not put anything into the folder, it should be empty now.

## Site generator

So far, we only have no contents in our blog. To quickly start a blog, we can use some generators to help us. I recommend two generators: [jekyll-bootstrap-3](https://github.com/dbtek/jekyll-bootstrap-3) and [Poole](http://getpoole.com/). Please clone their files and put it into the root folder of your repository.

## Jekyll config

The configurations of Jekyll are set in file `_config.yml`. Here, I introduce some basic configurations used in Jekyll

- **Markdown engine**: the default from bundler is kramdown, which is recommended by Git. You can change to any other engine, as you want.
^
	markdown: kramdown

- **Markdown extension**: choose what extensions will be treated as a markdown file. Here, we include markdown,mkd,mkdn, and md.
^
	markdown_ext: markdown,mkd,mkdn,md

- **Permalink**: the way you path of your post look like. Here, we make it as /2004/title-for-blog.
^ 
	permalink: /:year/:title/

- **Base Url path**: this is only required in project page. Even through the root of your project page is `your_username.github.io/your_project`, the permalink we generated above still put your post in `your_username.github.io/2004/title-for-blog`. Therefore, we should set this value to make your post in the correct path `your_username.github.io/your_project/2004/title-for-blog`.
^
	baseurl: /your_project

> However, if you set baseurl, the local viewer cannot recognize this path because it think everything is in the root. Therefore, to review your blog locally, you should use command `bundle exec jekyll serve --baseurl ''` to run Jekyll.

> In order to make your url path correctly when linking resources (ex, images and css), link everything like this way: \{\{ site.baseurl \}\}/path/to/css.

- Please check [Jekyll Documents](http://jekyllrb.com/docs/home/) for more details.

## Submit your files

After we have done all constructions, we commit our files and upload to github.

- Add your files into repository
^
	$ git add .

- Commit your modification
^
	$ git commit -m "First commit"

- Push to github
^
	$ git push -u origin master (if this is your user page)
	$ git push origin gh-pages (if this is your project page)

Now, you can check your blog in the address `http://your_username.github.io` or `http://your_username.github.io/your_project`. 

Ya!!