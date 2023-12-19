---
layout: post
title: Java - 접근제어자란 무엇인가?
subtitle: 김영한님의 Java 강의로 기초다지기 - 접근제어자란?
date: 2023-12-13
author: Warner
header-img: img/bg/post-bg-access.jpg
catalog: true
tags:
  - Java
---

## 접근제어자

자바는 `public`,`private` 같은 접근 제어자(access modifier)를 제공한다. 접근 제어자를 사용하면 해당 클래스 외부에서 특정 필드나 메서드에 접근하는 것을 허용하거나 제한할 수 있다.
![speaker.png](/img/post/2023-12-13/speaker.png)

`Speaker` 객체를 사용하는 사용자는 `Speaker`의 `volume` 필드와 메서드에 모두 접근할 수 있다.\
`volumeUp()` 메서드가 있지만 소용이 없다 `volume`필드에 직접 접근해서 원하는 값을 설정할 수 있기 때문이다.

이런 문제를 근본적으로 해결하기 위해서는 `volume` 필드의 외부 접근을 막을 수 있는 방법이 필요하다.

![speaker2.png](/img/post/2023-12-13/speaker2.png)
그림을 보면 `volume` 필드를 `private` 을 사용해서 `Speaker` 내부에 숨겼다.\
외부에서 `volume` 필드에 직접 접근할 수 없게 막은 것이다. `volume` 필드는 이제 `Speaker` 내부에서만 접근할 수 있다.

> **참고**: 좋은 프로그램은 무한한 자유도가 주어지는 프로그램이 아니라 적절한 제약을 제공하는 프로그램이다.

## 접근 제어자의 종류

자바는 4가지 종류의 접근 제어자를 제공한다.

- `private` : 모든 외부 호출을 막는다.
- `default`(package-private) : 같은 패키지안에서 호출은 허용한다.
- `protected` : 같은 패키지 안에서 호출은 허용한다. 패키지가 달라도 상속 관계의 호출은 허용한다.
- `public` : 모든 외부 호출을 허용한다.

순서대로 `private`이 가장 많이 차단하고, `public`이 가장 많이 허용한다.

`private -> default -> protected -> public`

**접근 제어자 사용 위치**

접근제어자는 필드와 메서드, 생성자에 사용된다.\
추가로 클래스 레벨에도 일부 접근 제어자를 사용할 수 있다.

**접근 제어자의 핵심은 속성과 기능을 외부로부터 숨기는 것이다.**

- `private`은 나의 클래스 안으로 속성과 기능을 숨길 때 사용, 외부 클래스에서 해당 기능을 호출할 수 없다.
- `default`는 나의 패키지 안으로 속성과 기능을 숨길 때 사용, 외부 패키지에서 해당 기능을 호출할 수 없다.
- `protected`는 상속 관계로 속성과 기능을 숨길 때 사용, 상속 관계가 아닌 곳에서 해당 기능을 호출할 수 없다.
- `public`은 기능을 숨기지 않고 어디서든 호출할 수 있게 공개한다.

## 캡슐화

캡슐화(Encapsulation)는 객체 지향 프로그래밍의 중요한 개념 중 하나다. 캡슐화는 데이터와 해당 데이터를 처리하는 메서드를 하나로 묶어서 외부에서의 접근을 제한하는 것을 말한다.
캡슐화를 통해 데이터의 직접적인 변경을 방지하거나 제한할 수 있다.\
캡슐화는 쉽게 이야기해서 속성과 기능을 하나로 묶고, 외부에 꼭 필요한 기능만 노출하고 나머지는 모두 내부로 숨기는 것이다.

그럼 어떤 것을 숨기고 어떤 것을 노출해야 할까?

**1. 데이터를 숨겨라**
객체에는 속성(데이터)과 기능(메서드)이 있다. 캡슐화에서 가장 필수로 숨겨야 하는 것은 속성(데이터)이다.\
객체 내부의 데이터를 외부에서 함부로 접근하게 두면, 클래스 안에서 데이터를 다루는 모든 로직을 무시하고 데이터를 변경할 수 있다.
결국 모든 안전망을 다 빠져나가게 된다. 따라서 캡슐화가 깨진다.

**객체의 데이터는 객체가 제공하는 기능인 메서드를 통해서 접근해야 한다.**

**2. 기능을 숨겨라**
객체의 기능 중에서 외부에서 사용하지 않고 내부에서만 사용하는 기능들이 있다. 이런 기능도 모두 감추는 것이 좋다.

정리하면 데이터는 모두 숨기고, 기능은 꼭 필요한 기능만 노출하는 것이 좋은 캡슐화이다.