---
layout: default
title: basic
parent: flutter
nav_order: 2
---

## 기본 화면 구성

		
	
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

## 결과이미지
<img src = "https://user-images.githubusercontent.com/71206860/189518375-84dbcc09-6c74-4bb5-870a-3bb388233ed8.png" width="300"/>
	
	
