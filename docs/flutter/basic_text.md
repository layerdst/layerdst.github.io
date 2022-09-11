## 텍스트 문장을 나열하기
- AppBar 에 이름은 First App 으로 지정한다.
- body 에 hello1, hello2, hello3 3 문장을 나열한다.
- MerialApp 과 Scaffold 위젯을 사용한다.
```java
class MyApp extends StatelessWidget {
  const MyApp({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'First App',
      theme: ThemeData(primarySwatch: Colors.blue),
      home: MyHomePage(),
    );
  }
}

class MyHomePage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('First App'),
      ),
      body: Center(
        child: Column(
          children: <Widget>[Text('hello'), Text('hello2'), Text('hello3')],
        ),
      ),
    );
  }
}
```

## 결과 이미지
<img src="https://user-images.githubusercontent.com/71206860/189519028-12aacf96-de6b-4b26-8e08-1df0060beddb.png" width="300">

