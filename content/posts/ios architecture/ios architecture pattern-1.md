---
title: "iOS Architecture Pattern 1부"
date: 2019-12-16T20:37:00+09:00
draft: false
tags: [
        "ios",
        "ios architecture"
      ]
series: ["ios architecture"]
categories: ["ios architecture"]
slug: "ios-architecture-patterns"
---
## Demystifying MVC, MVP, MVVM and VIPER
MVC, MVP, MVVM 과  VIPER 에 대한 자세한 내용이 포스팅에 있습니다.
</br></br>
2018년 [iOS Developer 로드맵 ](https://github.com/BohdanOrlov/iOS-Developer-Roadmap)놓치지 마십시오!

UPD: 내가 NSLondon에서 선보인 슬라이드들 [여기](http://slides.com/borlov/arch/fullscreen) 있다. 
iOS에서 MVC를 하는 동안 기분이 이상해? MVVM으로 전환하는 데 대해 의심스러운 점이 있으십니까? VIPER에 대해 들어봤지만, 그럴만한 가치가 있는지 확신할 수 없는가?

계속 읽으면 위의 질문에 대한 답을 찾을 수 있을 것이다. 그렇지 않다면 자유롭게 코멘트로 불만을 표시하십시오.

당신은 iOS 환경에서 architectural 패턴에 대한 지식을 구조화하려고 한다. 우리는 몇몇 인기 있는 것들을 간단히 검토하고, 이론과 연습을 위해  몇 가지 예제코드를 보면서 비교할 것이다. 특정 항목에 대한 자세한 정보가 필요하면 링크를 클릭하십시오.

디자인 패턴을 마스터하는 것은 중독성이 있을 수 있으므로 주의하라: 여러분은 결국 다음과 같이 이 기사를 읽기 전보다 더 많은 질문을 하게 될 것이다.

---

<font size=+1>
<ol>
<li style="padding-left:1em"><b style="color:#31B404;">누가 네트워킹 요청을 소유해야 하는가? 모델 또는 컨트롤러?</b></li>
<li style="padding-left:1em"><b style="color:#31B404;">모델을 새 뷰의 뷰 모델로 전달하는 방법</b></li>
<li style="padding-left:1em"><b style="color:#31B404;">새로운 VIPER 모듈(라우터 또는 프리젠터)을 만드는 사람은?</b></li>
</ol>
</font>
___

## 왜 architecture 를 선택하는 것이 중요합니까?

왜냐하면, 언젠가 수십 가지의 다른 것들을 가지고 거대한 클래스를 디버깅하지 않는다면, class 에서 어떤 버그도 찾아내지 못하고 고칠 수 없는 자신을 보게 될 것이다." 당연히, 이 class를  전체 실체(entity) 로 기억하기는 어렵다. 따라서, 여러분은 항상 몇 가지 중요한 세부사항을 놓치게 될 것이다. 만약 당신이 이미 자신만의 어플리케이션을 가지고 있는 이 상황에 있다면, 그것은 다음과 같은 가능성이 매우 높다.

- 이 클래스는 UIViewController 하위 클래스 입니다.
- UIViewController에 직접 저장된 데이터
- 당신의 UIViews는 거의 아무것도 하지 않는다.
- 그 모델은 이상한 데이터 구조다.
- 당신의 유닛 테스트는 아무것도 포함하지 않는다.

그리고 애플의 가이드라인을 따르고 애플의 MVC 패턴을 구현하고 있음에도 불구하고 이런 일이 일어날 수 있으니 기분 나쁘게 생각하지 마십시오. 애플의 MVC에 이상이 있지만, 나중에 다시 이야기하자.

## 우수한 아키텍처의 특징 정의 
---
<font size=+1>
<ol>
<li style="padding-left:1em"><b style="color:#EB9E2F;">역할이 분명한 엔티티 사이에 균형 잡힌 책임과 분배</b></li>
<li style="padding-left:1em"><b style="color:#EB9E2F;">검증가능성은 대개 첫 번째 특징</b> (그리고 걱정하지 마십시오. 적절한 아키텍처로 용이함)</li>
<li style="padding-left:1em"><b style="color:#EB9E2F;">사용 편의성과 낮은 유지보수 비용</b></li>
</ol>
</font>
___

## 왜 분배해야 하나요?
우리가 어떻게 일이 돌아가는지 알아내려고 노력하는 동안 분배는 우리의 두뇌에 상당한 부담을 줍니다. "만약 여러분이 더 많이 개발할수록 여러분의 뇌가 복잡성을 이해하고 더 잘 적응할 것이다", 라고 하면  여러분은 옳은 것이다. 그러나 이 능력은 선형적으로 확장되지 않고 매우 빨리 상한에 도달한다. 따라서 복잡성을 물리치는 가장 쉬운 방법은 **[단일 책임 원칙](https://en.wikipedia.org/wiki/Single_responsibility_principle)**에 따라 여러 주체 간에 책임을 나누는 것이다.

## 왜 검증가능성이 있습니까?
이것은 대개 보통 새로운 특징을 추가하거나 class 의 복잡성을 리팩토링(refactoring) 하기 때문에 실패한 단위 시험을 감사를 느낀 사람들에게 하는 질문이 아닙니다. 즉, 이 테스트로 인해 개발자가 런타임에 문제를 찾을 수 없게 되었습니다. 앱이 사용자의 장치에 있고 수정 작업이 사용자에게 도달하는 데 일주일이 걸릴 수 있습니다.

## 사용이 간편한 이유는 무엇입니까?
이것은 해답을 필요로 하지 않지만, 최고의 코드는 절대 쓴 적이 없는 코드 입니다.  따라서 코드가 적을수록 버그가 줄어듭니다. 즉, 코드를 적게 쓰려는 욕구는 개발자의 게으름으로만 설명해서는 안 되며, 유지 보수 비용에 암묵하는 현명한 솔루션을 선호해서는 안 됩니다.

> 이 포스팅은 [iOS Architecture Patterns](https://medium.com/ios-os-x-development/ios-architecture-patterns-ecba4c38de52) 참고하여 번역하였습니다. 




