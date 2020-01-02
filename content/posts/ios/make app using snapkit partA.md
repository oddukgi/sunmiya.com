---
title: "Problem of using storyboard & SnapKit Intro"
date: 2020-01-02T19:24:20+09:00
draft: false
tags: [ "ios",
       "snapkit", 
       "swift"]
series: ["ios"]
categories: ["ios"]
slug: "problem-of-storyboard-n-start-use-snapkit"
---
iOS 개발을 처음 배우면서, 스토리보드에 올려서 앱을 개발해왔다.
화면을 여러개 만들고 나서, 리소스를 넣는 것은 쉽지만 레이아웃을 하나씩 잡는 것은 쉽지 않다.
우연치 않게  Snapkit 을 맛보기로 보고나서, 코드로 화면을 구성하는 점이 신기했다.

## 스토리 보드 사용시 불편한 점 🤔
---
<font size=+1>
<ol>
<li style="padding-left:1em"><b style="color:#FFC300;">스토리보드를 여는 것은 오래 걸리고 느리다.</b></li>
<li style="padding-left:1em"><b style="color:#FFC300;">팀 단위로 작업할 때, 문제가 생긴다.</b></li>
<li style="padding-left:1em"><b style="color:#FFC300;">중복되는 코드를 쓸 때나, 중복되는 부분을 수정할 때 불필요한 동작 반복한다.</b></li>
<li style="padding-left:1em"><b style="color:#FFC300;">스토리보드에 여러 개 화면을 만들면, 복잡하고 지저분하다. </b></li>
</ol>
</font>

---
위 내용은 미디움 사이트에서 찾은 [스토리 보드 및 인터페이스 빌더 사용을 중단 한 이유](https://medium.com/@kenzai/why-i-stopped-using-storyboards-and-interface-builder-a9142e060f71) 정리하였습니다.

## SnapKit 코드 맛보기 
SnapKit is a DSL to make Auto Layout easy on both iOS and OS X.
스탭킷은  iOS와 OSX 에서 쉽게 Auto Layout을 만들 수 있는 라이브러리 입니다.

이렇게 ViewController에 코드를 넣으면 화면이 딱 만들어 집니다.
```swift
class ViewController: UIViewController {
    lazy var box = UIView()
    
    override func viewDidLoad() {
      super.viewDidLoad()
        
      self.view.backgroundColor = UIColor.white
      self.view.addSubview(box)
          box.backgroundColor = .green
          box.snp.makeConstraints { (make) -> Void in
            make.width.height.equalTo(100)
             make.firstBaseline.equalTo(self.view)
          }
     }
}

```
<img src="/images/2019/12/vc.png" width="60%" height="60%" title="connect datasource in TableView" alt="datasource"></img>

##   참고할 링크
- [스토리 보드 및 인터페이스 빌더 사용을 중단 한 이유](https://medium.com/@kenzai/why-i-stopped-using-storyboards-and-interface-builder-a9142e060f71)" 
- [SnapKit](https://github.com/SnapKit/SnapKit)
- [Swift 로 iOS 앱 만들기 - 03 : Auto Layout 과 SnapKit](https://tono18.tistory.com/4?category=837544)











