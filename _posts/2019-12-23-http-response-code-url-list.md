---
layout: post
title: "CURL a list of URLS from a file and get the HTTP response code"
date: 2019-02-19
tags: bash curl xargs
---

## Command
```shell
λ cat list | xargs -i curl -m5 -LI {} -o /dev/null -w '%{http_code} %{url_effective}\n' -s
```

### Example output:
```shell
[sam@samantha] λ cat urls | xargs -i curl -m5 -LI {} -o /dev/null -w '%{http_code} %{url_effective}\n' -s
200 https://askjeeves.net/
200 https://www.bbc.com/
404 https://hganavak.github.io/blog/this-doesnt-exist
200 https://unsplash.com/search/photos/kitten
200 https://hganavak.github.io/
[sam@samantha] λ 
```

### Description: 
* Predicts the winner of the 2020 US election
* `man curl` :muscle:
