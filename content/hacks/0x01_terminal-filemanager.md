---
title: "Terminal file manager"
date: "2020-01-12T00:00:00"
pre: "<b>0x01 </b>"
weight: 1
tags: ["cli", "ranger", "vim", "terminal"]
categories: ["hacks"]
summary: "If you are a terminal enthusiast like me, you appreciate every tool which will make your workflow faster and/or cooler in the terminal. File browsing is something we do day in, day out. This can get tedious, exspecially in the terminal. For me I really like the movement in **vim** so I was looking for a file manager which support that kind of navigation, so I found **ranger**, the cli file manager."
thumbnail: "/hacks/images/0x01-ranger-tn.png"
thumbnailalt: "ranger"
---

![ranger](/hacks/images/0x01-ranger.png)

If you are a terminal enthusiast like me, you appreciate every tool which will make your workflow faster and/or cooler in the terminal. File browsing is something we do day in, day out. This can get tedious, exspecially in the terminal. For me I really like the movement in **vim** so I was looking for a file manager which support that kind of navigation, so I found **ranger**, the cli file manager.

## Requirements

- ranger
- optional (w3m, archiv extract tools (like unrar, 7z, atool, etc.), pdftotext, and many more (check out the github repo at the bottom)

## Installation

Obviously you need to install `ranger`.

### Arch based

`ranger` is in the official arch repo so you can install it with:

```
sudo pacman -S ranger
```

or you can install the aur package:

```
yay -S ranger-git
```

### Debian based

`ranger` is also in the official debian repo. To install it run:

```
apt install ranger
```

## Configuration

Like many cli programs **ranger** is also highly customizable. Depending on your motivation to change the default behaviour of ranger, copy at least the rc.conf into your config directory:

```
mkdir -r ~/.config/ranger
cp /usr/share/doc/ranger/config/rc.conf ~/.config/ranger
```

Almost everyline in the `rc.conf` is documented, so you should be able to customize right away. If you want to customize even more, just copy the files form `/usr/share/doc/ranger/config` to your personal config folder in home.

### Personal customization

I really don't like the bookmarking system in ranger (maybe I didn't get the concept right), so I deactivated it:

```
set autosave_bookmarks false
set save_backtick_bookmark false

# Bookmarks
#map `<any>  enter_bookmark %any
#map '<any>  enter_bookmark %any
#map m<any>  set_bookmark %any
#map um<any> unset_bookmark %any
#
#map m<bg>   draw_bookmarks
#copymap m<bg>  um<bg> `<bg> '<bg>
```

Because I deactivated the bookmarks I needed something similar, so I added some mappings to my most visited directorys:

```
map dic cd ~/.config
map did cd ~/Downloads
map dis cd ~/scripts
```

**ranger** does a good job with previewing all kind of files:

```
set preview_images true
set preview_images_method w3m
```

filter files as-you-type:

```
map f console scout -prts%space
```

## Usage

**ranger** has a 3 column view by default. The middle on is your "working" column. Here you can run all kind of (vim) commands (see below for quick explanation how the controls work). Generally the first and third column will show you the content "below" or "up" (if you would cd into that directory) that directory. Whenever you highlight a file instead of the directory, ranger will show you a preview of that file.

### Controls

Everybody somewhat familiar with **vim** will get the controls pretty fast. I case you don't:

| Key | Description                  |
| --- | ---------------------------- |
| h   | moves you down the file tree |
| l   | moves you up the file tree   |
| j   | moves you down the file list |
| k   | moves you up the file list   |

Copying, deleting, etc. will work like in vim. If you want to do an action on multiply files in the directory, use `space` to select that file:

| Key  | Description                                |
| ---  | ------------------------------------------ |
|space | select/unselect file                       |
|yy    | copy selection/file                        |
|dd    | cut selection/file                         |
|:     | run command                                |
|v     | toggle (select) all files in the directory |
|/     | search/jump to search-phrase               |

If you want more than one tab for browsing you can easily open more:

| Key  | Description          |
| ---  | -------------------- |
|alt+1 | open/switch to tab 1 |
|alt+2 | open/switch to tab 2 |
|alt+x | open/switch to tab x |
|q     | close current tab    |

### My often used commands

**ranger** has some neat features. I will show some of my favorites.

#### Bulkrenaming

Just select all files you want to rename (with space oder v) and then type `:bulkrename`. It will open a vim buffer which will let you rename the files with **vim**. When you are happy with your changes just exit the buffer with `:wq`.

#### Flat

Another nice feature is the `flat` command. Imagine you have file structure with a good amount of files and neasted directorys. With `flat -1` ranger will prefix files in nested directory with the name of this directorys and "move" it in your working column. Now you have one list with all files and directorys, which you can excute commands on.

#### Filter as you type

In addition to the command above, it would be nice so somewhat filter that huge list of files. We can do that with `:scout -prts`. This will shrink the list as you type.

## Further information

If you want to customize **ranger** further more, something doesn't work or you need more information, check out the links below or open an issue on github for this post.

- [arch wiki](https://wiki.archlinux.org/index.php/Ranger)
- [ranger github page](https://github.com/ranger/ranger)

{{% comments %}}
