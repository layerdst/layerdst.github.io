---
layout: default
title: 텍스트 가운데 정렬
parent: basic
grand_parent: flutter
nav_order: 4
---

## 문장을 가운데 정렬하기
- AppBar 에 이름은 First App 으로 지정한다.
- AppBar 와 body 사이의 음영을 없앤다. (elevation)
- body 에 hello1, hello2, hello3 3 문장을 나열한다.
- 3문장을 수직 수평 가운데 정렬을 한다.
- MerialApp 과 Scaffold 위젯을 사용한다.
 
```java
class MyApp extends StatelessWidget {
  const MyApp({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return MaterialApp(title: 'character card', home: MyCard());
  }
}

class MyCard extends StatelessWidget {
  const MyCard({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
        appBar: AppBar(
          title: Text('BBANTO'),
          centerTitle: true,
          backgroundColor: Colors.redAccent,
          elevation: 0.0,
        ),
        body: Center(
          child: Column(
              mainAxisAlignment: MainAxisAlignment.center,
              children: [Text('hello'), Text('hello2'), Text('hello3')]),
        ));
  }
}

```
## 결과 이미지

<img src = "https://user-images.githubusercontent.com/71206860/189519369-0f69b3d1-af6c-4d64-a533-a595479b76fc.png" width="300"/>
