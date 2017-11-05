---
layout: post
title: "Powerline in Ubuntu 16.04.3 LTS"
date: 2017-11-04 12:26:56 +0530
categories: ubuntu
description: A tutorial to set up powerline in <code>bash</code>, <code>vim</code> and <code>tmux</code>.
image: /blog/images/thumbnail-powerline.jpg
thumbnail: /blog/images/thumb-powerline.jpg
type: blog
tags: [powerline, ubuntu, terminal, vim, tmux, bash]
---
<style>
{% include custom.css %}
</style>

![powerline](/blog/images/powerline.png)

The powerline gives special geeky feel to the inner self. You can set the powerline to your `terminal` prompt, `vim` status or more.

I have given the following steps by which you can set your `powerline` to your `terminal`, `vim` or `tmux`.

#### Steps to install
- Install the powerline using pip3, wget the fonts and apply them system wide.
{% highlight bash linenos %}
$sudo -H pip3 install git+https://github.com/powerline/powerline.git
$wget https://github.com/powerline/powerline/raw/develop/font/PowerlineSymbols.otf
$wget https://github.com/powerline/powerline/raw/develop/font/10-powerline-symbols.conf
$sudo mv PowerlineSymbols.otf /usr/share/fonts/
$sudo fc-cache -vf /usr/share/fonts/
$sudo mv 10-powerline-symbols.conf /etc/fonts/conf.d/
{% endhighlight %}
- Get the location of installed powerline
{% highlight bash linenos %}
$pip show powerline-status
{% endhighlight %}
```
Name: powerline-status
Version: 2.6.dev9999-git.b-5198b50463c7a29a9f5ef94bbc45a995223dac2d-
Summary: The ultimate statusline/prompt utility.
Home-page: https://github.com/powerline/powerline
Author: Kim Silkebaekken
Author-email: kim.silkebaekken+vim@gmail.com
License: MIT
Location: /usr/local/lib/python3.5/dist-packages
Requires:
```
#### Enable Powerline on Bash Shell
- Add the following code in `~/.bashrc`

{% highlight bash linenos %}
export TERM="screen-256color"
powerline-daemon -q
POWERLINE_BASH_CONTINUATION=1
POWERLINE_BASH_SELECT=1
. /usr/local/lib/python3.5/dist-packages/powerline/bindings/bash/powerline.sh
{% endhighlight %}

#### Enable Powerline for Vim
- Add the following code in `~/.vimrc`
{% highlight bash linenos %}
set  rtp+=/usr/local/lib/python3.5/dist-packages/powerline/bindings/vim/
set laststatus=2
set t_Co=256
{% endhighlight %}

#### Enable Powerline for tmux
- Add the following code in `~/.tmux.conf`
{% highlight bash linenos %}
source /usr/local/lib/python3.5/dist-packages/powerline/bindings/tmux/powerline.conf
set-option -g default-terminal "screen-256color"
{% endhighlight %}


#### References
1. https://www.tecmint.com/powerline-adds-powerful-statuslines-and-prompts-to-vim-and-bash/
2. https://www.youtube.com/watch?v=_D6RkmgShvU
