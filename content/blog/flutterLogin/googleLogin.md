---
title: flutterLogin
date: "2020-07-16"
description: googleLogin
---
[google Login](https://fkkmemi.github.io/ff/ff-001/)
[동영상](https://dev.to/happyharis/flutter-web-google-sign-in-42bb)

### Runner.xcworkspace

 open ios/Runner.xcworkspace. 
![](https://i.ibb.co/nRG8Cvm/Screen-Shot-2020-09-19-at-4-13-38-PM.png =300x300)
### 5장 화면전환
![](https://fkkmemi.github.io/images/ff/2019-12-11_15.53.18.gif)
```js
import 'package:firebase_auth/firebase_auth.dart';
import 'package:flutter/material.dart';
import 'package:google_sign_in/google_sign_in.dart';


void main(){
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context){
    return MaterialApp(
      home: HomeWidget()
    );
  }
}

class AppState {
  bool loading;
  String user;
  AppState(this.loading, this.user);
}

class HomeWidget extends StatefulWidget{
  @override
  _HomeWidgetState createState() => _HomeWidgetState();
}

class _HomeWidgetState extends State<HomeWidget> {
  final FirebaseAuth _auth = FirebaseAuth.instance;
  final GoogleSignIn _googleSignIn = googleSignIn(;
  final app = AppState(true, '');

_delay(){
  Future.delayed(Duration(seconds: 1), (){
    setState(()=> app.loading = false);
  });
}

@override
void initState(){
  super.initState();
  _delay();
}


  @override
  Widget build(BuildContext context){
    if(app.loading) return _loaging();
    if(app.user.isEmpty) return _signIn();
    return _main();
  }


Widget _loaging(){
  return Scaffold(
    appBar: AppBar(title: Text('loading...')),
    body: Center(child: CircularProgressIndicator(),)
  );
}

Widget _signIn(){
  return Scaffold(
    appBar: AppBar(
      title: Text('login page')
    ),
    body: Center(
      child: Column(
        mainAxisAlignment: MainAxisAlignment.center,
        crossAxisAlignment: CrossAxisAlignment.center,
        children: <Widget>[
          Text('id'), Text('pass'),
          RaisedButton(
            child: Text('login'),
            onPressed: (){
              setState((){
                app.loading = true;
                app.user = 'myname';
                _delay();
              });
            },
          )
        ],
      )
    )
  );
}

Widget _main(){
  return Scaffold(
    appBar: AppBar(
    title: Text(app.user),
    actions: <Widget>[
      IconButton(
        icon: Icon(Icons.account_circle),
        onPressed: () {
          setState(() {
            app.user = '';
            app.loading = true;
            _delay();
          });
        },
      )
    ]
  ),
  body: Center(child: Text('contents'),)
  );
}
}
```


> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE5NTk5NDc3MDIsMzIwODkyNTQ4LDg0ND
M1MDgzNywzMjM1MTUzOTEsLTEyOTY3NjMyNjFdfQ==
-->