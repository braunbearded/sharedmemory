---
title: "Retro Soundcurve"
date: 2020-01-12T21:21:31+01:00
pre: "<b>0x02 </b>"
weight: 1
tags: ["fun", "audio", "cli"]
categories: ["hacks"]
summary: "Show a visualization of your microphones input."
thumbnail: "/hacks/images/0x02-soundcurve.png"
thumbnailalt: "screenshot"
---

![screenshot](/hacks/images/0x02-soundcurve.png)

[@claussmann](https://github.com/claussmann) There is a lot of nice musicplayer software around, that can display a nice visualization of your music while it is playing. Nowadays, in a time of streaming services, it is no longer easy to show a visualization since you don't have the MP3-files.
So how about if you could make the visualization completely independent of the player or software? The key to this is your microphone!

## Requirements

- GStreamer and Pulseaudio installed on your machine
- Microphone


## Getting started

If everything is installed, you should be able to run this comand out of the box:

```
gst-launch-1.0 pulsesrc ! audioconvert ! wavescope ! ximagesink

```

You should now see a window with several waves moving around to the tones that the microphone picks up. Try playing music and watch what happens.
You may want to adjust the volume of the microphone in the pulseaudio settings to fit the graphics to your windowsize.

## Customization

As you will notice, GStreamer interpretes the "!" as a "pipe" just like in your shell. You can simply plug different components together.


```
    audiosource ! visualisation ! videoconvert ! where to show
(...) pulsesrc ! wavescope ! videoconvert ! ximagesink
```

This will show the wave-style already mentioned. But GStreamer gives you other alternatives like these:

```
gst-launch-1.0 pulsesrc ! audioconvert ! synaescope ! ximagesink
gst-launch-1.0 pulsesrc ! audioconvert ! spectrascope ! ximagesink
gst-launch-1.0 pulsesrc ! audioconvert ! spacescope ! ximagesink

```

Now let's bring color into it!

```
gst-launch-1.0 pulsesrc ! audioconvert ! wavescope style=color-lines shade-amount=0x0055bbff ! ximagesink

```

To soften the lines:


```
gst-launch-1.0 pulsesrc ! audioconvert ! wavescope style=color-lines shade-amount=0x0055bbff ! vertigotv ! ximagesink

```

Play with the shaders and visualization-modes and create your own personal audio-visualizer. I know, the visualisations cannot compete with modern software for visualisation. Nevertheless it is a nice shortcut for your shell to quickly visualize music with free software!

## Further information

See the GStreamer wiki for details:
- [gstreamer](https://gstreamer.freedesktop.org/data/doc/gstreamer/head/gst-plugins-bad/html/gst-plugins-bad-plugins-plugin-audiovisualizers.html)

You are not forced to use puseaudio. There are alternative commands for other sound servers like alsa.
- [raspberrypi forum] (https://www.raspberrypi.org/forums/viewtopic.php?t=86115)
