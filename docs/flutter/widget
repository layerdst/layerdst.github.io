---
layout: default
title: Wiget Structure
parent: flutter
nav_order: 2
---

## Flutter 실행하기 ( VS Code)
- 참고자료 : https://flutter-ko.dev/docs/get-started/test-drive?tab=vscode
- 명령 팔레트 ⇧⌘P (Command + Up Arrow + P)
- Flutter : New Project 선택

## main.dart
- import 
	- flutter/material.dart 는 플러터 프레임워크와 구글에서 제공하는 UI 와 관련된 material 이미지, 소스들을 모두 사용할 수 있게 한다.
	```java
	import 'package:flutter/material.dart';
    ```

- main 메소드
	- runApp() 에서 arguments 는 클래스로 받게 되는데, 최상단의 위젯인 MyApp() 을 사용하는게 일반적이다.

- MyApp 
	- StatelessWidget 을 상속받아 정적인 화면을 구성한다.
	- MyApp 은 위젯의 최상단 트리에 위치하는 위젯이다.
	- MyApp 하위 위젯에는 Material 이 있는데, 이를 리턴한다.
	- Material 위젯에는 title 속성과, home 속성이 있다. 
	- theme 는 optional 한 파라미터로 테마를 의미하고, 견본색상인 blue 테마를 사용하기 위해 입력한다. 
	- Scaffold 는 화면의  UI 를 구성하는 위젯으로 AppBar 와 Center 라는 위젯으로 나뉘게 된다. 
```java
class MyApp extends StatelessWidget {
	const MyApp({Key? key}) : super(key: key);
	
	@override
	Widget build(BuildContext context) {
		return MaterialApp(
			title: 'welcome to Flutter',
			theme:ThemeData(
				primarySwatch : Colors.blue
			)
			home: Scaffold(
				appBar: AppBar(
					title: Text('Welcome to Flutter'),
				),

				body: Center(child: Text('Hello world')),
			),
		);
	}
}
```

![[Pasted image 20220905201332.png]]
