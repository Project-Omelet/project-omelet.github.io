---
title: MaterialApp Widget
author: Luke
date: 2022-06-29 17:08:00 +0900
categories: [Flutter, Basic]
tags: [flutter, Widget]
---

# MaterialApp

MaterialApp은 이름 그대로 material style의 App widget

> 가장 바깥 쪽에 위치하는 widget
{: .prompt-info }

모든 widget은 MaterialApp widget의 하위에 위치

## Properties

**가장 많이 사용하는 대표적인 properties**

- title
  ```dart
  title: 'My App'
  ```
  - App의 한 줄 설명
  - Android의 경우 최근 사용한 앱에 표시
  - IOS는 의미가 없음

- theme
  ```dart
  theme: ThemeData(
    // light/dart mode
    brightness: Brigntness.light,

    // Primary color
    primaryColor: Colors.blue,

    // Font
    fontFamily: 'Noto-sans',
  ),
  ```
  - App의 테마를 구성

- home
  ```dart
  home: Scaffold(
    appBar: AppBar(
        title: const Text('MaterialApp'),
        centerTitle: false,
    ),
    body: Column(
        mainAxisAlignment: MainAxisAlignment.center,
        children: [
            Center(
                child: FloatingActionButton(
                    onPressed: () {},
                ),
            ),
        ],
    ),
  ),
  ```
  - App 실행 시 최초 화면
  - Scaffold Widget을 사용하여 정의
  - Scaffold, AppBar, Column, Center 등은 모두 Widget으로, 다른 section에서 다룸

- routes
  ```dart
  // "/"으로 named route와 함께 시작
  initialRoute: '/',
  routes: {
    // "/" route로 이동하면 FirstScreen widget을 생성
    '/': (context) => FirstScreen(),
    // "/second" route로 이동하면 SecondScreen widget을 생성
    '/second': (context) => SecondScreen(),
  }
  ```
  - 화면 전환을 위한 properties

- debugShowCheckedModeBanner
  ```dart
  debugShowCheckedModeBanner: false // or true
  ```
  - 화면 최상단의 `debug` banner의 유무를 정의
