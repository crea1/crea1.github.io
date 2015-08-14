---
layout: post
title:  "Manage dotfiles with GIT and GNU Stow"
date:   2015-08-14 10:00:00
categories: linux
---

After a while you start to get a lot of dotfiles laying around holding various configuration. Often you want this configuration on multiple machines. I have mine in a GitHub repository, and that works great for distributing it around to my machines. Then I came across GNU Stow, and it made it even better. I use ubuntu and installed it using apt ```sudo apt-get install stow```

My dotfile repository can be found at <https://github.com/crea1/dotfiles> and is structured like below. Each folder is package that can be installed with stow.

{% highlight bash %}
.
├── bash
│   └── .bash_aliases
├── bash-extra
│   └── .inputrc
├── git
│   ├── .gitconfig
│   └── .gitignore
├── README.md
└── scripts
    └── bin
        └── restart_ibus
{% endhighlight %}

Say I want the contents of the git package to be installed in my home folder ~/

Clone the repository inside your home folder

{% highlight bash %}
cd ~
git clone git@github.com:crea1/dotfiles.git
{% endhighlight %}

Go into the repository and use stow to install the git package. 

{% highlight bash %}
cd dotfiles
stow git
{% endhighlight %}

The result is that both .gitconfig and .gitignore have been installed in my home folder using soft links.

{% highlight bash %}
ls -la ~/.git*
lrwxrwxrwx  1 crea1 crea1     27 aug.  13 10:17 .gitconfig -> dotfiles/git/.gitconfig
lrwxrwxrwx  1 crea1 crea1     27 aug.  13 10:17 .gitignore -> dotfiles/git/.gitignore
{% endhighlight %}

This will delete the soft links.

{% highlight bash %}
stow -D git 
{% endhighlight %}

To reload a package (delete soft link and add again). Typically if you've added another config file to your package and want that installed aswell.

{% highlight bash %}
stow -R git
{% endhighlight %}

