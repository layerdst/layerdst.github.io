

### Stateful LifeCycle 구현해보기



```java
class LifeCycle extends StatefulWidget {
  const LifeCycle({Key? key}) : super(key: key);

  @override
  State<LifeCycle> createState() => _LifeCycleState();
}

class _LifeCycleState extends State<LifeCycle> {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: LifeCycleBody()
    );
  }
}

class LifeCycleBody extends StatefulWidget {
  const LifeCycleBody({Key? key}) : super(key: key);

  @override
  State<LifeCycleBody> createState() => _LifeCycleBodyState();
}

class _LifeCycleBodyState extends State<LifeCycleBody> {
  Color colors = changeColors();
  @override
  Widget build(BuildContext context) {
    return Container(
      padding: EdgeInsets.all(10.0),
      child :
        Padding(
          padding: EdgeInsets.all(20.0),
          child:
            Column(
              mainAxisAlignment: MainAxisAlignment.spaceBetween,
              children: [
                Expanded(child: Center(child : cycleSquare(colors))),
                columnButton(colors)
            ]
          ),
        ),
    );
  }

  ElevatedButton styleButton(String msg, Color color) {
    return ElevatedButton(
      onPressed: (){
        setState(() {
          color == Colors.red ? cycleSquare(Colors.blue) : cycleSquare(Colors.red) ;
          print("state ${color}");
          print("clicked");
          print(msg);
        });
      },
      child: Text(msg),
    );
  }

  Column columnButton(Color color) {
    return Column(
      mainAxisAlignment: MainAxisAlignment.center,
      crossAxisAlignment: CrossAxisAlignment.stretch,
      children: [
        styleButton("색깔변경하기", color),
        SizedBox(width: 100),
      ],
    );
  }

  Container cycleSquare(Color color) {
    Container ex = Container(
        width: 50.0,
        height: 50.0,
        color : color
    );
    print("싸이클 + ${color}");
    return ex;
  }

  static Color changeColors({Color? c}) {
    return c != null ? (c==Colors.red ? Colors.blue : Colors.red) : Colors.blue;
  }
}
```
