## 이미지와 텍스트 나열하기
- AppBar 의 이름은 BBanTo 이다.
- body 내 순서는 이미지, 작은 텍스트, 큰 텍스트, 작은 텍스트, 아이콘, 이미지 순으로 배치한다.
- 모든 텍스트의 정렬은 왼쪽 정렬로, CrossAxisAlignment.start 를 적용한다.
- 첫 이미지 아래에 있는 회색 라인은 Divider 위젯을 사용한다.
- 각 영역의 공백은 SizedBox 를 활용한다.


```java
class MyApp extends StatelessWidget {
  const MyApp({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      title: 'BBAnsTo',
      home: Grade(),
    );
  }
}

class Grade extends StatelessWidget {
  const Grade({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: Colors.amber[800],
      appBar: AppBar(
        title: Text('BBanTo'),
        backgroundColor: Colors.amber[700],
        centerTitle: true,
        elevation: 0.0,
      ),
      body: Padding(
        padding: EdgeInsets.fromLTRB(30.0, 40.0, 0.0, 0.0),
        child: Column(
            crossAxisAlignment: CrossAxisAlignment.start,
            children: <Widget>[
              Center(
                child: CircleAvatar(
                  backgroundImage: AssetImage('assets/ddong2.png'),
                  radius: 60.0,
                ),
              ),
              Divider(
                height: 60.0,
                color: Colors.grey[850],
                thickness: 0.5,
                endIndent: 30.0,
              ),
              Text('Name',
                  style: TextStyle(
                    color: Colors.white,
                    letterSpacing: 2.0,
                  )),
              SizedBox(
                height: 10.0,
              ),
              Text(
                'BBANTO',
                style: TextStyle(
                    color: Colors.white,
                    letterSpacing: 2.0,
                    fontSize: 28.0,
                    fontWeight: FontWeight.bold),
              ),
              SizedBox(
                height: 30.0,
              ),
              Text(
                'BBANTO POWER LEVEL',
                style: TextStyle(color: Colors.white, letterSpacing: 2.0),
              ),
              SizedBox(height: 10.0),
              Text('14',
                  style: TextStyle(
                      color: Colors.white,
                      letterSpacing: 2.0,
                      fontSize: 20.0,
                      fontWeight: FontWeight.bold)),
              SizedBox(
                height: 25.0,
              ),
              Row(
                children: <Widget>[
                  Icon(Icons.check_circle_outline),
                  SizedBox(
                    width: 10.0,
                  ),
                  Text(
                    'using lightsaber',
                    style: TextStyle(fontSize: 16.0, letterSpacing: 1.0),
                  ),
                ],
              ),
              SizedBox(
                height: 10.0,
              ),
              Row(
                children: <Widget>[
                  Icon(Icons.check_circle_outline),
                  SizedBox(
                    width: 10.0,
                  ),
                  Text(
                    'face hero tattoo',
                    style: TextStyle(fontSize: 16.0, letterSpacing: 1.0),
                  ),
                ],
              ),
              SizedBox(
                height: 10.0,
              ),
              Row(
                children: <Widget>[
                  Icon(Icons.check_circle_outline),
                  SizedBox(
                    width: 10.0,
                  ),
                  Text(
                    'title Flame',
                    style: TextStyle(fontSize: 16.0, letterSpacing: 1.0),
                  ),
                ],
              ),
              Center(
                child: CircleAvatar(
                  backgroundImage: AssetImage('assets/ddong3.png'),
                  radius: 40.0,
                  backgroundColor: Colors.amber[800],
                ),
              )
            ]),
      ),
    );
  }
}
```

## 결과 이미지
