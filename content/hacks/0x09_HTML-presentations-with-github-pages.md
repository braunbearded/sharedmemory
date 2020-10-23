---
title: "HTML presentations with github pages"
date: 2020-10-23T17:01:50+02:00
draft: true
pre: "<b>0x09 </b>"
weight: 1
tags: ["github-pages","HTML","presentation"]
categories: ["hacks"]
summary: "HTML presentation are a non-platform bound form of presentations which can be shared publicly through Github-pages"
thumbnail: "/sharedmemory/0x09_pages.png"
thumbnailalt: "Github pages logo"
---


[@grimaldus12](https://github.com/grimaldus12)

Giving online presentations has become a common thing during the pandemic. Every meeting software 
allows to share your screen with others but the quality and experience for the audience is heavily 
dependent on your internet connection. Further maybe people would like to revisit the presentation and 
look things up but not everyone has PowerPoint or can't read the file for some reason. Everyone has a browser 
on the other hand and it would be nice to be able to host a website containing your presentation right? 
Well in this article I will give you the tools you need to publish your HTML presentations with Github-pages.

## Requirements

You need a basic understanding on HTML syntax to actually write your presentation although I have to say that 
I am not good with HTML either but managed to put together good looking (at least for me) presentations nonetheless.
Second you will need a Github account to host a repository. 

## Setting up the repository

Hosting a presentation online is nice but you might want to limit access to certain people. That is also 
possible and will be shown later. For now, the only thing you need to know is, that you can make a private repository 
so not everyone can look up the source HTML. 

In the settings of the repository you have to enable sharing for `Github-pages` but there is no need for a theme or 
custom domains. However I would recommend enforcing HTTPS if you are using a custom domain. 

Lastly, for the presentation to work you need the [reveal.js](https://github.com/hakimel/reveal.js/tree/bd19860b4d6e85ff98067546faa4ffd87527a0ba)
repository linked to yours. This can be done by cloning the repo into the root directory of your repository. Github will automatically 
create the link instead of pushing the encapsulated repository. 

NOTE: Remember to call your reveal.js scripts by the correct path starting from root directory. 

## The HTML file

A complete guide on doing HTML presentations with the reveal.js framework can be found [here](https://revealjs.com/).
I would recommend sticking to full HTML code instead of writing the presentation in a markdown file because you 
get the direct ability to use CSS styles for images etc.

As I alluded to earlier, you might want to restrict access to your presentation. There is no build in way by Github
to protect your pages site, but since `Github-pages` uses static links, you can encrypt the HTML file. Let's assume 
you got your HTML ready, you can now encrypt it. I used [StatiCrypt](https://robinmoisson.github.io/staticrypt/) to achieve 
this. Here you can enter a passphrase for the decription process. Whenever you are trying to access he website in a new session 
you are prompted to enter the passphrase. 

## Local testing

To test out changes locally you can navigate to the `reveal.js` folder and start a local server with `npm start` (requires npm). 
The last step missing to view your changes is, that you have to move the `index.html` file with your presentation into the `reveal.js` folder.
In my opinion it is easiest to check out the `reveal.js` repo and build the whole presentation inside it first and then move on to 
creating your own repo. THe only changes to the `.html` file needed are updated file paths to the scripts and images. 


## Conclusion

In my opinion HTML presentations are a great way to present your results to a broad audience without having to deal with compatibility 
problems. The feature pallete given by the `html` language is nearly unmatched and everything can be adjusted pixel by pixel. 
The setup might be a bit fiddly to get into but after a while you get used to it and know how to initially position things better.
The deployment with `Github pages` is a very easy and free way of hosting a website for these specific purposes and make your presentation 
available.


