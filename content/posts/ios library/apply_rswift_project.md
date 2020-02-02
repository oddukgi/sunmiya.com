---
title: "Mint로 R.swift 설치하고,프로젝트에 적용하기"
date: 2020-02-01T10:54:00+09:00
draft: false
tags: [
        "R.swift",
        "Mint"
        ]
series: ["ios library"]
categories: ["ios library"]
slug: "install-r-swift-apply-project"
---

기존에 스토리보드에서 ViewController를 선언하는 코드는 이렇습니다.

<img src="/images/2020/2/rswift_settings/storyboard_vc_access.png">

리소스를 상수형 클래스를 사용하면, 긴 코드를 짧게 줄일 수 있습니다. </br>
R.swift 는 UIImage, 프로젝트 내에 리소스를 끌어올 수 있는 역할을 합니다.
R.swift 패키지를 설치하면, </br>아래와 같이 `r.generated.swift` 파일이 생성이 됩니다. 

![R.swift Swift Package Manager에 추가하기](/images/2020/2/rswift_settings/r.generated.png "r.generated.swift 내부")

## R.swift 사용하기 
1. Mint 설치하기</br>
```
$ brew install mint
```
2. R.swift 를 Mint 를 이용하여 설치하기</br>
```
mint install https://github.com/mac-cain13/R.swift.git@master
```
![Mint를 사용하여 R.swift 설치하기](/images/2020/2/rswift_settings/install rswift using mint.png "CLI 에서 Mint명령어를 사용하여 R.swift 설치하기")

3. Xcode에서 Swift Packages 에 R.swift.Library 추가하고 설치하기</br>
Xcode에서 프로젝트를 선택하고,  Swift Packages 항목에 아래의 git을 추가합니다.</br>
`https://github.com/mac-cain13/R.swift.Library`</br>
git을 추가할 때, 아래의 창이 나올 때, 아래그림 처럼 하면 됩니다. 

<img src="/images/2020/2/rswift_settings/add_r.swift.lib.png" width="60%" height="60%"</img> <br>
4. Build Phase에 [+] 버튼을 눌러  "New Run Script" 이름을  R.swift 를 바뀐뒤, 아래와 같이 넣어줍니다.

- Shell
```sh
if mint list | grep -q 'R.swift'; then
  mint run R.swift rswift generate "$SRCROOT/YOUR_PROJECT_NAME/Resources/R.generated.swift"
else
  echo "error: R.swift not installed; run 'mint bootstrap' to install"
  return -1
fi
```
- Input Files
 `$TEMP_DIR/rswift-lastrun` 
- Output Files
 `$SRCROOT/YOUR_PROJECT_NAME/Resources/R.generated.swift` 

![Build Phase 순서](/images/2020/2/rswift_settings/build_phase.png "Build Phase 순서")

스크립트를 작성을 끝내면 ,Build Phase의 순서를 위 그림처럼 맞춥니다. </br>
순서를 안맞추면 아래 로그처럼 에러가 생깁니다. Warning로그를 보고, 지나치다가 찾아보니 </br>Build Phase 의 순서를 조정하는 것이 해결책 이었습니다.

```swift
Cycle inside XXXX; building could produce unreliable results. This usually can be resolved by moving the target's Headers build phase before Compile Sources.
Cycle details:
→ Target 'XXXX': LinkStoryboards
○ Target 'XXXX': Ditto /Users/yoshimi/Library/Developer/Xcode/DerivedData/XXXX_Admin-heiXXXX_Development-Swift.h
○ Target 'XXXX' has compile command for Swift source files
○ That command depends on command in Target 'XXXX': script phase “Run Script”
○ Target 'XXXX' has compile command with input '/Users/yoshimi/Documents/Project/XXXX/AdminView.storyboard'
```
<br>
5. 프로젝트를 빌드합니다.</br>
6. 파인더에서 R.generated.swift가 생성됩니다. 생성된 파일을 드래그에서 Xcode에 있는 폴더에 넣어줍니다. </br>
저는 Resources 폴더에 넣어줬습니다.</br>
 
<img src="/images/2020/2/rswift_settings/r.generated.swift_auto_create.png" width="45%" height="45%"</img></br>

swift파일에 R을 입력한 뒤 code snippet이 뜨는지 확인합니다.

<img src="/images/2020/2/rswift_settings/r.swift_code snippet.png" width="45%" height="45%"</img></br>

## R.swift를 사용하여 ViewController 를 선언하기 
테스트 할 겸 UITabBarController가 들어 있는 ViewController 를 선언했습니다.
```swift
// MARK: - Segue
    private func performLogin() {
        let tabBarController = R.storyboard.main.mainTabBarController()
    }
```

## 참고 링크
- [R.swift github](https://github.com/mac-cain13/R.swift)
- [R.swift.Library](https://github.com/mac-cain13/R.swift.Library)
- [Manage iOS resources type safely with R.swift](https://andreaslydemann.com/manage-your-ios-resources-type-safely-with-r-swift/)