---
layout: default
title: LogIn
parent: ex
grand_parent: flutter
nav_order: 1
---

## 로그인 화면 구현하기
- AppBar 상단 왼쪽 메뉴, 오른쪽 검색 아이콘 만들기
- Body 에는 이미지와 Form 으로 구성되어있다.
- Form 은 두개의 텍스트 필드와 한개의 버튼으로 구성된다.
- Form 내의 상단 Input 필드는 keyboardType 이 email 이다.
- Form 내의 하단 Input 필드는 keyboardType 이 text 이다.
- Form 하단 버튼은 ElevatedButton 을 활용한다.

## 코드 작성
```java


import 'package:flutter/material.dart';

class Dice extends StatelessWidget {
  const Dice({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      title:'Dice game',
      home:LogIn(),
    );
  }
}

class LogIn extends StatefulWidget{
  @override
  State<LogIn> createState() => _LogInState();
}




class _LogInState extends State<LogIn> {

  TextEditingController controller = TextEditingController();
  TextEditingController controller2 = TextEditingController();

  @override
  Widget build(BuildContext context) {
    // TODO: implement build
    return Scaffold(
      appBar: AppBar(
        title: Text('Log in'),
        backgroundColor: Colors.redAccent,
        centerTitle: true,
        leading: IconButton(
          icon:Icon(Icons.menu),
          onPressed: (){},
        ),
        actions: [
          IconButton(onPressed: (){}, icon: Icon(Icons.search))
        ],
      ),
      body: Builder(
        builder: (context){
          return GestureDetector(
            onTap: ()=>{
              FocusScope.of(context).unfocus()
            },
            child: SingleChildScrollView(
              child: Column(
                children: [
                  const Padding(padding: EdgeInsets.only(top: 50)),
                  const Center(
                    child: Image(
                      image: AssetImage('image/flutter.png'),
                      width: 170.0,
                      height: 190,


                    ),
                  ),
                  Form(
                    child: Theme(
                      data:ThemeData(
                          primaryColor: Colors.teal,
                          inputDecorationTheme: InputDecorationTheme(
                              labelStyle: TextStyle(
                                  color: Colors.teal,
                                  fontSize: 15.0
                              )
                          )
                      ),

                      child: Container(
                        padding: const EdgeInsets.all(40.0),
                        child: Column(
                          children: [
                            TextField(
                              controller: controller,
                              decoration: InputDecoration(
                                  labelText: 'Enter dice'
                              ),
                              keyboardType: TextInputType.emailAddress,
                            ),
                            TextField(
                              controller: controller2,
                              decoration: InputDecoration(
                                  labelText: 'Enter password'
                              ),
                              keyboardType: TextInputType.text,
                              obscureText: true,
                            ),
                            SizedBox(height: 40.0),
                            ElevatedButton(
                              child: Icon(Icons.arrow_forward, color:Colors.white, size: 35.0,),
                              onPressed: () {
                                if (controller.text == 'dice' && controller2.text == '1234') {
                                  Navigator.push(context,
                                      MaterialPageRoute(builder: (BuildContext context)=>Dices()));
                                }else if(controller.text=='dice' && controller2.text != '1234'){
                                      showSnackBar(context, Msg.pwErr);
                                }else if(controller.text!='dice'&& controller2.text == '1234'){
                                      showSnackBar(context, Msg.diceErr);
                                }else{
                                      showSnackBar(context, Msg.good);
                                }
                              },

                            ),
                          ],
                        ),
                      ),
                    ),
                  )
                ],
              ),
            ),
          );
        },
      ),
    );
  }
}

class Dices extends StatelessWidget{
  @override
  Widget build(BuildContext context) {
    // TODO: implement build
    return Scaffold(
      backgroundColor: Colors.red,
      appBar: AppBar(
        backgroundColor: Colors.red,
        title: Text('Dice game'),
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            Padding(
              padding: EdgeInsets.all(32.0),
              child: Row(
                mainAxisAlignment: MainAxisAlignment.center,
                children: [
                  Expanded(child: Image(image: AssetImage('image/dice/dice1.png'))),
                  SizedBox(width: 20.0,),
                  Expanded(child: Image(image: AssetImage('image/dice/dice2.png')))
                ],
              ),
            ),
            SizedBox(
              height: 60.0,
            ),
            ButtonTheme(
                minWidth:100.0,
                height: 60.0,

                child: ElevatedButton(
                  onPressed: (){},
                  child: Icon(Icons.arrow_forward,
                    color: Colors.white,
                    ),
                )
            )
          ],
        )
      )
    );
  }
}

void showSnackBar(BuildContext context, String msg){
  ScaffoldMessenger.of(context).showSnackBar(
    SnackBar(content:
      Text(msg, textAlign: TextAlign.center,),
      duration: Duration(seconds: 2),
      backgroundColor: Colors.blue,
    )
  );
}

class Msg{
  static String good = "로그인정로를 확인하세요" ;
  static String pwErr = "비밀번호를 확인하세요" ;
  static String diceErr = "dice 철자를 확인하세요" ;

}

```

## 결과이미지
<img src = "https://user-images.githubusercontent.com/71206860/192154310-5a30ceba-c3db-477e-81cf-f4d856c89327.png" width = "300"/>
