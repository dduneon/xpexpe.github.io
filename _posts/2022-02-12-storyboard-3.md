---

title: Storyboard | 화면 전환 방식(push, present)
date: 2022-02-12 22:00:00 +0900
categories: [iOS, Storyboard]
tags: [NavigationController, segue, ViewController, present, push]

---

# 화면 전환 방식(push, present)

---

다양한 서비스를 제공하기 위해서 애플리케이션은 다양한 화면을 이용자에게 제공해야 한다

단일 화면에서 여러개의 뷰를 이용한 화면 전환과 화면 간 데이터를 주고받는 과정은 필수적이라고 할 수 있다

![navigation_interface_2x_8f059f7f-2e2f-4c86-8468-7402b7b3cfe0](https://user-images.githubusercontent.com/84072084/153719497-d12e7c1d-2724-4857-ab26-aab633a47e4a.png)


iOS 설정 어플리케이션에 들어가면 다음과 같은 화면을 볼 수 있는데 이 또한 `Navigation Controller` 를 이용한 화면 전환 방식을 취하고 있다

<br>

## 다음 두 가지 방식이 대표적인 화면 전환의 방식이다

<img width="212" alt="스크린샷 2022-02-12 시간: 23 11 41" src="https://user-images.githubusercontent.com/84072084/153719526-7064a3c0-f0f4-4ab9-aeef-4ebf387ebcfd.png">
<img width="212" alt="스크린샷 2022-02-12 시간: 23 12 04" src="https://user-images.githubusercontent.com/84072084/153719528-8703a8f2-d087-4bb9-bab2-7601d9883a7f.png">

<br>

### **Push**

- 화면이 가로 방향으로 전환되며 스택의 구조를 가진다 (`Navigation Stack` 이라고 불림)
- 상단의 `Back Navigation Item` 이 자동으로 생성되며 누르면 기존 뷰 컨트롤러로 되돌아 간다 (pop 과정)
- Left Edge Swipe(화면 왼쪽 모서리를 스와이프) 방식을 통해서도 이전 화면으로 되돌아 갈 수도 있음
- LIFO(Last In First Out) : 후입선출 방식의 앞서 말한 네비게이션 스택을 활용
- `UINavigationController` 클래스의 메서드를 이용한다

### **Present**

- 화면이 세로 방향으로 전환되며(*default*) `Navigation Controller` 위에 새로운 뷰 컨트롤러가 덮어지게 됨
- Push 방식과 같이 Back 버튼은 생성되지 않으며, Default는 위쪽 가장자리 부분을 아래로 쓸어내리면 기존 뷰 컨트롤러로 되돌아갈 수 있다
- `UIViewController` 클래스의 메서드를 이용한다

<br>

# 화면 전환 방법

---

## `View` 위에 다른 `View` 를 가져와 바꿔치기

- 메모리 누수 위험이 있어 사용되지 않음

## `View Controller` 에서 다른 `View Controller` 를 호출하여 전환

- 이동할 화면의 `View Controller` 를 덮는 방식
- `present, dismiss` 이용
- 비동기 방식 처리

## `Navigation Controller` 를 사용하여 화면 전환하기

- `View Controller` 의 전환을 컨트롤
- `Navigation Stack` 으로 자식 뷰 컨트롤러를 관리
- `pushViewController, popViewController` 이용

## 화면 전환용 객체 `Segue`를 이용한 화면 전환

- Storyboard 만으로 화면 전환 가능
- **Action Segue** : 버튼 터치, 소스코드 추가 안해도 가능
    - Show (`Navigation Controller` 이용시 Push, 없다면 Present 이용)
    - Show Detail : iPad OS에서 이용
    - Present Modally : present 방식으로 처리
    - Present As Popover : iPad OS에서 이용
- **Manual Segue** : 수동으로 처리해주는 `Segue`