---
layout: post
title:  "Manage dotfiles"
date:   2014-06-28 19:51:12
categories: dotfiles
---

To make a soft link in ~/
Clone your github to ~/dotfiles
{% highlight bash %}
$ cd dotfiles
$ stow .gitconfig
{% endhighlight %}

This will delete the softlink

{% highlight bash %}
stow -D .gitconfig 
{% endhighlight %}

To reload a package (delete soft link and add again). 

{% highlight bash %}
stow -R .gitconfig
{% endhighlight %}

