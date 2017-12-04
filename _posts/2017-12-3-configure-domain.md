---
layout: single
title: "Configure 1&1 domain for GitHub Pages Site"
excerpt: "How to setup a custom domain name on 1&1 for a GutHub Pages website"
tags: [jekyll,github]
share: true
comments: true
---

The process of setting up a custom domain name for a [GitHub Pages](https://pages.github.com/) website is striaght forward, but it could be confusing if you haven't setup a domain before. I will use [1&1](https://www.1and1.com) a domain name register to setup GitHub Pages website domain. the process should be similar using other domain registers such as [GoDaddy](https://www.godaddy.com/).

## Configure domain on GitHub

 First we start by setting up the domain name on GitHub Pages repository. under you GitHub repository settings, Find GiHub Pages section then set Custom domain to your domain name and hit save.

 <img src="/files/github_domain_2017-12-03.png">

## Configure Subdomain CNAME

 At this point your github website is configured and ready to receive traffic from your domain register dns! The next step is to configure a subdomain for your website. follow the steps:

 1. Login to your 1&1 account.
 2. Click Domains from left side menu.

 <img src="/files/domains_2017-12-03.png">
 
 3. Click `Manage Subdomains` under your domain settings
 4. Click `Add subdomain` on the right side menu.
 5. Choose a name for your subdomain

**If** you would like to to redirect all traffic from root domain to your website, use `www` as your subdomain name.
{: .notice--success}


 <img src="/files/subdomain_2017-12-03.png">

 6. Click edit domain settings on the newly created subdomain.
 7. To setup a `CNAME` or a traget for dns to forward traffic to, choose `CNAME` in **A/AAAA and CNAME Records** section
 8. Then enter your GitHub pages url under **Alias** `username.github.io`

 <img src="/files/cname_2017-12-03.png">

## Forward All Traffic

The last step before you're all done, is to setup the main root domain to redirect to subdomain. In order to do that:

1. Go to 1&1 domain control panel.
2. Click on your root domain name
3. Click on `Forward to` under settings
4. Choose Redirect type to `HTTP redirect`
5. Set your `Redirect to destination` to your subdomain name `http://www.yourdomain.com`

 <img src="/files/redirect_2017-12-03.png">

 Great! You'are all done.

### More Info

 * [Setting up a www subdomain on GitHub Pages](https://help.github.com/articles/setting-up-a-www-subdomain/)
 * [Configuring a publishing source for GitHub Pages](https://help.github.com/articles/configuring-a-publishing-source-for-github-pages/)
 * [Setting Up Your CNAME with 1and1 Web Hosting](https://documentation.unbounce.com/hc/en-us/articles/204432234-Setting-Up-Your-CNAME-with-1and1-Web-Hosting)
