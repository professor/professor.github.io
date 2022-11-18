---
layout: post
title: "OS X filesystem and case sensitive bugs"
date: 2015-05-13 20:16
comments: false
categories: 
---
# OS X filesystem and case sensitive bugs

Note: I was later convinced that this was a "not so great" solution =)

### Problem: 
On one project, our test cases would be green locally, but then fail on CI due to filesystem case sensitivity differences between OS X (our development environment) and linux (our QA and production environments.). By default, OS X treats ~/project/myFile as equals to ~/projectMyFile. Thus if the code had a typo on an import, it might pass locally when it shouldn't.

### Solution: 
I wanted to use the base pivotal OS X image and sprout wrap. The strategy is to create a case sensitive partition and symlink the workspace directory to it. Sprout wrap has issues with case sensitivity (pivotal_ide_prefs in particular), so we would run that from the user's home directory, but run all project materials in the case sensitive directory.

Alternative solution: getting the pivotal OS X image on a USB key might allow us to configure the default partition's setting on installation.

These steps could work with an existing machine, but I only tested on a clean install

Step 1) install the Pivotal Labs OS X image

Step 2) using Disk Utility, split the only partition in half. For the new partition select "Mac OS Extended (Case-sensitive, Journaled)"

<span class="thumbnail-image-block ssNonEditable"><span><img src="/images/screen_shot_partition.png" alt=""/></span></span>

Step 3) create a workspace directory in the new partition
mkdir /Volumes/CASE_SENSITIVE/workspace

Step 4) symlink ~pivotal/workspace to the new partition's workspace directory. 
ln -s /Volumes/CASE_SENSITIVE/workspace /Users/pivotal/workspace

Step 5) install sprout-wrap from ~, NOT from ~/workspace. I noticed that the pivotal_ide_prefs wouldn't fully work with case sensitive on. (There may be other recipes that have issues too.)

Step 6) install your project code in ~/workspace

Note that everything in Applications et al.  will be typical Mac Setup, but we were fine with that.

