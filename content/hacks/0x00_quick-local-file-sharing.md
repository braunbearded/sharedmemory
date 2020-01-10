---
title: "Quick local file sharing"
date: 2020-01-10T20:15:24+01:00
weight: 10000
pre: "<b>0x00 </b>"
---

Did you ever try quickly to share a couple of files from your pc to your phone or vise-versa at home? The following **hack** will teach you exactly that.

<!--more-->

The following command will start a simple python webserver in your current directory which will list all directorys and files in that folder able for you to download. Check the ip address of that machine and browse to it on port 8000.

{{% notice warning %}}
Keep in mind that **everybody** in your network can potentially download the files aswell because there is **no authentication** by default.
{{% /notice %}}

## Requirements

- python(3)
- some way of aliasing commands

## Installation

- just [download](https://www.python.org/downloads/) and install python(3) for your system

## Configuration

### Python3

#### Linux/Mac

If you are using a Unix like system and installed python3, add
```
alias share="python3 -m http.server"
```
to your (`.bashrc`) or whatever configuration file is used by your shell.

### Python

#### Linux/Mac

If you are on a Unix like system and installed python instead of python3, add
```
alias share="python -m SimpleHTTPServer 8000"
```
to your (`.bashrc`) or whatever configuration file is used by your shell.

## Usage

Move into the directory you want to share and simply type
```
share
```
