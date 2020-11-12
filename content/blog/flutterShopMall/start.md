------
title: flutterShoppingMall
date: 2020-05-08
description: flotter 쇼핑몰강의 
---
[강의](https://www.youtube.com/watch?v=nPa-53FXebU&list=PLmnT6naTGy2SC82FMSCrvZNogg5T1H7iF&index=8)

![](https://i.ibb.co/mvJjjfN/flutter04.png)

```js
import 'package:flutter/material.dart';

void main(){
  runApp(
    MaterialApp(
      home: HomePage(),
    )
  );
}

class HomePage extends StatefulWidget {
  @override
  _HomePageState createState() => _HomePageState();
}

class _HomePageState extends State<HomePage> {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: new AppBar(
        backgroundColor: Colors.red,
        title: Text('ShopApp'),
        actions: <Widget> [
          new IconButton(icon: Icon(Icons.search, color: Colors.white,), onPressed: (){}),
          new IconButton(icon: Icon(Icons.shopping_cart, color: Colors.white,), onPressed: (){}),
        ],
      ),
    );
  }
}
```

![](https://i.ibb.co/1z1pDJF/flutter05.png)
```js
import 'package:flutter/material.dart';

void main(){
  runApp(
    MaterialApp(
      home: HomePage(),
    )
  );
}

class HomePage extends StatefulWidget {
  @override
  _HomePageState createState() => _HomePageState();
}

class _HomePageState extends State<HomePage> {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: new AppBar(
        backgroundColor: Colors.red,
        title: Text('Shop'),
        actions: <Widget> [
          new IconButton(icon: Icon(Icons.search, color: Colors.white,), onPressed: (){}),
          new IconButton(icon: Icon(Icons.shopping_cart, color: Colors.white,), onPressed: (){}),
        ],
      ),
      drawer: new Drawer(
        child: new ListView(
          children: <Widget>[
            new UserAccountsDrawerHeader(
              accountName: Text('Santos Enoque'), 
              accountEmail: Text('santosenoque.ss@gmail.com'),
            currentAccountPicture: GestureDetector(
              child: new CircleAvatar(
                backgroundColor: Colors.grey,
              ),
            ),
            )
          ],
        )
      ),
    );
  }
}
```
![](https://i.ibb.co/26mLczq/flutter06.png)

```js
import 'package:flutter/material.dart';

void main(){
  runApp(
    MaterialApp(
      home: HomePage(),
    )
  );
}

class HomePage extends StatefulWidget {
  @override
  _HomePageState createState() => _HomePageState();
}

class _HomePageState extends State<HomePage> {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: new AppBar(
        backgroundColor: Colors.red,
        title: Text('Shop'),
        actions: <Widget> [
          new IconButton(icon: Icon(Icons.search, color: Colors.white,), onPressed: (){}),
          new IconButton(icon: Icon(Icons.shopping_cart, color: Colors.white,), onPressed: (){}),
        ],
      ),
      drawer: new Drawer(
        child: new ListView(
          children: <Widget>[
            new UserAccountsDrawerHeader(
              accountName: Text('Santos Enoque'), 
              accountEmail: Text('santosenoque.ss@gmail.com'),
            currentAccountPicture: GestureDetector(
              child: new CircleAvatar(
                backgroundColor: Colors.grey,
                child: Icon(Icons.person, color: Colors.white,),
              ),
            ),
           decoration: new BoxDecoration(
             color: Colors.red
           ),
            ),
//body
        
         InkWell(
           onTap: (){},
           child: ListTile(
             title: Text('Home Page'),
             leading: Icon(Icons.home),
           ),
         ),
         InkWell(
           onTap: (){},
           child: ListTile(
             title: Text('My account'),
             leading: Icon(Icons.person),
           ),
         ),
         InkWell(
           onTap: (){},
           child: ListTile(
             title: Text('My Order'),
             leading: Icon(Icons.shopping_basket),
           ),
         ),
         InkWell(
           onTap: (){},
           child: ListTile(
             title: Text('Categoris'),
             leading: Icon(Icons.dashboard),
           ),
         ),
         
         InkWell(
           onTap: (){},
           child: ListTile(
             title: Text('Favourites'),
             leading: Icon(Icons.favorite),
           ),
         ),

        Divider( color: Colors.black87),

         InkWell(
           onTap: (){},
           child: ListTile(
             title: Text('Settings'),
             leading: Icon(Icons.settings),
           ),
         ),
         InkWell(
           onTap: (){},
           child: ListTile(
             title: Text('About'),
             leading: Icon(Icons.help),
           ),
         ),
          ],
        )
      ),
    );
  }
}
```
![](https://i.ibb.co/7twfBHZ/flutter07.png  )
[강의보기](https://www.youtube.com/watch?v=uXB3h7LfWIs&list=PLmnT6naTGy2SC82FMSCrvZNogg5T1H7iF&index=9)
```js
dependencies:
	carousel_pro: ^1.0.0
	assets:  //위치를 잘맞춰야 함..
		- images/
		- images/cats/
	- 
import  'package:carousel_pro/carousel_pro.dart';
```
![]( https://i.ibb.co/ypWb55B/flutter08.png )


![](https://i.ibb.co/DbqTz0R/flutter09.png  )
위젯 carousel을만들고 body에 붙인다는 간단한 ....

```js
dependencies: 
 carousel_pro: ^1.0.0
 ```
```js
import 'package:flutter/material.dart';
import 'package:fluApp/components/horizontal_listview.dart';
import 'package:carousel_pro/carousel_pro.dart';

void main(){
  runApp(MaterialApp(
    home: HomePage()
    )
  );
}
class HomePage extends StatefulWidget {
  @override
  _HomePageState createState() => _HomePageState();
}

class _HomePageState extends State<HomePage> {
  @override
  Widget build(BuildContext context) {
  Widget image_carousel = new Container(
    height: 200.0,
    child: new Carousel(
      boxFit: BoxFit.cover,
        images: [  
			Image.network(
                    'https://cdn-images-1.medium.com/max/2000/1*GqdzzfB_BHorv7V2NV7Jgg.jpeg'),
            AssetImage('images/c1.jpg'),
            AssetImage('images/m1.jpeg'),
            AssetImage('images/w3.jpeg'),
            AssetImage('images/w4.jpeg'),
            AssetImage('images/m2.jpg'),
          ],
          autoplay: false,
          animationCurve: Curves.fastOutSlowIn,
          animationDuration: Duration(milliseconds: 1000),
    ),
  );
    return Scaffold(
      appBar: new AppBar(
        title: Text('Shop'),
        actions: <Widget> [
          new IconButton(icon: Icon(Icons.search, color: Colors.white,), onPressed: (){},),
        ],
      ),
      drawer: new Drawer(

      ),

      body: new ListView(
        children: <Widget>[
          image_carousel,

          new Padding(padding: const EdgeInsets.all(8.0),
          child: new Text('Categories'),
          ),
          HorezontalList(),
        ],
      )
    );
  }
}

```
![](https://i.ibb.co/jJ9vkTD/flutter-11.png)
[강의](https://www.youtube.com/watch?v=32RI0qUnTzQ&list=PLmnT6naTGy2SC82FMSCrvZNogg5T1H7iF&index=11)
```js

## 이미지가 안보이면..yml확인할것

  assets:
   - images/
   - images/cats/
```
![](https://i.ibb.co/gysMtsk/flutter-001.png)
```js

## Categorys추가

new  Padding(padding:  const  EdgeInsets.all(8.0),
child:  new  Text('Categorys'),
```
```js

## ***lib/components/horizontal_listview.dart'***

import 'package:flutter/material.dart';

class HorezontalList extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Container(
      height: 80.0,
      child: ListView(
        scrollDirection: Axis.horizontal,
        children: <Widget> [
          Category(
            image_location: 'images/cats/tshirt.png',
            image_caption:'shirt',
          )
       

        ],
      ),
    );
  }
}

class Category extends StatelessWidget {

|  final String image_location; | 이것만 공부하면 될것같은데....
|  final String image_caption;  |

  Category({
 |    this.image_location,| 
 |    this.image_caption, | 
  });

 
  @override
  Widget build(BuildContext context) {
    return Padding(padding: const EdgeInsets.all(2.0),
    child: InkWell(onTap: (){},
    child: Container(  넓이를 잡지 않으면 에러가 난다
      width: 100.0,
        child: ListTile(
        title: Image.asset(image_location, width: 100.0, height: 80.0,), 이 넓이도 잡아야 하고
        subtitle: Text(image_caption),
          ),
    )
      )
    );
  }
}
```
subtitle: Text(image_caption)에 컨테이너로 스타일 추가
```js
     subtitle: Container(
          alignment: Alignment.topCenter,
          child: Text(image_caption, style: new TextStyle(fontSize: 12.0),),
        )
```
![](https://i.ibb.co/1mXhrPH/Screen-Shot-2020-07-13-at-11-21-06-PM.png)
![](https://i.ibb.co/s2XT0Sz/Screen-Shot-2020-07-13-at-11-20-53-PM.png)
![](https://i.ibb.co/y6LTK8Z/flutter-12.png)
[강의](https://www.youtube.com/watch?v=vt0u9WFHZ4w&list=PLmnT6naTGy2SC82FMSCrvZNogg5T1H7iF&index=13)
```js
assets:
	- images/
	- images/products/
```
```js
##  main.dart
import  'package:carousel_pro/carousel_pro.dart';

body: new ListView(
        children: <Widget>[
          image_carousel,
          
          new Padding(padding: const EdgeInsets.all(8.0),
          child: new Text('Categorys'),
          ),
          HorizontalList(),

>           new Padding(padding: const EdgeInsets.all(20.0),
>           child: new Text('Resent products'),
>           ),
>           Container(
>             height: 320.0,
>             child: Products(),

          )
        ],
```

```js

## *products.dart*

import 'package:flutter/material.dart';

class Products extends StatefulWidget {
  @override
 _ProductsState createState() => _ProductsState();
}

class _ProductsState extends State<Products> {
  var product_list = [
   { 
    "name": "Blazer",
    "picture": "images/products/blazer1.jpeg",
    "old_price": 120,
    "price": 85,
    },
   { 
    "name": "Red dress",
    "picture": "images/products/dress1.jpeg",
    "old_price": 100,
    "price": 50,
    },
  ];
  @override
    Widget build(BuildContext context) {
    return GridView.builder(
      itemCount: product_list.length,
      gridDelegate: new SliverGridDelegateWithFixedCrossAxisCount(crossAxisCount: 2), 
      itemBuilder: (BuildContext context, int index){
        return Single_prod(
          prod_name: product_list[index]['name'],
          prod_picture: product_list[index]['picture'],
          prod_old_price: product_list[index]['old_price'],
          prod_price: product_list[index]['price'],
        );
      },);
  }
}

class Single_prod extends StatelessWidget {
  final prod_name;
  final prod_picture;
  final prod_old_price;
  final prod_price;

  Single_prod({
    this.prod_name,
    this.prod_picture,
    this.prod_old_price,
    this.prod_price,
  });
  @override
  Widget build(BuildContext context) {
    return Card(
      child: Hero(
        tag: prod_name,
        child: Material(
          child: InkWell(onTap: (){},---------->Navigator
            child: GridTile(
              footer: Container(
                color: Colors.white70,
                child: ListTile(
                  leading: Text(prod_name, style: TextStyle(fontWeight: FontWeight.bold),),
                ),
              ),
              child: Image.asset(prod_picture,
              fit: BoxFit.cover,)),
          ),
        )
      )
    );
  }
}



```
![](https://i.ibb.co/2jBghGV/Screen-Shot-2020-07-14-at-4-51-03-PM.png)
```js
 child: GridTile(
                    footer: Container(
                      color: Colors.white70,
                      child: ListTile(
                          leading: Text(
                            prod_name,
                            style: TextStyle(fontWeight: FontWeight.bold),
                          ),
                          title: Text(
                            "\$$prod_price",
                            style: TextStyle(
                                color: Colors.red, fontWeight: FontWeight.w800),
                          ),
                          subtitle: Text(
                            "\$$prod_old_price",
                            style: TextStyle(
                                color: Colors.black54,
                                fontWeight: FontWeight.w800,
                                decoration: TextDecoration.lineThrough),
                          )),
                    ),
```

![](https://i.ibb.co/bFcF7y5/flutter-13.png)

[here](https://www.youtube.com/watch?v=zZdbCSDlhx8&list=PLmnT6naTGy2SC82FMSCrvZNogg5T1H7iF&index=15)
라우터
![](https://i.ibb.co/kQTpCK0/Screen-Shot-2020-07-14-at-5-21-33-PM.png)
![](https://i.ibb.co/T4qBk7h/Screen-Shot-2020-07-14-at-5-20-34-PM.png)
```js
child:  InkWell(
		onTap: () =>  Navigator.of(context).push(new  MaterialPageRoute(
				builder: (context) =>  new  ProductDetails())),
```
![](https://i.ibb.co/Tmz6Mcw/flutter-14.png)

##페이지 전환
![](https://i.ibb.co/syGb1s9/flutter-15.png)
## route
[강의 전체16분중에서 7분에 시작](https://www.youtube.com/watch?v=zZdbCSDlhx8)
```js
//새화면으로 이동
import  'package:fluIfyaa/components/pages/product_detail.dart';


class MyButton extends StatelessWidget {
  @override 
  Widget build(BuildContext context) {
    return InkWell(
      child: Container(
        padding: EdgeInsets.all(12.0),
        child: Text('ifyaa'),
      ),
      onTap: () {
       Navigator.of(context).push(new MaterialPageRoute(
         builder: (contest)=> new ProductDetail()));
      },
    );
  }
}
//  화면아래에 표시
      onTap: () {
        Scaffold.of(context).showSnackBar(SnackBar(content: Text('Tap')));
      },
```

```js
product_derail.dart

import 'package:flutter/material.dart';

class ProductDetail extends StatefulWidget {
  @override
  _ProductDetailState createState() => _ProductDetailState();
}
class _ProductDetailState extends State<ProductDetail>{
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: new AppBar(
        backgroundColor: Colors.red,
        title: Text('ShopApp'),
        actions: <Widget> [
          new IconButton(
	          icon: Icon(
	          Icons.search, color: Colors.white,), onPressed: (){}),
          new IconButton(
	          icon: Icon(
	          Icons.shopping_cart, color: Colors.white,), onPressed: (){}),
        ]
      )
    );
  }
}
```
![](https://i.ibb.co/yPwcdvz/flutter-002.png)
[강의 18분에서 6분 참고](https://www.youtube.com/watch?v=4DxEgh39aHg&t=59s)
```js
      body: new ListView(
        children: <Widget>[
          new Container(
            height: 300.0,
            color: Colors.black,
          )
        ],
      )
    );
  }
}
```
![](https://i.ibb.co/qp2hbTb/flutter-006.png)
![](https://i.ibb.co/6ZM4FNM/flutter-003.png)

여기서 다른 페이지도 이동
![](https://i.ibb.co/1n4BRdp/flutter-004.png)
![](https://i.ibb.co/fYvSjzr/flutter-005.png)

[8.47/19:32](https://www.youtube.com/watch?v=nUPF8mXdn7M&list=PLmnT6naTGy2SC82FMSCrvZNogg5T1H7iF&index=17)
[source](https://github.com/Santos-Enoque/complete_flutter_ecommerce/blob/master/lib/screens/product_details.dart)
> Written with [StackEdit](https://stackedit.io/).
![](https://i.ibb.co/VwZTGrQ/Screen-Shot-2020-07-15-at-12-10-04-AM.png)
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTY5ODM4MzQ0MCwtNDc1MTM1NTA5LDk4Mz
EzMDAwLDI1NDIyNTY4NCw0ODc4NTk0NjMsLTg4ODk2NTAzNSwx
OTkyNTg5MTkyLC0xMTI3MzAxMzc0LC0xNzAxMjY4NzQzLC03NT
k3MzkyMjNdfQ==
-->