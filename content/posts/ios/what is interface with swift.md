---
title: "Swift에서 Interface란?"
date: 2019-12-26T13:01:00+09:00
draft: false
tags: ["ios",
      "interface",
      "swift"]
categories: ["ios"]
slug: "what-is-interface-in-swift"
---

모바일 디자인 패턴에서 의존성 주입 이라는 개념을 공부하다가 interface 라는 용어를 
보았습니다. 인터페이스가 화면 인터페이스인지, 다른 의미를 갖고 있는가 싶어서 포스팅을 하게 되었습니다.

Swift는 인터페이스 대신 프로토콜이 있습니다.

**`Protocol`은 특정 작업이나 기능에 적합한 방법, 속성 및 기타 요구 사항의 청사진을 정의합니다.** 그런 다음 이러한 요구 사항을 실제로 구현하기 위해 <b style="color:#3339FF;">`class`</b>, <b style="color:#3339FF;">`structure` </b>또는 <b style="color:#3339FF;">`enumeration` </b>프로토콜을 채택 할 수 있습니다. `Protocol` 요구 사항을 충족하는 모든 유형은 해당 프로토콜을 충족한다고합니다. Interface는 `Protocol` 개념과 같은 것입니다.

## example 1
```swift
protocol Animal {
    func canSwim() -> Bool
}
// and we have a class that confirm this protocol name Animal

class Human : Animal {
   func canSwim() -> Bool {
     return true
   }
}
```
## example 2
```swift
protocol Shape {
    func shapeName() -> String
}

class Circle: Shape {
    func shapeName() -> String {
        return "circle"
    }

}

class Triangle: Shape {
    func shapeName() -> String {
        return "triangle"
    }
}
```

- class 와 struct 는 `protocol`을 사용하여 구현할 수 있습니다.

이 컨텐츠는 스택오버플로우 내용을 번역하였습니다. 
[stackoverflow_how_to_create_an_interface_Swift](https://stackoverflow.com/questions/45974041/how-to-create-an-interface-in-swift)