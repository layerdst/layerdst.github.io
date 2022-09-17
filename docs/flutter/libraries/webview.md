## flutter webview 라이브러리를 활용하여 블로그 만들기

## WebView 에 대한 설명
- 웹뷰는 만들고자 하는 플랫폼에 **웹페이지의 화면과 기능을 손쉽게 호출할 수 있는 라이브러리** 이다. 
- 본 예제에서 쓰이는 라이브러리는 webview_flutter 로 범용성이 뛰어나며, [pub.dev](https://pub.dev/). 에서 살펴볼수 있다.
- 라이브러리 선택기준은 like, pub point, popularity 도 있지만 MIT licence 도 고려해야한다.

## flutter webview
- WebViewController 는 웹뷰의 필드 중 하나로서, 웹뷰가 생성되면 인스턴스를 생성해줘야 한다.
- initialUrl 은 플랫폼에서의 첫 화면을 지정하는 것이다.
- javascriptMode 은 웹페이지의 자바스크립트의 기능의 구현을 해제하거나 유지할 수 있다. 기본값은 disabled 이다.

## 코드작성하기

```java
class WebViewScreen extends StatelessWidget {

  WebViewController? webViewController;
  final homeUrl = 'https://layerdst.github.io/docs/flutter/basic';

  @override
  Widget build(BuildContext context) {
    return Scaffold(
        appBar : AppBar(
          backgroundColor: Colors.orange,
          title: Text('Dev'),
          centerTitle: true,
          actions: [
            IconButton(
                onPressed: ()=>{webViewController == null ? null : webViewController!.loadUrl(homeUrl)},
                icon: Icon(Icons.home))
          ],
        ),
        body: WebView(
          onWebViewCreated: (WebViewController webViewController){
            this.webViewController = webViewController;
          },
          initialUrl: 'https://layerdst.github.io/docs/flutter/basic',
          javascriptMode: JavascriptMode.disabled,
      )

    );
  }
}
```

## 결과이미지
