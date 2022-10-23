## 랜덤숫자 생성기
- header, body, footer 세 영역을 디자인
- body 부분의 숫자들은 버튼을 누를때마다 임의의 숫자들이 생성된다. 

## 결과 코드
```java
import 'dart:math';
import 'package:flutter/material.dart';

const Color PRIMARY_COLOR = Color(0xFF2D2D33);
const Color RED_COLOR = Color(0xFFEA4955);
const Color BLUE_COLOR = Color(0xFF548FBF);

class RandomNumber extends StatefulWidget {
  const RandomNumber({Key? key}) : super(key: key);

  @override
  State<RandomNumber> createState() => _RandomNumberState();
}

class _RandomNumberState extends State<RandomNumber> {

  List<int> randomNums = [
    123,
    456,
    789,
  ];

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: PRIMARY_COLOR,
      body: SafeArea(
        child: Padding(
          padding: const EdgeInsets.symmetric(
            horizontal: 16.0
          ),
          child: Column(
            crossAxisAlignment: CrossAxisAlignment.start,
            children: [
              _Header(),
              _Body(randomNums: randomNums),
              _Footer(onPressed: onNumberGenerator)

            ],
          ),
        ),
      )
    );
  }

  void onNumberGenerator(){
      final rand = Random();
      final Set<int> tempNums = {};

      while(tempNums.length != 3){
        final number = rand.nextInt(10000);
        tempNums.add(number);
      }
      setState(() {
        randomNums = tempNums.toList();
      });
  }
}


class _Header extends StatelessWidget {
  const _Header({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Row(
        mainAxisAlignment: MainAxisAlignment.spaceBetween,
        children :[
          Text('랜덤숫자생성기', style: TextStyle(color: Colors.white, fontSize: 30.0, fontWeight: FontWeight.w700),),
          IconButton(
              onPressed: (){},
              icon: Icon(
                Icons.settings,
                color : RED_COLOR,)
          )
        ]
    );
  }
}

class _Body extends StatelessWidget {
  final List<int> randomNums;
  const _Body({required this.randomNums, Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Expanded(
        child: Column(
            mainAxisAlignment: MainAxisAlignment.center,
            children: randomNums
                .asMap()
                .entries
                .map(
                    (x)=> Padding(
                  padding: EdgeInsets.only(bottom: x.key == 2 ? 0 : 16.0),
                  child: Row(
                      children: x.value
                          .toString()
                          .split('')
                          .map(
                            (y)=>Image.asset(
                            'image/random/$y.png',
                            width: 50.0,
                            height: 70.0
                        ),
                      ).toList()
                  ),
                )
            ).toList()
        )
    );
  }
}

class _Footer extends StatelessWidget {
  final VoidCallback onPressed;
  const _Footer({required this.onPressed, Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return SizedBox(
      width: double.infinity,
      child: ElevatedButton(
          style: ElevatedButton.styleFrom(
              primary: RED_COLOR),
          onPressed: onPressed,
          child: Text('생성하기 !')
      ),
    );
  }
}
```

## 결과 
<image src = "https://user-images.githubusercontent.com/71206860/197398103-5537cc73-c108-4b65-b561-0697308eb01f.png" width="300"/>

