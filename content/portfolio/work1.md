+++
showonlyimage = false
draft = false
image = "img/portfolio/content1/git-hub-page.jpg"
date = "2018-04-27T15:00:00+07:00"
title = "How To Create A Blog and Deploy to Github"
weight = 0
+++

I ve just configured out recently how to create a site and deploy it to github hosting.
<!--more-->

![My blog][1]

### My Table of content

- [Introduction](#introduction)
- [Set Up Project](#setup-project)
- [Integrate Theme](#integrate-theme)
- [Deployment to Github page](#deployment)

#### Introduction <a name="introduction"></a>

Thanks to the article [Every developer should have a blog. Here’s why, and how to stick with it](https://medium.freecodecamp.org/every-developer-should-have-a-blog-heres-why-and-how-to-stick-with-it-5fd55a247fbf) that motivated me a lot to create a blog in order to share my knowledge to community.

So from that helpful topic. There are 3 things I have studied.

1. [Hugo](https://gohugo.io/)
2. [Github page](https://help.github.com/articles/what-is-github-pages/)
3. [Markdown](https://github.com/adam-p/markdown-here)

From this knowlegde I built my own site quickly and focused more on the content that I wanna share.

#### Set Up Project <a name="setup-project"></a>

My assumption is you guys already have experience with [Git](https://git-scm.com/docs/git) in command line, [Github](https://github.com/) which is a repository for your code and your labtop is **MacOS Sierra**.

We will have 3 steps to set up a project.

Step 1: Create Repo on **Github**

Repository is just a simple place to store your code. You have to create Github account first to create repository.

![Create new Repository][2]

Step 2: Install **Hugo**

```
brew install hugo
```

then cd to your Project folder and type

```
hugo new site you-site-name
cd you-site-name
git init
git remote add origin https://github.com/user-name/repo-name.git
```
Here we do 4 minor steps:

 1. Create project name you-site-name
 2. Move to your project name
 3. Initial git repo on local
 4. Point your local git to Git repo online

NOTE: a good question for newbie is where should I get this link https://github.com/user-name/repo-name.git ?

![public link to my repositoty][3]

Step 3 : Push your code to **Github Repository**
```
git status
git commit -m "your-first-message"
git push origin master
```

![How your code look like on Github][4]

#### Integrate Theme <a name="integrate-theme"></a>

Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.

#### Deployment to Github page <a name="deployment"></a>

Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.

[1]: /my-blog/img/portfolio/content1/my-Blog.jpg
[2]: /my-blog/img/portfolio/content1/step1.jpg
[3]: /my-blog/img/portfolio/content1/step2.jpg
[4]: /my-blog/img/portfolio/content1/step3.jpg