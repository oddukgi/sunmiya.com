---
title: "[번역] Swift에서 쓰레드 안정성을 있는 배열을 생성하는 법"
date: 2019-12-22T19:19:10+09:00
draft: true
tags: ["ios",
      "thread",
       "array" ]
series: ["ios"]
categories: ["ios"]
slug: "tr-how-to-create-thready-safe-arrays-swift"
---

스레드 안전은 특히 **내장된 동시성 지원이 없는 스위프트**와 같은 언어에서 까다로운 영역이다. 대신, 우리는 [Grand Central Dispatch](https://developer.apple.com/documentation/dispatch) 를 통과해야 한다. 그리고 동시성을 얻을 수 있는 것은 실 안전성을 찾을 수 있는 곳이므로, 스레드 안전을 달성하기 위한 Queue(큐)를 다시 사용해보자.

> Generic 버전은 [링크](https://basememara.com/creating-thread-safe-generic-values-in-swift/)를 참고하세요!

## 선형 큐 메소드 (Serial Queue Method)
직렬 큐를 활용함으로써 우리는 리소스에 대한 상호 배제(mutual exclusion) 를 시행할 수 있다. 직렬 큐를 사용하면 한 번에 하나의 프로세스만 실행될 수 있으므로, 여러 프로세스가 대기열에 채워져 어레이를 수정하는 경우, **직렬 큐는 한 번에 하나의 프로세스만 실행되도록 한다.** 어레이는 설계에 의한 동시 프로세스로부터 안전합니다. 

```swift
let queue = DispatchQueue(label: "MyArrayQueue")
 
queue.async() {
  // 배열 생성 실행
}
 
queue.sync() {
  // 배열 읽기 실행 
}
```

<img src="/images/2019/12/queue_sync.png" width="70%" height="70%" title="Thread in Queue" alt="datasource"></img>
<br><br>
`Dispatch queues`는 기본적으로 serial(직렬)입니다. 이 큐의 `async` 메소드를 사용하여 배열에 쓰고 결과에 대해 걱정하지 않습니다. 비동기 적으로 설정하고 잊어 버립니다. 배열에서 읽을 때 sync 메소드를 사용하여 결과를 즉시 얻을 수 있습니다.

우리는 더 잘 쓸 수 있습니다. 여러 개의 **읽기 요청이 큐(Queue)에서 서로 기다려야 하기 때문에 읽기가 최적화가 되지 않았습니다.** 그러나 동시에 쓰기가 발생하지 않는 한 읽기는 동시에 발생할 수 있어야합니다.

## Concurrent Queue Method (동시성 가진 큐 방법)
이 기술은 보다 우아하며  어레이에서 [공유 제외 잠금 ](https://en.wikipedia.org/wiki/Readers%E2%80%93writer_lock)을 사용합니다. 여전히 **Grand Central Dispatch**를 사용하지만 이번에는 선형 큐 대신 동시성  가진 큐 사용합니다. **동시 읽기에는 효과가 있지만 쓰기 작업에서 모든 동시성을 허용하지 않아야합니다**. `barrier` 디스패치 큐 의 플래그를 사용하여 수행 할 수 있습니다 .

```swift
let queue = DispatchQueue(label: "MyArrayQueue", attributes: .concurrent)
 
queue.async(flags: .barrier) {
  // Mutate array here
}
 
queue.sync() {
  // Read array here
}
```
이 async 메소드에는 barrier 쓰기 플래그가 설정되어 있습니다. 이는 비동기 / 배리어 프로세스가 실행되는 동안 큐에서 다른 블록을 예약 할 수 없음을 의미합니다. sync 읽기 에는 이 방법을 계속 사용  하지만 동시 큐 속성으로 인해 이번에는 모든 리더가 병렬로 실행됩니다.
<br><br>
<br><br>
참고한 글은 [creating thread safe-arrays-in-swift](https://basememara.com/creating-thread-safe-arrays-in-swift/) 입니다.