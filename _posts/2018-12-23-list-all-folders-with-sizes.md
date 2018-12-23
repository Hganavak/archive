---
layout: post
title: "Douche: List all folders with their total sizes"
date: 2018-12-23
tags: bash
---

## Douche (Mnemonic)

```du -sch */ * | sort -h```

### Example output

```
[sam@samantha ~] λ  du -sch */ * | sort -h
4.0K    dotfiles/
4.0K    Music/
4.0K    Public/
4.0K    Templates/
8.0K    Desktop/
8.4M    ibus-uniemoji/
34M     Pictures/
51M     snap/
138M    Documents/
164M    notion-app/
3.3G    anaconda3/
5.7G    Dropbox/
8.5G    Downloads/
157G    Videos/
175G    total
[sam@samantha ~] λ  
```

### Description: 
* Lists all top-level files and folders in a directory:
  * Their total size (recursive) (`du -s`)
  * Displays the sum total size of all the items (`du -c`)
  * Displays the size in human-readable format (`du -h`)
  * Puts a `/` at the end of folder names (`du */ *`)
  * Removes duplicates from `*/ *` (`du` does automatically)
  * Sorts by human-readable size (`sort -h`)
