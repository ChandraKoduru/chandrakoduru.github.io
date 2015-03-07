---
layout: post
title: Switching to jekyll + github pages
date: 2014-06-10
categories: jekyll tech
---

## Why ?

Somehow, writing on wordpress felt like difficult, distant, not-now kind of activity.
Hence, whenever the itch to write triggers, I postpone it citing those reasons.

I was looking for something that ...

* is always with me
    - on my laptop
* feels like owning it
    - github
* makes me write (quick turnaround)
    - vim editor
    - no browser (browser..feels like little away)
* has good control over styling
    - markdown

Jekyll and Github pages combination seems to have given the solution that is the closest.
The github gave me a comfort that my assets(code,docs etc) are always with me.
The jekyll has both the local service to finetune the style and structure and github pages to host and publish

Another post on the same topic:

<http://vitobotta.com/migrating-from-wordpress-to-jekyll-part-one-why-I-gave-up-on-wordpress>



## How to ..

#### Setup Jekyll

<http://import.jekyllrb.com/docs/home/>

#### Setup github and github-pages account

<https://pages.github.com/>

github pages are commited to repository: `<username>.github.io`

The pages will be made available at `http://<username>.github.io`

*It will take 10 minutes after your first push to view pages*

## Other things..

The way the vanilla version looks is not upto my liking.
But given the other offerings, I am willing to learn jekyll systems to prime it later.

## Now..

* I just open vim and write into a markdown file.
* When it has acquired some meat..
    * start jekyll `jekyll serve --watch`
    * hit <http://localhost:4000>
* Fine tune the text, style etc
* Commit and push it to github 
* Done..it is available to world !!

## Upgrading Jekyll on local system

* gem install github-pages
