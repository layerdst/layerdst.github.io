---
layout: default
title: 홈화면 만들기
parent: basic
grand_parent: flutter
nav_order: 6
---


## 강의예제 원형 로딩바가 있는 홈화면 만들기
  - android studio 셋팅
  - 로고 이미지 추가(pubspec.yml 셋팅)
  - 화면 오른쪽 상단 debug 제거 하기 (debugShowCheckedModeBanner 설정) 
  
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

## 결과이미지
<img src = "https://user-images.githubusercontent.com/71206860/190179479-dd023c71-70ba-46cd-9eaa-a8fee881c0f4.png" width="300"/>

