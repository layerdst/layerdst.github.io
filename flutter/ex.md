## 강의예제 원형 로딩바가 있는 홈화면 만들기
  - android studio 셋팅
  - 로고 이미지 추가(pubspec.yml 셋팅)
  
```java
import 'package:flutter/material.dart';

void main() {
  runApp(
      MaterialApp(
        debugShowCheckedModeBanner: false,
        home:HomeScreen(),
    ),
  );
}

class HomeScreen extends StatelessWidget{
  @override
  Widget build(BuildContext context) {
    // TODO: implement build
    return Scaffold(
        backgroundColor: Color(0xFFF99231),
        body: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            Image.asset(
                'asset/img/img.png'
            ),
            CircularProgressIndicator(
              color: Colors.white,
            ),
          ],
        ),
      );
  }
}
```
