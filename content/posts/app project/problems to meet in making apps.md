---
title: "The problems encountered in creating apps"
date: 2019-12-06T17:49:00+09:00
draft: false
tags: ["app project"]
series: ["app project"]
categories: ["app project"]
slug: "problems-encountered-in-creating apps"
---
개인 앱 프로젝트로 네이버 쇼핑의 Open API를 사용하여 제품 검색 앱을 만들었습니다.
url속에 검색어를 넣어서 query를 구성합니다. 결과값은 10개로 제한하여 구성했습니다. </br>

```
https://openapi.naver.com/v1/search/shop.json?query=%EB%84%A4%ED%8C%8C&start=1&display=10&sort=sim
```

위의 URL 에 접근하기 위해서는 secret id와 password 가 있어야 합니다.

네이버 개발자 센터에 문서를 보니 이렇게 되어있네요.
> 네이버 쇼핑 검색 결과를 출력해주는 REST API입니다. 비로그인 오픈 API이므로 GET으로 호출할 때 HTTP Header에 애플리케이션 등록 시 **발급받은 Client ID**와 **Client Secret 값**을 같이 전송해 주시면 활용 가능합니다.

자세한 내용은 아래의 [문서](https://developers.naver.com/docs/search/shopping/)를 참고하세요.

요청은 쉽게 하고자 Alamofire 를 사용하였습니다. 요청해서 결과 값도 잘 나오네요.
다음으로, 사용자가 좋아하는 아이템을 선택하여 저장하는 기능을 만들었는데요.
여기서 문제가 생깁니다.
2개를 선택하였는데, 불러온 데이터는 3개로 개수가 않맞습니다. 

<img src="/images/2019/11/tableview.png" width="60%" height="60%" title="connect datasource in TableView" alt="datasource"></img>

## Log 

```
1
3
4
3

마하링크 DVI- D 싱글
Optional(4) //--> problem
리버네트워크 넥시 DVI- D 듀얼 케이블
Optional(4)
강원전자 넷메이트 DVI- D 듀얼 골드 메탈 케이블
Optional(4)
Optional(4) 
```

아직 문제를 해결을 못했네요. 해결되는 데로 방법을 정리하여 포스팅을 올리겠습니다.


