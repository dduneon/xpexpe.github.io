---
title: Storyboard | UIKit 기초 알아보기
date: 2022-02-06 20:40:00 +0900
categories: [iOS, Storyboard]
tags: [AutoLayout, Content Hugging, Compression Resistance, UIKit, UIViewController]
---

*UIKit 기초 알아보기*

# Cocoa Touch Framework
---

`Cocoa Touch Framework`는 iOS 개발을 위한 최상위 프레임워크이며, 대부분의 클래스 객체들이 모두 이 코코아터치 프레임워크에 속한다

- Framework : 여러 기능을 가진 클래스와 라이브러리가 특정 결과물을 구현하고자 합쳐진 형태 (라이브러리보다 상위 그룹)

아래에서 설명할 `UIKit, Foundation` 을 비롯하여 `CoreData, MapKit` 등의 Framework들을 포함하고 있는 최상위 Framework로 iOS 등의 애플 기기에서 구동되는 Application을 개발하기 위해 사용하는 통합 프레임워크를 말한다

> 참고로 `Cocoa Framework`는 MacOS의 Application을 개발하기 위해 사용되는 통합 프레임워크로, `UIKit`대신 `AppKit`이 포함된다

<br>

# UIKit
---

**Construct and manage a graphical, event-driven user interface for your iOS or tvOS app.** - [애플 공식 문서](https://developer.apple.com/documentation/uikit)

> iOS 또는 tvOS 앱용 그래픽 이벤트 기반 사용자 인터페이스를 구성하고 관리합니다

<br>

`UIKit`은 `Cocoa Touch`를 구성하는 framework들 중 하나로 iOS 애플리케이션의 사용자 인터페이스, 이벤트 처리 및 관리, 애니메이션 등등의 핵심 오브젝트를 지원하는 프레임워크(Framework)이며 다음과 같은 기능들을 담당한다

- event handling
- drawing and printing
- image-handling
- text management and display
- search support
- accessibility support
- app extension support
- resource management

`UI~~`가 붙은 클래스들을 사용하려면 반드시 `UIKit`을 `import`해야 한다

<br>

# Foundation
---

**가장 기본적이고, 필수적인 기능을 정의한 framework**

앱 개발을 위한 기반 기능들을 제공하며 데이터타입, 콜렉션 등을 구현한다


<br>

# 다양한 용어들
---

## UIViewController, UIView

<img width="300" alt="스크린샷 2022-02-06 시간: 22 56 52" src="https://user-images.githubusercontent.com/84072084/152684274-2e9916f9-9f5a-46ad-8b5e-db368266a096.png">

<br>

<img width="219" alt="스크린샷 2022-02-06 시간: 23 17 41" src="https://user-images.githubusercontent.com/84072084/152685176-ddad85b3-d640-443f-be46-28859d144ec6.png">

최상단에 존재하는 `View Controller`는 iOS에서 가장 기본이 되는 컨트롤러로서 화면 하나를 관리하는 단위를 뜻하며 뷰 컨트롤러에 해당하는 `UIKit` 프레임워크의 클래스는 `UIViewController`이다

- 데이터 변경에 대한 응답으로 View의 내용을 업데이트
- View와 사용자 상호 작용에 응답
- View의 크기 조정 및 전체 Interface Layout 관리

<br>

<img width="214" alt="스크린샷 2022-02-06 시간: 23 21 28" src="https://user-images.githubusercontent.com/84072084/152685352-435c38ee-57b0-48dc-bbd6-881e7f4d4ffd.png">

그 아래 위치한 `View`는 화면을 구성하는 기본 클래스로, 이는 `JAVA`에서 GUI프로그래밍을 할 때 사용했었던 `Pannel`과 비슷한 의미인것 같았다

`View`안에는 다양한 Object들을 포함할 수 있으며 `View` 안에 `View`를 넣는 것 또한 가능하다

위의 이미지에서 배경인 흰색 부분은 상단의 `View`이며 "명언 생성기" 라고 적힌 `Label` 밑에 위치한 회색 배경의 Object 또한 `View`이다

<img width="144" alt="스크린샷 2022-02-06 시간: 23 25 26" src="https://user-images.githubusercontent.com/84072084/152685502-81386055-0343-4d9f-a5ec-7e25c6d0a476.png">

이 View는 두개의 Label을 포함한다

<br>

## AutoLayout
---
AutoLayout은 다양한 해상도 비율에 대응하기 위한 개념이고, 제약 조건(Constraints)을 이용하여 뷰의 위치나 크기를 지정하는것

- 화면과의 margin, View들간의 margin, 정렬 등을 이용한다

<img width="222" alt="스크린샷 2022-02-06 시간: 23 28 31" src="https://user-images.githubusercontent.com/84072084/152685628-9a9d8953-056b-4da4-96c1-a85f9a682f73.png">
<img width="274" alt="스크린샷 2022-02-06 시간: 23 28 20" src="https://user-images.githubusercontent.com/84072084/152685625-2546cbc4-132c-49ba-98c7-94f1f7785865.png">

**Add New Constraints**를 통하여 제약조건을 추가할 수 있으며 위 선택된 `Label`은 상, 하, 좌, 우로 24만큼의 margin을 가지고 AutoLayout을 구성하고 있는 것을 확인할 수 있다

참고로 기준점은 나와 가까운 곳에 위치한 Object를 기준으로 하며 **상(Top), 하(Bottom), 좌(Leading), 우(Trailing)**으로 표현하고 있다

<br>

<img width="997" alt="스크린샷 2022-02-06 시간: 23 40 46" src="https://user-images.githubusercontent.com/84072084/152686147-57a73af3-bf05-4a8a-9b3f-22f880cea51e.png">

Top에 설정된 Constraints를 예시로 보면, 가장 가까운 Object인 `Safe Area`를 기준으로 24만큼 떨어진 곳에 위치함을 알 수 있는데 `Safe Area`란

> 상태바(Status Bar), 내비게이션 바(Navigation Bar), 탭바(Tabbar) 등에 의해서 View가 가려지지 않기 위해서 제공 되던 시스템적인 마진을 뜻함

따라서 위와 같은 방식으로 AutoLayout을 구성할 수 있다

<br>

## IBOutlet & IBAction
---

**`IBOutlet`은 Storyboard에 등록한 UI Object를 코드의 변수로 접근할 수 있게 해주는 것이고,**

**`IBAction`은 UI Object의 이벤트 처리 함수를 만들어주는 것이다**

<br>

### IBOutlet

<img width="638" alt="스크린샷 2022-02-06 시간: 23 52 49" src="https://user-images.githubusercontent.com/84072084/152686643-b5d087d2-6691-4ea8-975f-e4fda3e9b65d.png">

storyboard에서 우측에 **Assistant** 를 클릭해주면 다음과 같이 왼쪽에는 storyboard, 오른쪽에는 ViewController가 위치하게 되는데

내가 추가한 Object를 코드로 접근하게 하도록 Object를 왼쪽 마우스로 클릭한 후 ViewController로 드래그 해주면 된다

<br>

<img width="940" alt="스크린샷 2022-02-06 시간: 23 58 55" src="https://user-images.githubusercontent.com/84072084/152686880-66eb5b82-35eb-4bde-888c-27671d772db2.png">

그러면 다음과 같은 화면이 나오는데, `Name`에는 원하는 변수의 이름을 적어주면 되고 `Storage`는 아직 잘 모르지만 메모리 관련 내용으로 특수한 경우 말고는 Weak가 쓰이는 것 같다

<br>

<img width="444" alt="스크린샷 2022-02-07 시간: 00 02 07" src="https://user-images.githubusercontent.com/84072084/152687003-e331d982-f870-4f2a-af96-1beddd7a2e08.png">

Connect를 눌러 주면 비로소 다음과 같이 IBOutlet형 변수가 만들어진 것을 볼 수 있다

<br>

### IBAction

<img width="815" alt="스크린샷 2022-02-07 시간: 00 04 35" src="https://user-images.githubusercontent.com/84072084/152687134-1443ff43-a83a-4aaa-b1be-fb4e633ec213.png">

위와 동일한 방식으로 Button 오브젝트를 생성하여 배치한 후, 연결해 보았더니 IBAction으로 연결된 것을 알 수 있었다

버튼을 눌렀을 때 액션을 만들기 위하여 간단한 코드를 작성해 보았고 실습해 보았다

<img width="375" alt="스크린샷 2022-02-07 시간: 00 11 45" src="https://user-images.githubusercontent.com/84072084/152687437-05b72d17-35c1-4f7f-8ad0-4c1ffdd9bf85.png">

다음과 같이 버튼을 클릭했을 때 레이블의 `text`가 변경되었다

> (미완성) 추가로 적을 것 : Content Hugging, Compression Resistance


Content Hugging, Compression Resistance - 원래의 사이즈보다 늘어나게 될 때 / 더 줄어들게 될 때

높으면 크기 유지 / 낮으면 크기 늘어남

높으면 크기 유지 / 낮으면 크기 줄어듦

명언 - 긴 명언 있으면 사이즈 늘어나야함 Huggin name 보다 작게

name은 크기 줄어들면 안되니까 높게 설정