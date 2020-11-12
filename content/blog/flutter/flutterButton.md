---
title: flotter 버튼모음
date: "2020-07-15"
	description: flotter 버튼모음.
---

[그리고 그외 참고할 것들](https://pythonkim.tistory.com/category/%ED%94%8C%EB%9F%AC%ED%84%B0)

가장 많이 사용하는 [RaisedButton](https://docs.flutter.io/flutter/material/RaisedButton/RaisedButton.html), 버튼 눌림 기능이 없는 [FlatButton](https://docs.flutter.io/flutter/material/FlatButton/FlatButton.html),  
상단 제목의 왼쪽이나 오른쪽에 주로 들어가는 [IconButton](https://docs.flutter.io/flutter/material/IconButton/IconButton.html)(프린터),  
안드로이드에서 주로 사용하는 공중에 떠있는 듯한 [FloatingActionButton](https://docs.flutter.io/flutter/material/FloatingActionButton/FloatingActionButton.html),  
버튼은 아니지만 버튼처럼 사용할 수 있는 [InkWell](https://docs.flutter.io/flutter/material/InkWell/InkWell.html),  
마지막으로 사진으로 만든 버튼까지.  
  
출처: [https://pythonkim.tistory.com/115](https://pythonkim.tistory.com/115) [파이쿵]
![](https://i.ibb.co/pf3fSrs/Screen-Shot-2020-07-15-at-3-13-39-PM.png)
```js
import 'package:flutter/material.dart';

void main() {
    runApp(MaterialApp(
        title: '버튼 종류',
        home: Scaffold(
            appBar: AppBar(title: Text('버튼 종류'),),
            body: MyApp(),
        ),
    ));
}

class MyApp extends StatelessWidget {
    BuildContext ctx;
    
    @override
    Widget build(BuildContext context) {
        ctx = context;
        return Center(
            child: Column(
                children: <Widget>[
                    RaisedButton(
                        child: Text('RaisedButton', style: TextStyle(fontSize: 24)),
                        onPressed: () => showMessage('RaisedButton'),
                    ),
                    FlatButton(
                        child: Text('FlatButton', style: TextStyle(fontSize: 24)),
                        onPressed: () => showMessage('FlatButton'),
                        color: Colors.green,
                        textColor: Colors.white,
                    ),
                    IconButton(
                        icon: Icon(Icons.print),
                        onPressed: () => showMessage('IconButton'),
                    ),
                    FloatingActionButton(
                        child: Icon(Icons.add),
                        onPressed: () => showMessage('FloatingActionButton'),
                    ),
                    InkWell(
                        child: Text('InkWell', style: TextStyle(fontSize: 24)),
                        onTap: () => showMessage('InkWell'),
                    ),
                    InkWell(
                        child: Image.asset('images/family_1.jpg', width: 120, height: 120),
                        onTap: () => showMessage('ImageButton'),
                    ),
                ],
                mainAxisAlignment: MainAxisAlignment.spaceEvenly,
            ),
        );
    }
    
    void showMessage(String msg) {
        final snackbar = SnackBar(content: Text(msg));

        Scaffold.of(ctx)
            ..removeCurrentSnackBar()
            ..showSnackBar(snackbar);
    }
}


출처: https://pythonkim.tistory.com/115 [파이쿵]
```

[flutter world](https://www.youtube.com/watch?v=GDWl6_RW9co&list=PUxJInPa5SMldFHfJreSJ73Q)
![](https://i.ibb.co/rbbLT30/Screen-Shot-2020-07-13-at-11-25-57-AM.png)
![](https://i.ibb.co/f4bfLQV/Screen-Shot-2020-07-15-at-5-35-28-PM.png)
```js
import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: "alert Dialog Example",
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: MyHomePage(),
    );
  }
}

class MyHomePage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
        appBar: AppBar(
          title: Text("Alert Dialog"),
          centerTitle: true,
        ),
        body: Column(
          children: <Widget>[
            RaisedButton(
              child: Text("Simple Dialog!!"),
              onPressed: () {
                showDialog(
                    context: context,
                    builder: (context) {
                      return AlertDialog(
                        title: Text("hello Everyone"),
                        content: Text("This is a body from Alert Dilog"),
                        actions: <Widget>[
                          FlatButton(
                            child: Text("yes"),
                            onPressed: () {},
                          ),
                          FlatButton(
                            child: Text("no"),
                            onPressed: () {},
                          )
                        ],
                      );
                    });
              },
            ),
            RaisedButton(
              child: Text("Custom Dialog"),
              onPressed: () {
                showDialog(
                    context: context,
                    builder: (context) {
                      return Dialog(
                          shape: RoundedRectangleBorder(
                            borderRadius: BorderRadius.circular(20.0),
                          ),
                          child: Container(
                              height: 200,
                              child: Padding(
                                  padding: EdgeInsets.all(12.0),
                                  child: Column(
                                      crossAxisAlignment:
                                          CrossAxisAlignment.start,
                                      mainAxisAlignment:
                                          MainAxisAlignment.center,
                                      children: <Widget>[
                                        TextField(
                                          decoration: InputDecoration(
                                              border: InputBorder.none,
                                              hintText:
                                                  "What do you wang from Byneet Dev?"),
                                        ),
                                        SizedBox(
                                            width: 320,
                                            child: RaisedButton(
                                                color: Colors.red[50],
                                                onPressed: () {},
                                                child: Text("confirm",
                                                    style: TextStyle(
                                                      color: Colors.black45,
                                                    ))))
                                      ]))));
                    });
              },
            ),
            RaisedButton(
              child: Text("Click Here"),
              onPressed: () {
                showDialog(
                    context: context,
                    builder: (context) => CustomDialog(
                        title: "Success",
                        description:
                            "Lorem50 우리는 민족중흥의 역사적 사명을 띄고 이땅에 태어났다 안으로 민족중흥에 이바지 하고 밖으로 인류공영에 이바지 하여야 한다 "));
              },
            )
          ],
        ));
  }
}

class CustomDialog extends StatelessWidget {
  final String title, description, buttonText;
  final Image image;

  CustomDialog({this.title, this.description, this.buttonText, this.image});
  @override
  Widget build(BuildContext context) {
    return Dialog(
      shape: RoundedRectangleBorder(borderRadius: BorderRadius.circular(16)),
      elevation: 0,
      backgroundColor: Colors.transparent,
      child: dialogContent(context),
    );
  }

  dialogContent(BuildContext context) {
    return Stack(
      children: <Widget>[
        Container(
            padding: EdgeInsets.only(top: 100, bottom: 16, left: 16, right: 16),
            margin: EdgeInsets.only(top: 16),
            decoration: BoxDecoration(
                color: Colors.white,
                shape: BoxShape.rectangle,
                borderRadius: BorderRadius.circular(17),
                boxShadow: [
                  BoxShadow(
                    color: Colors.black26,
                    blurRadius: 10.0,
                    offset: Offset(0.0, 10.0),
                  )
                ]),
            child: Column(mainAxisSize: MainAxisSize.min, children: <Widget>[
              Text(
                title,
                style: TextStyle(
                  fontSize: 24.0,
                  fontWeight: FontWeight.w700,
                ),
              ),
              SizedBox(height: 16.0),
              Text(description, style: TextStyle(fontSize: 16.0)),
              SizedBox(height: 24.0),
              Align(
                  alignment: Alignment.bottomRight,
                  child: FlatButton(
                    onPressed: () {
                      Navigator.pop(context);
                    },
                    child: Text("Confirm"),
                  ))
            ])),
        Positioned(
            top: 0,
            left: 16,
            right: 16,
            child: CircleAvatar(
              backgroundColor: Colors.blueAccent,
              radius: 50,
              backgroundImage: AssetImage('images/cats/test.png'),
            ))
      ],
    );
  }
}

```
> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTMyMzY3NjgyMSwtMTgxMDY4NDcyMywtMT
U0NTcwNjM0NCwtMTQ1MDA2MzA4M119
-->