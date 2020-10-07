---
title: "Using Bash for Productivity"
date: "2020-10-02T00:00:00"
pre: "<b>0x07 </b>"
weight: 1
tags: ["bash", "productivity"]
categories: ["hacks"]
summary: "Often *cd* and *ls* are called together. So why don't we define a macro for them? Bash allows to define functions and alias to make life easier."
thumbnail: "/hacks/images/0x07-screenshot.png"
thumbnailalt: "A simple bash function."
---

[@claussmann](https://github.com/claussmann)
To those of you for whom bash programming is old hat, you will get bored with the following.
To everyone else: If I had dealt with bash programming earlier, I would have saved myself a lot of keyboard typing.



## Requirements

- Bash. Thats it!

## Alias

The alias is a more often used Bash-feature in my experience.
We've been already using it in previous blog posts.
It is very simple, so we only give a brief example here.

Using the networkmanager one can disable or enable WIFI.
Since one has to remember the command and all parameters, to me (even with Bash-completion) it is always a matter of several seconds to turn wifi on or off.
So in our *.bashrc* we define an alias for that:

```
alias wlan_on='nmcli radio wifi on'
alias wlan_off='nmcli radio wifi off'

```

Typing *wlan_on* will enable wifi and *wlan_off* disables it. This is quicker than typing *nmcli radio wifi on*.
But you will also notice, that eventhough only one argument (*on* vs. *off*) changes in the command, we have to define a whole new alias for it, because alias not allowes parameters.

## Functions

... But we can use parameters in Bash-functions. We redefine the wifi alias in the following way:

```
wlan () {
 nmcli radio wifi "$1"
}

```

Now we can type *wlan on* or *wlan off* similar as before.
But we now have only one single macro which takes the parameter *on* or *off*.

*Not convinced?* Well yes, we can live with two different alias. But parameters allow us a much wider range of applications.

For instance, do you know that when you rummage through directories and first call up *ls* in each directory for orientation?
I've been doing this for a while... Until i found out, that i can tell bash to do this automatically.
An alias will not work here at all, because we have to submit the directory we want to go to as parameter.
Again we will define a bash function instead of an alias.
It will take a path to a directory as an argument, will use cd to go to the specified directory and afterwards call ls.

```
go () {
 cd "$1"
 ls
}

```

Now we can use *go* in the same way as *cd* but additionally we always get a feedback on the contents of the directory we're in.
This saves us every time the additional typing of *ls*.

Bash functions can take as many parameters as you like. The first parameter is available in the function as *$1*, the second as *$2* and so on.


## Conclusions

Of course, this isn't a particularly spectacular hack.
But many of the things that we laboriously type in by hand every day can be processed with one command using functions and alias.

We gave only two basic examples, but you can define functions for many other applications of your daily life.
For example define a function to automatically Backup important files to a specific location or define a function that disables all wireless networks at once (Bluetooth, Wifi, Cellular, ...).
Be creative - and become more productive!


{{% comments %}}
