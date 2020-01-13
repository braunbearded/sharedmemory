---
title: "Batteryplot"
date: 2020-01-13T12:46:21+01:00
pre: "<b>0x03 </b>"
weight: 1
tags: ["battery", "notebook", "cli", "statistics"]
categories: ["hacks"]
summary: "Monitor your batteryusage on a notebook"
thumbnail: "/hacks/images/0x03-screenshot.png"
thumbnailalt: "screenshot"
---

![screenshot](/hacks/images/0x03-screenshot.png)

[@claussmann](https://github.com/claussmann) On a smartphone you can monitor your batterylife easily. In nice graphics most OS show you an approximation of your batterytime left, when you used how much energy and what app drains your battery most.

Linux-systems can show you your current batterylevel and also an approximation of how long it will last. But as far as i know, you cannot look back into past. Therefor i recently coded a short program, that monitors your battery and can print a nice plot in the CLI.

## Requirements

- UPower (or whatever service your OS uses)


## Install



## Run

First step is to clone the repo [from Github.](https://github.com/claussmann/battery_plot)
You will also find the newest documentation and installation notices there.

Go to the cloned directory an run

```
make install

```

This will create a new directory "~/.batteryusage" and copy all compiled files there.
To start monitoring, you have these options to choose from:

* Run manually (for testing purposes):

```
~/.batteryusage/deamon.sh
```

* Run as cronjob atomatically (recommended):

```
crontab -e
#Append:
*/3 * * * *   /home/YOUR_USER/.batteryusage/deamon-cron.sh
```

Now you can draw the plot:

```
~/.batteryusage/batteryusage-plot
```

I recommend to set an alias for this is you shell config. You should see an empty plot now. Since the cronjob runs only once every 3 minutes, it will take some time until you see something useful in your plot.

If you have ideas how to improve this little tool, pullrequests are welcome!