---
title: Storyboard | 오토레이아웃(AutoLayout), Priority
date: 2022-02-09 00:40:00 +0900
categories: [iOS, Storyboard]
tags: [AutoLayout, Compression Resistance, Content Hugging]
---

*AutoLayout, Priority*

# AutoLayout
---

**AutoLayout은 다양한 해상도 비율에 대응하기 위한 개념이고, 제약 조건(Constraints)을 이용하여 뷰의 위치나 크기를 지정하는것**

우리가 `storyboard`상에서 구현한 하나의 애플리케이션 화면이 크기나 비율이 다른 기기에서도 동일한 모습을 보여주기 위하여 우리는 AutoLayout을 이용하여 구현한다

-  **AutoLayout**은 화면과의 margin, `View`들간의 margin, 정렬 등을 이용한다

<img  width="222"  alt="스크린샷 2022-02-06 시간: 23 28 31"  src="https://user-images.githubusercontent.com/84072084/152685628-9a9d8953-056b-4da4-96c1-a85f9a682f73.png">
<img  width="274"  alt="스크린샷 2022-02-06 시간: 23 28 20"  src="https://user-images.githubusercontent.com/84072084/152685625-2546cbc4-132c-49ba-98c7-94f1f7785865.png">

**`Add New Constraints`**를 통하여 제약조건을 추가할 수 있으며 위 선택된 `Label`은 상, 하, 좌, 우로 24만큼의 margin을 가지고 AutoLayout을 구성하고 있는 것을 확인할 수 있다

참고로 기준점은 나와 가까운 곳에 위치한 Object를 기준으로 하며 **상(`Top`), 하(`Bottom`), 좌(`Leading`), 우(`Trailing`)** 으로 표현한다

<br>

<img  width="997"  alt="스크린샷 2022-02-06 시간: 23 40 46"  src="https://user-images.githubusercontent.com/84072084/152686147-57a73af3-bf05-4a8a-9b3f-22f880cea51e.png">

Top에 설정된 Constraints를 예시로 보면, 가장 가까운 Object인 `Safe Area`를 기준으로 24만큼 떨어진 곳에 위치함을 알 수 있는데 `Safe Area`란

> 상태바(Status Bar), 내비게이션 바(Navigation Bar), 탭바(Tabbar) 등에 의해서 View가 가려지지 않기 위해서 제공 되던 시스템적인 마진을 뜻함

따라서 위와 같은 방식으로 AutoLayout을 구성할 수 있다

<br>

# Priority
---

우리는 앞에서 각 요소들 간의 margin의 **`Constraints`(제약)** 을 통하여 **AutoLayout**을 구성하였다

<img  width="268"  alt="스크린샷 2022-02-09 시간: 01 40 48"  src="https://user-images.githubusercontent.com/84072084/153033862-2667f1d3-515b-4d5d-af09-cfb684295d7d.png">

**Priority는 여러 제약조건들을 설정하여 구성하는데, 이들 서로 충돌이 일어날 때 어떤 Object를 우선순위가 되는지를 결정한다**

<img  width="104"  alt="스크린샷 2022-02-09 시간: 03 48 47"  src="https://user-images.githubusercontent.com/84072084/153055312-f0d9fcec-067a-411f-890f-bf89615e2e01.png">

우선순위는 1부터 1000까지의 임의의 수를 통하여 부여할 수 있으며, 숫자가 높을 수록 우선순위가 높음을 의미하며 **`Horizontal`**과 **`Vertical`** 값을 각각 지정할 수 있다

<br>

## Content Hugging Priority
---

**`Content Hugging Priority`는 오브젝트가 원래의 사이즈보다 더 늘어나게 될 때 사용한다**

`Priority`가 높다는 것은 여기서는 크기 증가에 대한 저항성같은 개념으로 생각하였다

- `Priority`값이 크면 : 크기 유지
- `Priority`값이  작으면 : 크기 늘어남

<br>

공간이 남을 때 어떤 오브젝트가 커질 지 결정하는 것이 **`Content Hugging Priority`** 이다

<img width="321" alt="스크린샷 2022-02-09 시간: 04 19 59" src="https://user-images.githubusercontent.com/84072084/153059987-66e4a72c-c1bb-492d-8ed7-4bcc9cd0dddd.png">

