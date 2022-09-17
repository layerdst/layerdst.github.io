## 페이지뷰를 활용한 

## introduction screen 를 활용하여 움직이는 페이지뷰 만들기
- 해당 페이지는 앱/웹의 맨 처음 이용할때 사용되는 소개페이지와 유사한 형태이다.
- PageViewModel 3페이지, 메인화면으로 이동하는 1개 페이지, 총 4개의 페이지로 구성된다.
- IntroductionScreen 내 pages 는 각각 PageViewModel 로 만들며, title, body, image, decoration 속성을 이용할 수 있다.
- 페이지 하단의 dots 의 버튼들은 에니메이션 속성과 크기를 조절할 수 있다.
- next 버튼과 skip 버튼을 활성화 한다.
- done 은 오른쪽 하단에 위치하여 메인페이지로 이동하는데 사용한다.

## 코드 작성
```java
class OnBoardingScreen extends StatelessWidget {
  const OnBoardingScreen({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return const MaterialApp(
      home: OnBoardingPage(),
    );
  }
}

class MyPage extends StatelessWidget {
  const MyPage({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
       title: const Text('Main Page'),
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            const Text('Main Screen', style : TextStyle(fontSize: 25, fontWeight: FontWeight.bold)),
            ElevatedButton(onPressed: (){
              Navigator.of(context).pushReplacement(
                MaterialPageRoute(builder: (context)=> const OnBoardingPage())
              );
            }, child: const Text('Go to onBoarding screen'))
          ],
        ),
      )
    );
  }
}

class OnBoardingPage extends StatelessWidget {
  const OnBoardingPage({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return IntroductionScreen(
      pages: [
        PageViewModel(
          title:'Test',
          body: 'first Page',
          image: Image.asset('image/flutter.png'),
          decoration: getPageDecoration()
        ),
        PageViewModel(
            title:'Test',
            body: 'second Page',
            image: Image.asset('image/icon_flutter.png'),
            decoration: getPageDecoration()
        ),
        PageViewModel(
            title:'Test',
            body: 'third Page',
            image: Image.asset('image/flutter.png'),
            decoration: getPageDecoration()
        ),

      ],
      done: const Text('Done'),
      onDone: (){
        Navigator.of(context).pushReplacement(MaterialPageRoute(builder: (context)=>const MyPage()));
      },
      next:const Icon(Icons.arrow_forward),
      showSkipButton: true,
      skip:const Text('skip'),
      dotsDecorator: DotsDecorator(
        color:Colors.cyan,
        size:Size(10, 10),
        activeSize: Size(22,10),
        activeShape: RoundedRectangleBorder(
          borderRadius: BorderRadius.circular(24)
        ),
      ),
      curve: Curves.bounceOut,
    );
    

  }

  PageDecoration getPageDecoration(){
    return PageDecoration(
      titleTextStyle: TextStyle(
        fontSize: 28,
        fontWeight: FontWeight.bold,
      ),

      bodyTextStyle: TextStyle(
        fontSize: 18,
        color : Colors.blue
      ),

      imagePadding: EdgeInsets.only(top:40),
      pageColor: Colors.white
    );
  }
}

```

