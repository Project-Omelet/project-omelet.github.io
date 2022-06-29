---
title: Flutter 개요
author: Luke
date: 2022-06-29 13:50:00 +0900
catetories: [Flutter, Study]
tags: [flutter]
pin: true
---

# Why Flutter?

## Cross Platform

IOS, Android, Web, Desktop application을 one source로 구현

## Performance

- 대표적으로 비교할 만한 platform은 React-Native(RN)이 있다
- 과거에는 많은 차이를 보였으나, Hermes engine의 도입으로 native에 근접한 성능을 보인다하여 Flutter가 성능면으로 이점을 갖는 것은 과거의 일이 되었다
- 네이티브와 비교했을 때, 네이티브보다 빠를 수는 없지만 근접한 성능을 낸다

## Structure

![Untitled](https://flutter-ko.dev/assets/resources/diagram-layercake-73512ded89f7df8301f622c66178633f04f91187822daf1ddff0d54b2d2676dc.png)

# Start Flutter!

## Environment

책 or Web site를 참고

공식 사이트:

[Install](https://docs.flutter.dev/get-started/install)

## Dart

Made by Google

### 주요 개념

- Variables

  ```dart
  /*
  	Dynamic type
  	var: 어떤 형태의 타입도 가질 수 있는 type (like any in javascript)
  	선언과 동시에 할당 시 최초 할당한 데이터의 타입으로 고정
  */ 선언만 하는 경우 dynamic type -> 추후 할당하더라도 타입 고정이 이뤄지지 않음
  // 선언 + 할당
  var a = 1; // Integer type
  a = 'test'; // Error

  // 선언
  var a;
  a = 1;
  a = 'test'; // No problem

  /*
  	Implicit type
  	- int: 정수형
  	- double: 실수형
  	- String (S is capital): 문자열
  	- bool: true/false
  	- List: Python list와 유사
  	- Map: Key-value data type (Key has unique value)
  	- enum: 열거형
  */
  // String concat -> Javascript style
  var a = 'This';
  var b = 'is';
  var c = 'string';
  var testString = a + ' ' + b + ' ' + c; // Not good
  var testString = '$a $b $c \\$'; // Good

  /*
    List
  */
  // List First Example
  List<String> fruits = []; // 선언
  List<String> fruits = List.empty(growable: true); // 선언 2
  fruits.add('Apple');
  fruits.add('Banana');
  fruits.add('Kiwi'); // Item 추가, ['Apple', 'Banana', 'Kiwi']
  fruits.removeAt(1); // Item 제거, ['Apple', 'Kiwi']

  // List 선언과 동시에 할당
  List<String> fruits = ['Apple', 'Banana', 'Kiwi'];
  List<String> fruits = List.from(['Apple', 'Banana', 'Kiwi']);

  // 고정 길이 List
  // 고정된 길이의 List는 add, removeAt 등 List 길이의 변화가 일어나는 함수 사용 불가
  List<String> fruits = List.filled(3, '');
  fruits[0] = 'Apple';
  fruits[1] = 'Banana';
  fruits[2] = 'Kiwi';

  /* List Functions */
  // join
  var oneString = fruits.join(','); // 'AppleBananaKiwi'

  // indexOf
  var bananaIndex = fruits.indexOf('Banana'); // 1

  // where
  var has_a = fruits.where((fruit) => fruit.toLowerCase().indexOf('a') >= 0);
   // has_a = ['Apple', 'Banana']

  // forEach
  fruits.forEach((fruit) { // Loop - forEach
  	print(fruit);
  });

  // map
  Iterable<String> newFruits = fruits.map((e) {
  	return 'My ${e}';
  });  // ['My Apple', 'My Banana', 'My Kiwi']

  // fold
  List<int> numbers = [1, 2, 3, 4, 5];
  int result = numbers.fold(10, (previousValue, element)
  															=> (previousValue + element) * 2); // 114

  // reduce
  int result = numbers.reduce((value, element) => value + element); // 15

  // asMap
  List<int> numbers = [10, 20, 30, 40, 50];
  Iterable indexNumbers = numbers.asMap().entries.map((e) {
    return 'index: ${e.key} / value: ${e.value}';
  });

  /*
    enum
  */
  enum Status {
  	wait,
  	approve,
  	reject,
  }

  switch (currentStatus) {
    case Status.wait: break;
    case Status.approve: break;
    case Status.reject: break;
  }

  /*
    Constant
  	- final: Runtime에 상수가 지정
  	- const: Compile time에 상수가 지정
  */

  // Constant Example
  final DateTime now = DateTime.now(); // OK
  const DateTime now = DateTime.now(); // Error - compile time에 값을 알 수 없음

  /*
    Nullable: ?
    - 초기값을 설정하지 않고 변수 선언 가능 (default = null)
    - null 할당 가능

  	Null-aware: ??
  	- Means, if null
  */
  String? name;
  name = 'Luke'; // OK
  name = null; // OK

  profileName = name ?? 'default name';

  // Search Default parameter
  ```

- Control flow

  - if-else, switch-case
  - for, while

- Function

- OOP

  - Class
  - Inheritance
  - Method override

- Asynchronous

  - Node.js와 유사하게 Single thread + Event loop 형식
  - dart:isolate library로 Node.js의 worker와 유사하게 구현 가능

# Basic of Flutter

## Concept

### Everything is Widget

화면 안에 모든 요소는 위젯이다 (like React)

- Class의 형태를 갖는다 (view code)

### State

어떤 상태에 대한 값을 저장하는 변수

상태가 변한다 = 이전 상태의 모습에서 현재 상태의 모습으로 바꿔서 보여준다 (re-rendering)

- Local state: 특정 widget에 국한된 상태
  - Using stateful widget & setState
- Global state: 앱 전체를 아우르는 상태
  - 가장 위의 상태를 하위 위젯으로 넘겨주거나,
  - 모듈을 사용하여 해결 (BloC, Provider, GetX, …)

### Stream

흐름

데이터를 불러오는 데 시간이 오래 걸리거나, 지속적으로 데이터를 받아야 하는 경우 활용

! Flutter 비동기 프로그래밍에서 많이 접하게 될 Future와는 다른 개념

Future는 일시적으로 데이터를 받을 때 / Stream은 지속적으로 데이터를 받을 때

- Future: async-await + return 구조 → return으로 값을 받고 종료

- Stream: async \* - await + yield 구조 → yield로 계속 값을 수신

  ```dart
  // Stream Example
  import 'dart:async';

  Future<int> sumStream(Stream<int> stream) async {
  	var sum = 0;
      await for (var value in stream) {
      	sum += value;
          print(sum);
      }
      return sum;
  }
  Stream<int> countStream(int to) async* {
  	for(int i = 1; i < to; i++) {
      	await Future.delayed(const Duration(seconds:1));
          yield i;
      }
  }

  var transformer = StreamTransformer<int, String>.fromHandlers(handleData : (value, sink) {
  	sink.add("value: $value");
  });

  void main() async {
  	var stream = countStream(10);
  //  stream.transform(transformer).listen((value)=>print(value));
    var sum = await sumStream(stream);
    print(sum);
  }
  ```

## New project

### In vscode

- cmd + shift + p (for Mac)
- ctrl + shift + p (for Windows)

### Command-line

```bash
# Flutter project name은 snake-case
flutter create first_app
```

### Structure of project

살펴볼 요소

- pubspec.yaml
- lib/main.dart

### pubspec.yaml

Flutter project의 메타 정보를 담고 있는 마크업 파일

- Project name, descriptions, version, etc…

- Package

  - pubspec.yaml 파일에 직접 타이핑하여 추가

    - 추가 후, vscode 확장이나 기타 도구를 사용하지 않는 경우 get 명령어로 다운로드를 수행

    ```bash
    flutter pub get
    ```

  - Command-line 명령어를 통해 추가

    ```bash
    # Version을 명시하지 않으면 최신의 모듈을 받아온다
    flutter pub add 'package name'
    ```

- Image

  - Image resource를 정의하는 부분

- Font

  - Image와 동일한 방식으로, 사용하고자 하는 글꼴을 정의하는 부분

### lib

실제 구현하게 될 dart 코드가 위치하는 폴더

- main.dart - Root code