위의 사진은 각 Label의 `Constraints`를 `Top`과 `Bottom`은 49, `Leading`과 `Trailing`은 각각 30으로 설정하였더니

다음과 같이 오른쪽의 Label이 Leading과 Trailing `Constraint`를 모두 만족시킬 수 없어 두 Label중 하나는 크기가 늘어나야 하는 상황이 발생하였다

이와 같은 상황에서 `Content Hugging Priority`가 사용되는데, 우선순위가 낮은 객체의 크기가(`Width`)가 증가한다

| 왼쪽 Label | 오른쪽 Label |
|--|--|
| 250 | 250 |

현재 두 Label의 Content Hugging Priority의 값은 다음과 같다

<img width="320" alt="스크린샷 2022-02-09 시간: 04 20 33" src="https://user-images.githubusercontent.com/84072084/153059978-3eb62184-d03c-4638-acc4-a2f2c8442acc.png" title="hi">

| 왼쪽 Label | 오른쪽 Label |
|--|--|
| 250 | 249 |

왼쪽 Label의 `Priority`가 더 크기 때문에 크기 증가에 대한 저항성을 가지므로 오른쪽 Label의 크기가 늘어나서 `Constraints`를 충족시킨다

<img width="317" alt="스크린샷 2022-02-09 시간: 04 20 18" src="https://user-images.githubusercontent.com/84072084/153059983-9f2a992b-9487-4652-b1ec-d815f1817309.png">

| 왼쪽 Label | 오른쪽 Label |
|--|--|
| 249 | 250 |

오른쪽 Label의 `Priority`가 더 크기 때문에 크기 증가에 대한 저항성을 가지므로 왼쪽 Label의 크기가 늘어나서 `Constraints`를 충족시킨다

<br>

## Compression Resistance Priority
---

**`Compression Resistance Priority`는 반대로 오브젝트가 원래의 사이즈보다 줄어들 때 사용한다**

`Priority`가 높다는 것은 크기 감소에 대한 저항성을 가진다는 개념으로 생각하였다

- `Priority`값이 크면 : 크기 유지
- `Priority`값이 작으면 : 크기 감소

<br>

공간이 부족할 때 어떤 오브젝트가 더 작아질 지 결정하는 것이 **`Compression Resistance Priority`** 이다

<img width="340" alt="스크린샷 2022-02-09 시간: 04 44 36" src="https://user-images.githubusercontent.com/84072084/153063722-53f16942-050d-4adb-bc2e-4eb95cccbe5d.png">

위의 사진은 각 Label의 `Constraints`는 위의 상황과 동일하고, 각 Label의 Text를 길게 입력시켜 공간이 부족하도록 만들었다

다음과 같이 두 Label 모두 공간이 부족하여 텍스트가 생략되었고 `Constraints`를 충족시키지 못하기 때문에 경고가 발생한다

이와 같은 상황에서 `Compression Resistance Priority`가 사용되는데, 우선순위가 낮은 객체의 크기가(`Width`)가 감소한다

| 왼쪽 Label | 오른쪽 Label |
|--|--|
| 750 | 750 |

현재 두 Label의 Compression Resistance Priority의 값은 다음과 같다

<img width="313" alt="스크린샷 2022-02-09 시간: 04 44 54" src="https://user-images.githubusercontent.com/84072084/153063715-f1066491-a05b-4732-b6c6-d4484a983e4e.png">

| 왼쪽 Label | 오른쪽 Label |
|--|--|
| 750 | 749 |

왼쪽 Label의 `Priority`가 더 크기 때문에 크기 감소에 대한 저항성을 가지므로 오른쪽 Label의 크기가 줄어들고 왼쪽 Label의 Text를 모두 보여지게 만든다

<br>

<img width="318" alt="스크린샷 2022-02-09 시간: 04 45 04" src="https://user-images.githubusercontent.com/84072084/153063727-cee51d7a-bf42-4a3c-b584-3fdcc05cfbe9.png">

| 왼쪽 Label | 오른쪽 Label |
|--|--|
| 749 | 750 |

반대로 오른쪽 Label의 `Priority`가 더 크기 때문에 크기 감소에 대한 저항성을 가지므로 왼쪽 Label의 크기가 줄어들고 오른쪽 Label의 Text를 모두 보여지게 만든다
