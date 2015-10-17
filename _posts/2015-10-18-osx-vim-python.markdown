---
layout: post
title:  "OSX VIM with Python support"
date:   2015-10-17 08:48:17
categories: blog
---

Several months ago I spent way too long trying to figure out how to upgrade my Vim install from the default system 7.3 install to 7.4 in order to use new plugins. Hours later I gave up.

It should have been as easy as this:

{% highlight bash %}
sudo port install vim
{% endhighlight %}

When I fired it up, I get this message about python not being installed. Well OSX comes with a default python install. Well `sudo port select python python27`. Nope.

Fast-forward to a few weeks ago when our team start developing outside the VM. I install MacVim with python support. It works, but it's super slow.

I wanted my old workflow back with `tmux`. And in order to get that back, I need to get a usable latest `vim` install. I finally made some headway.

# First, fetch the `vim` repo.

{% highlight bash %}
git clone https://github.com/vim/vim.git
cd src
make distclean  # if you build Vim before
{% endhighlight %}

# Next configure it.

I'm configuring to remove gui support. Not important. I'm adding the `huge` feature set because why not. Don't need NetBeans support. **Enabling Python support**. Finally, since I'm using Macports, I point to the Macports directory.

{% highlight bash %}
./configure --disable-darwin --enable-gui=no --with-features=huge \
--disable-netbeans --enable-pythoninterp \
--prefix=/opt/local --with-local-dir=/opt/local --disable-netbeans
{% endhighlight %}

# Now, make and install

{% highlight bash %}
make
sudo make install
{% endhighlight %}

# Woo!
Next step is to get tmux working. I'm thinking of splitting my tmux config to work across OSX and Linux.
