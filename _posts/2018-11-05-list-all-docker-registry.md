---
layout: post
title: "List all images in a Docker Registry over SSH"
date: 2018-11-05
tags: meta misc docker bash
---

**Warning**: This solution isn't pretty.

By default there's no clean way to list **all** the Docker `images` in a remote docker registry, especially if you're using SSH *without* a keypair or certificate of any kind (as is the case in my setup, yay!).

Instead you have to first query the registry API `_catalog` endpoint to get a list of all the `repositories`, and then run separate queries on each of the repositories that were returned to list all the `images`.

Ergo this monstrosity:

```bash
ssh -t user@host.goes.here '
for repo in $(curl --silent localhost:5000/v2/_catalog | jq -r .repositories[]); do
curl --silent localhost:5000/v2/${repo}/tags/list | jq .;
done;'
```