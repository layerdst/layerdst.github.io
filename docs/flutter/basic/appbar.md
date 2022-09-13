## 앱바 아이콘 추가하기
- 앱바 상단 왼쪽의 햄버거 IconButton 을 이용해 아이콘 추가하기
- IconButton 은 icon 과 같이 onPressed 함수와 같이 사용되어야 함.

```java
class MyApp extends StatelessWidget {
  const MyApp({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'AppBar',
      theme: ThemeData(primarySwatch: Colors.red),
      home: MyPage(),
    );
  }
}

class MyPage extends StatelessWidget {
  const MyPage({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
        appBar: AppBar(
      title: Text('Appbar Icon Menu'),
      centerTitle: true,
      elevation: 0.0,
      leading: IconButton(
        icon: Icon(Icons.menu),
        onPressed: () {
          print('menu btn clicked');
        },
      ),
    ));
  }
}
```