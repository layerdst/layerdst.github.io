---
layout: default
title: 기본 화면
parent: align
grand_parent: flutter
nav_order: 2
---

## 정렬 속성을 사용하여 아래의 이미지를 구현
- 해당 화면은 SafeArea 를 적용한다.
- Column 과 Row 를 사용한다. 
- 각 줄의 Row 들의 간격은 동일하며, 맨 윗여백과 아래여백도 마찬가지로 동일하다.
- 첫 줄의 이미지는 각 이미지의 간격은 동일하나, 맨앞과 뒤는 이미지 간격의 1/2이다. 
- 두번째줄 이미지는 가운데에 고정되어 있다.
- 세번째줄 이미지는 오른쪽 끝에서 나열되 있다. 
- 네번째줄 이미지는 가운데에 고정되어 있다.spaceEvenly 

## 구현할 이미지
<img src = "https://user-images.githubusercontent.com/71206860/190420940-739d1cb9-ff36-435c-a3c0-49ab0ea49470.png" width = "300" />



## 첫번째 구현 - 각줄의 위아래 여백이 동일하지 않음
  - Expanded 를 활용해서 공백줄을 만들었으나, 각 줄마다 여백이 동일하지 않았다.

```java
class HomeScreen extends StatelessWidget {
  const HomeScreen({Key? key}) : super(key: key);

  Row blackRow(){
   return Row(
       children: [
         Expanded(
           child: Container(
             color: Colors.black,
             height: 50.0,
           ),
         )
       ],
     );
  }

  Container changeColorBrick(String colors){
    return Container(
      color: searchColor(colors),
      width: 50.0,
      height: 50.0,
    );
  }

  Color searchColor(String color){
    switch(color){
      case "black" :  {return Colors.black;} break;
      case "red" : {return Colors.red;} break;
      case "orange" : {return Colors.orange;} break;
      case "yellow" : {return Colors.yellow;} break;
      case "green" : {return Colors.green;} break;
      default : {return Colors.black;} break;
    }
  }
  
  @override
  Widget build(BuildContext context) {
    return Scaffold(
        body: SafeArea( //
          child: Container(
            // width: MediaQuery.of(context).size.width,
            mainAxisAlignment: MainAxisAlignment.spaceEvenly,
            color:Colors.black,
            child: Column(
              children: [
                blackRow(),
                Row(
                  mainAxisAlignment: MainAxisAlignment.spaceAround,
                  children: [
                    changeColorBrick("red"),
                    changeColorBrick("orange"),
                    changeColorBrick("yellow"),
                    changeColorBrick("green")
                  ],
                ),
                blackRow(),
                Row(
                mainAxisAlignment: MainAxisAlignment.center,
                  children: [
                    changeColorBrick("orange")
                  ],
                ),
                blackRow(),
                Row(
                  mainAxisAlignment: MainAxisAlignment.end,
                  children: [
                    changeColorBrick("red"),
                    changeColorBrick("orange"),
                    changeColorBrick("yellow"),
                    changeColorBrick("green")
                  ],
                ),
                blackRow(),
                Row(
                  mainAxisAlignment: MainAxisAlignment.center,
                  children: [
                    changeColorBrick("green")
                  ],
                )

              ],
            ),
          ),
        ),
    );
  }
```

## 첫번째 구현 이미지
<img src = "https://user-images.githubusercontent.com/71206860/190420732-18233162-8ba5-40de-ad88-daf7398d6952.png" width="300"/>



## 두번째 구현 - 완성

```java
@override
  Widget build(BuildContext context) {
    return Scaffold(
      body: SafeArea(
        child: Container(
          color: Colors.black,
          child: Column(
            mainAxisAlignment: MainAxisAlignment.spaceEvenly,
            children: [
              Row(
                mainAxisAlignment: MainAxisAlignment.spaceAround,
                children: [
                  changeColorBrick("red"),
                  changeColorBrick("orange"),
                  changeColorBrick("yellow"),
                  changeColorBrick("green"),
                ],
              ),
              Row(
                mainAxisAlignment: MainAxisAlignment.center,
                children: [
                  changeColorBrick("orange")
                ],
              ),
              Row(
                mainAxisAlignment: MainAxisAlignment.end,
                children: [
                  changeColorBrick("red"),
                  changeColorBrick("orange"),
                  changeColorBrick("yellow"),
                  changeColorBrick("green"),
                ],
              ),
              Row(
                mainAxisAlignment: MainAxisAlignment.center,
                children: [
                changeColorBrick("green"),
                ]
              ),
            ],
          )

        ),
      ),
    );
  }

```
