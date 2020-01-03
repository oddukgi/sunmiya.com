---
title: "Playground 빌드가 않 되고, 행 걸릴 때"
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
### 1. 코드 넣기 전에 <b style="color:#28DC1C;">&nbsp; import </b> <b style="color:#FF9A19;">PlaygroundSupport&nbsp;</b> 넣기

효과가 없을 때에는 </br> 
### 2. derived data 폴더 삭제하기
Xcode 메뉴에서 [File] - [Playground Settings] 들어가면 derived data 경로가 보일 것이다.</br> - 화살표를 나오면 클릭한다!!
![Playground Settings](/images/2019/12/playground settings.png "Playground Settings")
**Derived Data 폴더가 보이면, 삭제한다.**

![Derived Data folder](/images/2019/12/derived data folder.png "Derived Data folder")


<br><br>

## 참고 링크
[Playground is not showing result on right bar
](https://stackoverflow.com/questions/26210992/playground-is-not-showing-result-on-right-bar)

[How can I delete derived data in Xcode 8?
](https://stackoverflow.com/questions/38016143/how-can-i-delete-derived-data-in-xcode-8)

