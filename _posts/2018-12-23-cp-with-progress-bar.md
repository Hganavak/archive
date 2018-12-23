---
layout: post
title: "Copy files with a progress bar"
date: 2018-12-23
tags: bash
---

## cpx alias

```shell
alias cpx="rsync -ah --progress"
```
## Example:

```shell
cpx -r source-folder/ path-to-destination/
```

### Description: 
* Replacement for standard `cp` that gives you progress bars and ETAs
* Maintains file permissions (`rsync -a`)
* Display progress in human-readable format (`rsync -h`)
* Takes `-r` just like standard `cp` for recursive copies

### _Misc._
You can actually use `curl` locally if you're a weirdo to get the same result (although it doesn't maintain file permissions)

```shell
curl -o path-to-destination/ FILE://source-folder/
```
