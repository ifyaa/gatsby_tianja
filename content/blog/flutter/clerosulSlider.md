---
title: clerosul slider
date: "2020-07-12"
description: clerosul slider.
---

[# Carousel Slider](https://www.youtube.com/watch?v=SGLyKxTAo00)
![](https://i.ibb.co/2MD5KYh/Screen-Shot-2020-07-12-at-11-22-31-AM.png)


[# Carrossel](https://www.youtube.com/watch?v=YB9Hd1laVB4)


[다른강의들 참고](https://www.youtube.com/channel/UCNQLusaGT0qnCMpK2TBQFAA)

회전하기
[참고사이트](https://medium.com/@quswlals822/flutter-%EC%95%84%EC%9D%B4%EC%BD%98-%EB%8F%8C%EB%A6%AC%EA%B8%B0-7f4914dcc966)
![](https://i.ibb.co/vH0Bq8Q/Screen-Shot-2020-07-12-at-4-35-31-PM.png)

```js
import 'package:flutter/material.dart';

void main() {
  runApp(new RotationIconApp());
}

class RotationIconApp extends StatelessWidget {
  Widget build(BuildContext context) {
    return new MaterialApp(
      title: 'Flutter Deme',
      theme: new ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: new MyHomePage(title: 'icon rotation'),
    );
  }
}

class MyHomePage extends StatefulWidget {
  MyHomePage({Key key, this.title}) : super(key: key);
  final String title;

  @override
  _MyHomePageState createState() => new _MyHomePageState();
}

class _MyHomePageState extends State<MyHomePage> {
  var _position = 0.0;

  @override
  Widget build(BuildContext context) {
    return new Scaffold(
        appBar: new AppBar(
          title: new Text(widget.title),
        ),
        body: new Center(
            child: new Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: <Widget>[
            new Slider(
                value: _position,
                onChanged: (var position) {
                  setState(() {
                    _position = position;
                  });
                }),
            new Transform.rotate(
              angle: _position * 2 * 3.14,
              child: Icon(Icons.android),
            ),
            new Transform.rotate(
              angle: _position * -2 * 3.14,
              child: Icon(Icons.android),
            ),
          ],
        )));
  }
}

```


## slider
![](https://i.ibb.co/KxrW92f/Screen-Shot-2020-07-12-at-4-54-55-PM.png)

```js
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Slider Demo',
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: MyHomePage(title: 'Flutter Slider Demo Home Page'),
    );
  }
}

class MyHomePage extends StatefulWidget {
  MyHomePage({Key key, this.title}) : super(key: key);

  final String title;

  @override
  _MyHomePageState createState() => _MyHomePageState();
}

class _MyHomePageState extends State<MyHomePage> {
  double _value = 0.5;

  @override
  Widget build(BuildContext context) {
    return Scaffold(
        appBar: AppBar(
          title: Text(widget.title),
        ),
        body: Slider(
          value: _value,
          onChanged: (double newValue) {
            setState(() {
              _value = newValue;
            });
          },
        ));
  }
}
```





<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0NTMzNTk3OTIsMzk0ODQxNDEyLC00OD
MyMzQ0ODEsLTE5MDc0MDA1NTNdfQ==
-->