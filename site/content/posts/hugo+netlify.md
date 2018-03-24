---
title: "Hugo + Netlify"
date: 2018-03-19T17:00:43-07:00
draft: false
---
I've been trying out different platforms and blogging engines for this site for a while now.  I've given each of the following a good shot, but there were always problems with them for me and they never stuck:

* Wordpress.com
* My own Wordpress.org instance hosted on Azure
* Blogger
* BlogEngine.Net
* github pages
* Medium
* Roll my own blog engine

Each of these failed for me for different reasons.  They either cost too much for features I needed, were too inflexible, or were just way too much work to maintain.  My needs also changed over time.  For example, at one point I imagined that building an engine from scratch would be a great way to learn.  I ain't got time for that at this point, so now I need something that meets my current requirements:

* Easy and frictioness to add new posts
* Fast and secure site
* Easy to set up and maintain
* Support custom domains
* Simple https for subdomains

## Static Sites

The first two are solved by having a [static site](https://www.smashingmagazine.com/2015/11/modern-static-website-generators-next-big-thing/).  I missed when this trend started, but I absolutely love it.  Basically, people realized that for most blogs (and most other types of sites) we really don't need a server processing templates or fetching data from a database.  We could just run a tool that generates a bunch of static HTML pages, and then copy those pages over to a storage solution like Azure Storage or AWS S3, and do a some CDN caching.  Your site will be blazing fast and super safe since there is no code running on a server.

There are a bunch of different static site generators out there.  I picked [Hugo](https://gohugo.io/), actually [*Victor Hugo*](https://github.com/netlify/victor-hugo).  Hugo is a super simple yet powerful generator written in Go and Victor Hugo takes it and adds some boilerplate, bundlers and packers like Gulp, Webpack, PostCSS, and Babel. Once you're set up, you simply make a new markdown file in your site directory, type out your post, and run a build command.  Boom, you've got a full-on site built.  Now you need to host it somewhere.

## Netlify

I'm using [Netlify](https://www.netlify.com/) to host this site and I have been blown away by how awesome this service is.  They make it super easy to deploy a static site from Github, GitLab, or Bitbucket - just connect the accounts and pick your repository.  Netlify will run your build command ( *npm run build* for me ) and copy your build output folder to their storage and cdn after each commit to your repo.  From there, it's just a couple of clicks to set up a custom domain and HTTPS.  For HTTPS, you can either provide your own certificate or they will automatically reach out to [Let's Encrypt](https://letsencrypt.org/) and generate a cert for you.  It couldn't be easier.  They offer a bunch of other cool features that I haven't tried out yet, like [Form submissions](https://www.netlify.com/docs/form-handling/) and [Split Testing](https://www.netlify.com/docs/split-testing) (which sounds amazing).  If you have a site you need to host you should be checking this service out.

## Wrap up

So that's all there is to it.  I'm happy with the set up as it's super simple to me but also very flexible as far as the features I can add to the site, but it's not for everyone.  There is a great [Step-By-Step guide for setting this up](https://www.netlify.com/blog/2016/09/21/a-step-by-step-guide-victor-hugo-on-netlify/) if you want to give it a shot for your site.