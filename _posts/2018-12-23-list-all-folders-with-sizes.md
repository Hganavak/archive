---
layout: post
title: "Douche: List all folders with their total sizes"
date: 2018-12-23
tags: bash
---

# Douche (Mnemonic)

`du -sch */ * | sort -h`

## Description: 
* Lists all top-level files and folders in a directory:
  * Their total size (recursive) (`du -s`)
  * Displays the sum total size of all the items (`du -c`)
  * Displays the size in human-readable format (`du -h`)
  * Puts a `/` at the end of folder names (`du */ *`)
  * Removes duplicates from `*/ *` (`du` does automatically)
  * Sorts by human-readable size (`sort -h`)
