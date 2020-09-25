---
title: "i3 status using FontAwesome!"
date: 2020-09-25T0:0:0+01:00
pre: "<b>0x05 </b>"
weight: 1
tags: ["i3", "unixporn"]
categories: ["hacks"]
summary: "Nicer symbols in i3 status using FontAwesome."
---

[@claussmann](https://github.com/claussmann) 

## Requirements

- [FontAwesome](https://fontawesome.com/) installed
- i3 inclusive i3status installed


## Getting started

The first thing we need to do, is to run i3status as status-command in our i3 bar. Therefore we edit the bar-section in our ~/.config/i3/config:

```
bar {
	status_command i3status
	position top
}


```

Then create the file ~/.config/i3status/config and begin by creating the modules you want:

```
general {
	color_good = "#33FF33"
	color_degraded = "#FFFF66"
	color_bad = "#FF0000"
	colors = true
	#refresh every second
	interval = 1
}

order += "wireless _first_"
order += "ethernet _first_"
order += "battery all"




wireless _first_ {
        format_up = "%essid (%quality)"
        format_down = "No Wifi"
}

ethernet _first_ {
        format_up = "Ethernet (%speed)"
        format_down = "No Ethernet"
}

battery all {
        format = "%status %percentage %remaining"
        status_chr = "CHR"
        status_bat = "On Battery"
        status_full = "Full"
}
#(... other modules)

```

Until now this was the basic setup for the i3status bar. For further information see TODO
If you now reload i3 (usually with mod+shift+R) you should see the i3status bar at the top of your screen showing your wifi-connection and battery percentage.



## Bring the Symbols!

FontAwesome brings a variety of nice icons. Some of them are for free and some cost extra.
The icons can be found and searched at [FontAwesome Galery](fontawesome.com/icons?d=gallery).
When you click on an icon you can see its hexadecimal utf-8/utf-16 representation.

Moving back to your ~/.config/i3status/config file, you can add the icons where you want by entering their hexadecimal representation.
In the nano texteditor this works by pressing CTL+Shift+U. A small u appears and you can simply enter the utf-8/16-hexadecimal code from the icon.
This could for example look as follows:

```
wireless _first_ {
        format_up = " %essid (%quality)"
        format_down = ""
}

ethernet _first_ {
        format_up = " (%speed)"
        format_down = ""
}

battery all {
        format = "%status %percentage <span color='#FFFF66'>%remaining</span>"
        status_chr = "  "
        status_bat = " "
        status_full = " "
}


```

Probaply now if you reload i3 you see some strange symbols instead of you icons.
We have to tell the system that it should use FontAwesome in the status bar.
Move back to your ~/.config/i3/config and edit the bar-section in the following way:

```
bar {
	status_command i3status
	font pango:DejaVu Sans Mono, FontAwesome 10
	position top
}

```

You should see the symbols now after reloading i3.
If you want, you can also set a different seperator (for instance :|:) now in the same config file:


```
bar {
	separator_symbol ":|:"
	status_command i3status
	font pango:DejaVu Sans Mono, FontAwesome 10
	position top
}


```



## Bring the Colors!

By now everything should be white letters on black background.
We now want to colorize the symbols:

Edit ~/.config/i3status/config the following way:

```
general {
	color_good = "#33FF33"
	color_degraded = "#FFFF66"
	color_bad = "#FF0000"
    colors = true
    interval = 1
    #colors:
	markup = "pango"
}


```

Now you can define colors in the modules with a HTML-like syntax. For example the following will make the Battery-Full icon green and the Battery-Charging icon yellow.

```
battery all {
        format = "%status %percentage <span color='#FFFF66'>%remaining</span>"
        status_chr = "<span color='#FFFF66'>  </span>"
        status_bat = "<span color='#FFFF66'> </span>"
        status_full = "<span color='#689F38'> </span>"
        low_threshold = 30
}

```



{{% comments %}}
