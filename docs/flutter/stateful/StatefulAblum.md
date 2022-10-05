## Stateful, PageView Wiget을 활용한 carousel 앨범 만들기 


```java
import 'dart:async';

import 'package:flutter/material.dart';
import 'package:flutter/services.dart';

class Album extends StatefulWidget {
  const Album({Key? key}) : super(key: key);

  @override
  State<Album> createState() => _AlbumState();
}

class _AlbumState extends State<Album> {

  Timer? timer;
  PageController controller = PageController(
    initialPage: 0,
  );

  @override
  void initState() {
    super.initState();
    timer = Timer.periodic(Duration(seconds: 1), (timer) {
      int currentPage = controller.page!.toInt();
      int nextPage = currentPage+1;
      if(nextPage>4){
        nextPage = 0;
      }
      controller.animateToPage(nextPage, duration: Duration(milliseconds: 2000), curve: Curves.linear);
    });
  }

  @override
  void dispose() {
    controller.dispose();
    if(timer != null){
      timer!.cancel();
    }
    super.dispose();
  }

  @override
  Widget build(BuildContext context) {
    SystemChrome.setSystemUIOverlayStyle(SystemUiOverlayStyle.dark);
    return Scaffold(
      body:PageView(
        controller: controller,
        children: [1,2,3,4,5].map(
            (e) => Image.asset('image/album/image_$e.jpeg', fit: BoxFit.cover)
        ).toList(),
      )
    );
  }
}
```
