---
title: Configuring Hexo on Mac with GitHub pages support
date: 2016-02-29 15:07:58
tags:
---
After I went over Google and met some errors, (which none of the blog post I came across mentioned), I decide to write this post to help configure [Hexo](https://hexo.io/) on Mac OS X and post it on [GitHub](https://github.com) pages.

## Environments & Prerequisites

To install hexo, you should have a Node.js environment setup on your mac. Follow [this](http://blog.teamtreehouse.com/install-node-js-npm-mac) guide to install Node.js.

## Installing Hexo and initialization

Then, simply type `npm install hexo-cli -g` and hit return in terminal and ... wait! It took me about 10 minutes to install all the dependencies.

After setting up hexo, make sure you have a GitHub account. Create the repository called `YOURACCOUNTNAME.github.io`, where `YOURACCOUNTNAME` should be your GitHub handle.

Change to your favorite directory and then run `hexo init YOURACCOUNTNAME.github.io` to make a new directory, then you should wait for hexo to do all the initialization for you.

After initialization, **make sure to install the git deployer for hexo**. You can do that by running `npm install hexo-deployer-git --save`.

## Editing configuration file

The configuration file for hexo is `_config.yml`, and you can find more documentation [here](https://hexo.io/docs/configuration.html).

To deploy your site/blog to GitHub, edit the Deployment section as follows:

```yml
# Deployment
## Docs: https://hexo.io/docs/deployment.html
deploy:
  type: git
  repository: git@github.com:YOURACCOUNTNAME/YOURACCOUNTNAME.github.io.git
  branch: master
```

## Push to GitHub

Now since hexo has auto generated a 'hello-world' for you, you don't have to write your own post if you don't want to do it.

Run `hexo generate` (or `hexo g` for short), then you will get the rendered html files under public folder. `hexo serve` or `hexo s` will help you view that site locally on localhost:4000.

Now, if you want to write a post, follow the [Writing](https://hexo.io/docs/writing.html) guide. If you don't, `hexo deploy` or `hexo d` will help you push the public folder onto GitHub on the master branch. Your site will be ready after a successful push.

## Store the repository on GitHub

You might wonder that since the master branch is used to store the site, how to keep track of your source?

Well, `git branch` could be useful for you.

Use `git init` to initialize a git repository in your site folder, then `git add .` and `git commit` to commit all your files.

To setup a remote origin, use `git remote add origin git@github.com:YOURACCOUNTNAME/YOURACCOUNTNAME.github.io.git`. Then create a branch called blog (or whatever you want) by `git branch blog`. Checkout to that branch by `git checkout blog`, and then push to remote by `git push --set-upstream origin blog`.

Note that it might prompt you that you're pushing to a non-existing branch on origin, so you need to use the `--set-upstream` option.

Then you're ready to go!
