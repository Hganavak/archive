---
layout: post
title: "Git-powered idea logging"
date: 2019-05-29
tags: bash
---

## Description
* Allows you to log your ideas with a single command `idea "Your idea here"`.
* These ideas are timestamped and written to an idea log, which is then `commited`, and `pushed` to a Git repo (with the commit message set to your idea).
* Your idea log can be viewed with the matching `ideas` command (which also does a `git pull` before displaying your ideas).

## Example Usage 

### `idea` command
```shell
[sam@samantha] λ idea "This repository"
Idea added
```

### `ideas` command
```shell
[sam@samantha] λ ideas
===============
= My Idea Log =
===============
Mon May 27 08:22:17 NZST 2019 
This repository

Mon May 27 08:27:31 NZST 2019 
Oh look another cool idea
```

## Setup & Code
1. As this code uses Git, you'll want to initialize a Git repository somewhere  (which will do nothing but store your `idea-log` file). Personally I used `~/Documents/ideas`.

    ```shell
    cd ~/Documents/ideas && touch idea-log && git init
    # Now set your repo upstream tracking
    ```

2. Now simply save the script file below somewhere, and `source` it in your `.bashrc`

    ```shell
    function idea() {
        cd ~/Documents/ideas # cd to idea-log repo directory
        echo -e $(date) "\n$1\n" >> idea-log # Timestamp + add idea to the idea-log file
        git commit -am "$1" --quiet # Silently commit (commit msg=idea) the change
        git push --quiet # Silently push the idea
        cd - > /dev/null # Silently cd back to the previous working directory
        echo -e "Idea added"
    }

    function ideas() {
        cd ~/Documents/ideas # cd to idea-log repo directory
        git pull --quiet # Pull any new ideas that have been added
        cat idea-log # Read the idea log
        cd - > /dev/null # Silently cd back to the previous working directory
    }
    ```
