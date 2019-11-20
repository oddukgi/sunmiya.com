---
title: "스토리보드에서 TableView 기본 설정하기"
date: 2019-11-20T17:51:13+09:00
draft: false
tags: [
  "storyboard",
  "constraints",
  "tableview",
  "uikit"
]
series: ["uikit"]
categories: ["uikit"]
slug: "setting-tableview-storyboard"
---
스토리보드에서 뷰컨트롤러를 올리고 테이블뷰를 넣고 난 뒤 constraints 설정하는 것을 잊어먹어서 적어봅니다.

## Setting constraints in Xcode 
뷰컨트롤에 테이블뷰를 올렸습니다. 마진이 여기저기 보입니다.  0으로 설정하여 맞춰야겠죠?
![](/images/2019/11/constraints setting.png"constrainst setting in xcode")

## Create Prototype Cell
![](/images/2019/11/create prototype cells.png"create prototype cells")

## Connect datasource 
생성된 테이블뷰에 우클릭하여 tableview datasource를 연결해줍니다.

<img src="/images/2019/11/connect datasource in tableview.png" width="75%" height="75%" title="connect datasource in TableView" alt="datasource"></img>





