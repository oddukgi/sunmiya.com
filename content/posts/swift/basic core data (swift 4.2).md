---
title: "Core Data(CRUD) Swift 4.2 기초 - Medium 번역"
date: 2019-12-08T20:32:13+09:00
draft: false
tags: [ "swift",
        "core data"]
categories: ["swift"]
slug: "core-data-swift-basic"
---
코어 데이터는 macOS 와 iOS  운영체제를 제공하는 애플사의 객체 그래프 및 지속성 프레임워크 입니다. </br> iPhone SDK 3.0을 탑재한 Mac OS X 10.4 Tiger와 iOS에 도입되었다. 관계 엔티티에 의해 구성된 데이터를 XML, 이진 또는 SQLite 저장소로 직렬화 할 수 있습니다.

## How Does It Differ From SQLite?
Core Data를 처음 접하는 개발자는 종종 SQLite와 Core Data의 차이점으로 인해 혼동됩니다. SQLite 또는 Core Data 가 필요한지 궁금하다면 잘못된 질문입니다. </br> Core Data는 데이터 베이스가 아닙니다.

### SQLite
- 데이터 제한 기능이 있습니다.
- 디스크에 저장된 데이터에서 작동합니다.
- 메모리에 로드하지 않고, 테이블을 삭제하고, 데이터를 편집 할 수 있습니다.
- 핵심 데이터에 비해 느립니다.

###  Core Data
- 필요한 경우 비즈니스 로직으로 구현해야 하는 경우, 데이터 제약 조건이 없습니다.
- 메모리에서 작동 (데이터를 디스크에서 메모리로 로드해야 함)
- 테이블을 삭제하거나 업데이트 해야 할 경우 전체 데이터를 로드해야 합니다.
- 레코드 생성 측면에서 빠릅니다. 저장하는 데 시간이 오래 걸릴 수 있습니다. </br>
또한 백엔드 코어 데이터는 디스크에 데이터를 저장하기 위해 XML 또는 이진 형식을 사용할 수 있으므로 SQLite 와 별도로 제공됩니다.

## Core Data Limitations
### 코어 데이터 단점
1) 프레임 워크의 특성 및 작동 방식과 직접 관련이 있습니다.

- 수천 개의 레코드를 삭제하려면 코어 데이터는 먼저 각 레코드를 메모리에 로드 해야합니다. 

데이터 베이스에서 SQL쿼리를 수행하는 것과 매우 다르고, 잘못하면 메모리 및 성능문제를 발생시킨다.

2) Core Data의 Threading 모델입니다.
프레임워크는 단일 쓰레드(single thread) 로 실행되는 데, core data는 수년에 걸쳐 급격히 발전했습니다. 이 프레임 워크는 멀티 스레드 환경에서 Core Data 작업을보다 안전하고 쉽게 수행 할 수 있도록 다양한 솔루션을 마련했습니다.

## Core Data 의 적합한 용도 
- 복잡한 객체 그래프를 관리해야 하는 애플리케이션의 경우 적합합니다.
- 소수의 관련없는 개체 만 저장해야 하는 경우 , 간단한 솔루션 또는 사용자 기본 시스템을 사용하는 것이 좋습니다.  
예시) Bookmark 엔티티와 Keyword 엔티티를 따로 생성해서 데이터를 저장하도록 설계할 때, 코어 데이터를 쓰면 좋습니다.

##  참고 웹사이트 
[Core Data (CRUD) with Swift 4.2 for Beginners](https://medium.com/@ankurvekariya/core-data-crud-with-swift-4-2-for-beginners-40efe4e7d1cc)








