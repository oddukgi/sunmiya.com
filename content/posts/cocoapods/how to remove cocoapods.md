---
title: "How to remove CocoaPods from a project"
date: 2019-11-19T18:10:10+09:00
draft: false
tags: [
  "cocoapods",
  "pod",
  "cocoapods-clean"
]
series: ["cocoapods"]
categories: ["cocoapods"]
slug: "how-to-remove-cocoapods-from-project"
---

Open terminal and go to your project directory and type.
```bash
$ sudo gem install cocoapods-deintegrate cocoapods-clean
$ pod deintegrate
$ pod clean
$ rm Podfile
```