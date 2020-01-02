---
title: "Playground 빌드가 되지않고,행 걸릴 때"
date: 2020-01-02T23:30:10+09:00
draft: false
tags: [
       "xcode",
       "playground"
      ]
categories: ["xcode"]
slug: "playground-is-hanging-no-result"
---

playground에서 코드를 빌드하면, 행(hang) 이 걸려서 결과 값을 못 볼 때가 있다.</br>
코드 넣기 전에 <b style="color:#28DC1C;">&nbsp; import </b> <b style="color:#FF9A19;">PlaygroundSupport</b> 를 넣으면 빌드가 잘 될 것이다.
<br><br>

## 참고 링크
[Playground is not showing result on right bar
](https://stackoverflow.com/questions/26210992/playground-is-not-showing-result-on-right-bar)