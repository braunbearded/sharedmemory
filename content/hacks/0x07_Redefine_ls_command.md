---
title: "Redefining cd and ls to work together."
date: "2020-10-02T00:00:00"
pre: "<b>0x07 </b>"
weight: 1
tags: ["bash", "productivity"]
categories: ["hacks"]
summary: "Often *cd* and *ls* are called together. So why don't we define a macro for them?"
---

[@claussmann](https://github.com/claussmann)
To those of you for whom bash programming is old hat, you will get bored with the following.
To everyone else: If I had dealt with bash programming earlier, I would have saved myself a great many *ls*-commands.

Do you know that when you rummage through directories and first call up *ls* in each directory for orientation?
I've been doing this for a while... Until i found out, that i can tell bash to do this automatically!
It is easy to define macros of this type.
The question is why this is not done much more often.

## Requirements

- Bash. Thats it!


## Getting started

The only thing we need to do is to define a bash function.
It will take a path as an argument and will use cd to go to the specified directory and afterwards call ls in that directory.
I will call this function *go* instead of *cd*.

```
go () {
 cd "$1"
 ls
}


```

Add this to your .bashrc file and thats it!
Next time you open bash you can move through directories using the *go* command and will see the contents of the directory automatically!

Of course, this isn't a particularly spectacular hack.
But many of the things that we laboriously type in by hand every day can be processed with one command using precisely these functions. 
*cd* and *ls* are just an example.




{{% comments %}}
