---
layout: post
title:  "Manage dotfiles"
date:   2014-06-28 19:51:12
categories: dotfiles linux
---

After a while you start to get a lot of dotfiles laying around holding various configuration. Often you want this configuration on multiple machines. I have mine in a GitHub repository, and that works great for distributing it around to my machines. Then I came across GNU Stow, and it made it even better.

To make a soft link in ~/
Clone your github to ~/dotfiles
{% highlight bash %}
cd dotfiles
stow .gitconfig
{% endhighlight %}

This will delete the softlinks

{% highlight bash %}
stow -D .gitconfig 
{% endhighlight %}

To reload a package (delete soft link and add again). Typically if you've added another config file to your package 

{% highlight bash %}
stow -R .gitconfig
{% endhighlight %}

