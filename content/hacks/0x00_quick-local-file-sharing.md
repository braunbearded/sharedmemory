---
title: "Quick local file sharing"
date: "2020-01-10T00:00:00"
weight: 0
pre: "<b>0x00 </b>"
tags: [python, hacks, sharing]
categories: [hacks]
summary: "Did you ever try to quickly share a couple of files from your pc to your phone or vise-versa at home? The following **hack** will teach you exactly that."
thumbnail: "/hacks/images/0x00-listing-tn.png"
thumbnailalt: "webserver listing"
---

![Listing](/hacks/images/0x00-listing.png)
Did you ever try to quickly share a couple of files from your pc to your phone or vise-versa at home? The following **hack** will teach you exactly that.

It will start a simple python webserver in your current directory which will list all directorys and files in that folder able for you to download. Check the ip address of that machine and browse to it on port 8000.

{{% notice warning %}}
Keep in mind that **everybody** in your network can potentially download the files as well because there is **no authentication** by default.
{{% /notice %}}

## Requirements

- python(3)
- some way of aliasing commands in your shell

## Installation

### Unix like systems

- just [download](https://www.python.org/downloads/) and install python(3) for your system

### Android

You can also start a python webserver from your android phone which requires you to install `termux`.
To do so check the `google play store` or `f-droid`. After you are done with installing termux open termus and continue with installing python via:

```
pkg install python
```

Python 3 will be installed in this case.

{{% notice tip %}}
Termux will probably download some stuff. Connect to Wi-Fi beforehand.
{{% /notice %}}

## Configuration

### Python3 (Linux/Mac/Termux)

If you are using a Unix like system and installed python3, add

```
alias share="python3 -m http.server"
```

to your (`.bashrc`) or whatever configuration file is used by your shell.

### Python (Linux/Mac)

If you are on a Unix like system and you choose to use python(2) instead of python3, add

```
alias share="python -m SimpleHTTPServer 8000"
```

to your (`.bashrc`) or whatever configuration file is used by your shell.


## Usage

Move into the directory you want to share and simply type:

```
share
```

{{% comments %}}
