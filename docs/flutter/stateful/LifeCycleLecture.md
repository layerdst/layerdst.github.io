## 라이프 사이클 구현하기
- stateful 에서의 consturctor, createState, initState, didChangeDepencies, deactive, dispose 실행 순서 확인하기

```java
import 'package:flutter/material.dart';

class LifeCycle extends StatefulWidget {
  LifeCycle({Key? key}) : super(key: key){
  }

  @override
  State<LifeCycle> createState() {
    return _LifeCycleState();
  }
}

class _LifeCycleState extends State<LifeCycle> {
  Color color = Colors.blue;
  bool show = false;
  @override
  Widget build(BuildContext context) {
    return Scaffold(
     body: SafeArea(
       child: Padding(
         padding: const EdgeInsets.symmetric(horizontal: 8.0),
         child : Column(
           children: [
             Expanded(child: Center(
                child: show ? HomeScreen(color: color) : Container()
              )
             ),
             Column(
               crossAxisAlignment: CrossAxisAlignment.stretch,
               children: [
                 ElevatedButton(
                     onPressed: (){
                       setState(() {
                         color = color==Colors.red ? Colors.blue: Colors.red;
                       });
                     },
                     child: Text('색깔변경하기')
                 ),
                 const SizedBox(height: 4.0,),
                 ElevatedButton(onPressed: (){
                   setState(() {
                     show = !show;
                   });
                 }, child: Text(!show ? '위젯생성하기' : '위젯삭제하기'))
               ],
             )
           ],
         )
       ),
     ),
    );
  }
}

class HomeScreen extends StatefulWidget {
  final Color color;
  HomeScreen({
    required this.color,
    Key? key}) : super(key: key){
    print('constructor 실행');
  }

  @override
  State<HomeScreen> createState() {
    print('createState 실행');
    return _HomeScreenState();
  }
}

class _HomeScreenState extends State<HomeScreen> {

  @override
  void initState() {
    print('init State 실행');
    super.initState();
  }

  @override
  void didChangeDependencies() {
    print('didChangeDepencies');
    super.didChangeDependencies();
  }

  @override
  void deactivate() {
    print('deactive 실행');
    super.deactivate();
  }


  @override
  void dispose() {
    print('dispose 실행');
    super.dispose();
  }

  @override
  void didUpdateWidget(covariant HomeScreen oldWidget) {
    print('didUpdateWidget 실행');
    super.didUpdateWidget(oldWidget);
  }

  @override
  Widget build(BuildContext context) {
    print('build실행');
    return Container(
      width: 50.0,
      height: 50.0,
      color : widget.color
    );
  }
}
```
