---
layout: default
title: D-day
parent: example
grand_parent: flutter
nav_order: 2
---


## D-DAY 계산기 만들기 강의
- date 관련 dart api 이용하기
- coupertino 라이브러리 이용하기
- 프로젝트에 사용되는 textStyle 관리는 최상위인 main.dart -> themeData 의 설정을 통해 코드 최소화

## 

```java
*** main dart ***
void main() {
  runApp(
    MaterialApp(
      theme: ThemeData(
        fontFamily: 'sunflower',
        textTheme: TextTheme(
          headline1: TextStyle(color:Colors.white, fontFamily: 'parisienne', fontSize: 80.0),
          headline2: TextStyle(color: Colors.white, fontSize: 30.0),
          bodyText1: TextStyle(color:Colors.white,  fontSize: 30.0),
          bodyText2: TextStyle(color:Colors.white, fontWeight:FontWeight.w700, fontSize: 50.0),
        )
      ),
      home : YouAndIScreen(),
  ));
}

***youAndIScreen dart ***
import 'package:flutter/cupertino.dart';
import 'package:flutter/material.dart';

class YouAndIScreen extends StatefulWidget {
  const YouAndIScreen({Key? key}) : super(key: key);
  @override
  State<YouAndIScreen> createState() => _YouAndIScreenState();
}

class _YouAndIScreenState extends State<YouAndIScreen> {

  DateTime seletedDate = _Now().date;

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: Colors.pink[100],
      body: Center(
        child: SafeArea(
          bottom: false,
          child: Container(
            width: MediaQuery.of(context).size.width,
            child: Column(
              children: [
                _TopPart(
                  seletedDate: seletedDate,
                  onPressed: onHeartPressed,
                ),
                _BottomPart()
              ],
            )
          ),
        ),
      ),
    );
  }

  void onHeartPressed(){
    showCupertinoDialog(
      context: context,
      barrierDismissible: true,
      builder: (BuildContext context){
        return Align(
          alignment: Alignment.bottomCenter,
          child: Container(
            color:Colors.white,
            height: 300.0,
            child: CupertinoDatePicker(
              mode : CupertinoDatePickerMode.date,
              initialDateTime: seletedDate,
              maximumDate: _Now().date,
              onDateTimeChanged: (DateTime date){

                setState(() {
                  seletedDate = date;
                });

              },
            ),
          ),
        );
      }
    );
  }
}


class _TopPart extends StatelessWidget {
  final DateTime seletedDate;
  final VoidCallback onPressed;

  _TopPart({
    required this.seletedDate,
    required this.onPressed,
    Key? key}) : super(key:key);

  @override
  Widget build(BuildContext context) {
    final theme = Theme.of(context);
    return Expanded(
      child: Column(
      mainAxisAlignment: MainAxisAlignment.spaceEvenly,
        children: [
          Text('U & I', style: theme.textTheme.headline1,),
          Column(
            children: [
              Text('D-DAY', style: theme.textTheme.headline2,),
              Text('${seletedDate.year}.${seletedDate.month}.${seletedDate.day}', style: theme.textTheme.bodyText1,),],),
          IconButton(
              iconSize: 60.0,
              onPressed: onPressed,
              icon: Icon(Icons.favorite, color: Colors.red,)),
          Text('D+${
            _Now().date.difference(seletedDate).inDays + 1
          }', style: theme.textTheme.bodyText2,)
        ],
      ),
    );
  }
}

class _BottomPart extends StatelessWidget {
  const _BottomPart({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Expanded(child: Image.asset('asset/img/middle_image.png'));
  }
}

class _Now{
  final date = DateTime(DateTime.now().year, DateTime.now().month, DateTime.now().day);
}

```

## 결과이미지

<img src = "https://user-images.githubusercontent.com/71206860/196222353-cf0ae422-98fe-49a3-b307-48578783c46b.png" width="300"/>

