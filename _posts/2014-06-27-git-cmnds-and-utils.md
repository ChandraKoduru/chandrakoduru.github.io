---
layout: post
date: 2014-06-27
title: Git - personal - cheat sheet
categories: tech
---

## Hosting a git repo

* cd to the folder __containing__ the repository
* `git daemon --base-path=. --export-all --reuseaddr --informative-errors --verbose`
* `git clone git://<ip.ip.ip.ip>/<reponame>`

* Taming the git daemon <http://railsware.com/blog/2013/09/19/taming-the-git-daemon-to-quickly-share-git-repository/>

## Adding a remote

* `git remote add <remotename> git://127.0.0.1/project_name`

#### After that
    * git fetch <remotename>
    * get pull <remotename> <branch name in the remote>

## Setup A Local gitignore without messing up the project config

* <http://vinitkumar.me/gcode/2014/02/14/setup-a-local-gitignore-without-messing-up-project.html>

* Some IDE and Editors create some files which are very specific developer’s environment.
* They need to be ignored by git.
* But we cannot patch .gitignore. It will effect the entire dev team
* Here is the trick..
* go to: cd .git/info/

    There should be a file called exclude.
    Fill it up with the files and directories you want it to ignore
    such as 

    * *.swp, 
    * ~*


## git push & fetch

* A good article explaining git and also fetch and pull
* <http://longair.net/blog/2009/04/16/git-fetch-and-merge/>

## Tracking Branches and remote tracking branches

* <http://www.gitguys.com/topics/tracking-branches-and-remote-tracking-branches/>

## Compiling and Installing Git on the Ubuntu

* make prefix=/usr/local
* sudo make install prefix=/usr/local

## Other Internals hacking
* https://git-scm.com/book/en/v2/Git-Internals-Git-Objects

* echo 'test content' | git hash-object -w --stdin
    + generate a hash object using the content from stdin
    + -w to write the blob into the git repository at .git/objects/here
    + --stdin to read from std input
    + d670460b4b4aece5915caf5c68d12f560a9fe3e4

* git cat-file -p d670460b4b4aece5915caf5c68d12f560a9fe3e4
    + display the contents of the blob object identified by the hash-tag
    +  -p --> pretty print
    +  -t --> type of the object

* git cat-file -p master^{tree} 
    + pretty print the master(commit)'s tree object

* git update-index --add --cacheinfo 100644 83baae61804e65cc73a7201a7252750c76066a30 test.txt
    + --add --> adding to index
    + --cacheinfo --> adding entry from the git object database
    + 100644 --> blob type plain/exe/link etc
    + 83baae61804e65cc73a7201a7252750c76066a30 --> blob identifier
    + test.txt --> entry name for the corresponding blob (that name need be present on the disk)
    + this command doesn't create any entry/file in the .git repository. TODO: where does it store this information

* git write-tree
    + this command emits a hash-tag of the tree-object
    + writes the contens of the index into a tree-object
    + to read this tree-object use 
        > git cat-file -p <hash-tag>
        > 100644 blob 83baae61804e65cc73a7201a7252750c76066a30      test.txt
        > git cat-file -t <hash-tag>
        > tree

* git commit-tree
    + echo 'first commit' | git commit-tree d8329 -> commit object for the first tree
    + echo 'second commit' | git commit-tree 3c4e9c  -p <above commitid> --> another commit with the pointer to previous commit
    + echo 'third commit' | git commit-tree 3c4e9c -p <above commitid> -> another commit

* git log <any commitid>

* programmatically generating a blob object (using ruby)
```
# code
content = "hello there"
header = "blob #{content.length}\0"
store = header+content
require 'digest/sh1'
# hash tag generation based on the stored content which is header +  content
sha1 = Digest::SHA1.hexdigest(store)
require 'zlib'
# using the sha1 as filename/path to store the content
# content is zipped and stored
zlib_content = Zlib::Deflate.deflate(store)
path = '.git/objects/' + sha1[0,2] + '/' + sha1[2,38]
require 'fileutils'
FileUtils.mkdir_p(File.dirname(path))
File.open(path, 'w') { |f| f.write zlib_content}
```
    + that's it, a valid git blob object will be created
    + all git objects (blob,tree,commit) are generated in a similar manner
    + blob objects can contain any content
    + commit and tree objects have some more formatting/structural requirements
