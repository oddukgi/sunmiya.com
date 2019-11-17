---
title: "가격비교어플 구상안"
date: 2019-11-16T10:52:00+09:00
draft: false
tags: ["app project"]
series: ["app project"]
categories: ["app project"]
featured_image: ""
slug: "mini-project"
images: ""
---

개인 앱 프로젝트를 뭘 할지 고민하다가 가격 검색 앱을 생각했다. 
사용자가 제품을 검색하면 네이버 쇼핑에서 여러사이트에서 최저가를 보여주는 앱을 생각했다.
사용자가 찾고 싶은 가격대를 설정하는 기능도 필요할 것이다.

## 가격비교 앱에 필요한 기능
- 제품 검색기능
- 가격대 설정
- 최저가, 최고가 보기
- 공유기능 (SNS, 메모장)

## 프로젝트 시작전 준비사항 
- 네이버 개발자 센터에 가서 openAPI 신청 하였고, 애플리케이션 등록을 한다.
- [네이버 개발자 쇼핑 검색 API](https://developers.naver.com/docs/search/shopping/)를 참고하여 앱등록시 받은 Client ID와 Client Secret을 값을 넣어 url 을 구성한다.

```json
{
    "lastBuildDate": "Sun, 17 Nov 2019 17:50:41 +0900",
    "total": 9783,
    "start": 1,
    "display": 10,
    "items": [
        {
            "title": "애경<b>울샴푸</b> 애경 <b>울샴푸</b> 오리지널 300ml 1개 / 니트 캐시미어",
            "link": "https://search.shopping.naver.com/gate.nhn?id=21003896292",
            "image": "https://shopping-phinf.pstatic.net/main_2100389/21003896292.jpg",
            "lprice": "660",
            "hprice": "0",
            "mallName": "G마켓",
            "productId": "21003896292",
            "productType": "2"
        },
        {
            "title": "애경 애경 <b>울샴푸</b> 300ml/울 세제/드라이/세탁/빨래/물",
            "link": "https://search.shopping.naver.com/gate.nhn?id=21203774698",
            "image": "https://shopping-phinf.pstatic.net/main_2120377/21203774698.jpg",
            "lprice": "680",
            "hprice": "0",
            "mallName": "G마켓",
            "productId": "21203774698",
            "productType": "2"
        }
    ]
}
```
