
## Flutter是什么

> Flutter是谷歌的移动UI框架，可以快速在iOS和Android上构建高质量的原生用户界面。 Flutter可以与现有的代码一起工作。在全世界，Flutter正在被越来越多的开发者和组织使用，并且Flutter是完全免费、开源的。

### 优点
- 快速开发
- 富有表现力和灵活的UI
- 原生性能

## 学习资料
- [Flutter官网](https://flutter.io/)
- [GitHub](https://github.com/flutter)
- [Flutter中文网](https://flutterchina.club/)
- [Flutter掘金社区](https://juejin.im/tag/Flutter)

## Flutter值得学吗
最近看了相关资料，好像用Flutter的并不多，阿里咸鱼据说有用Flutter，其他的大厂好像没什么消息。

我是看了[为什么我觉得 Flutter 短期内不会流行但依然选择学习它](https://limboy.me/essay/2019/01/07/is-flutter-the-future.html)决定试下Flutter。我最早是作Android开发，不过说来惭愧，没有写过生成性的App。工作后就搞Java Web开发了，现在依然在搞Java Web开发。看到Flutter貌似还可以，决定试下，看能不能捣鼓点东西出来。

## 开发环境安装
- sdk安装
   按照官网教程一步一步来就可以了。
    - [英文](https://flutter.io/docs/get-started/install)
    - [中文](https://flutterchina.club/get-started/install/)
- 开发工具
    我是Android开发，所以偏向于用Android Studio。[Android Studio下载地址](https://developer.android.com/studio/?hl=zh-cn)。安装好Android Studio后，先要安装Dart插件和Flutter插件，因为Flutter是使用Dark开发。

##  创建项目
安装好Dark和Flutter插件后，可以直接创建Flutter项目。
![](http://blog.caofeng.me/images/flutter1.png)
![](http://blog.caofeng.me/images/flutter2.png)
![](http://blog.caofeng.me/images/flutter3.png)
![](http://blog.caofeng.me/images/flutter4.png)
填写项目项目，一路next，等待项目创建。
项目目录结构如下
![](http://blog.caofeng.me/images/flutter5.PNG)
打开GeneratedPluginRegistrant.java ,如果没有设置Java Sdk，会提示设置Sdk。
## 运行项目
运行Android项目，要先设置好Java Sdk 。然后用用Usb连接手机，在上方会出现已连接的手机，选择手机，点击debug ,等待项目运行并安装到手机上。
![](http://blog.caofeng.me/images/flutter6.png)

Demo项目运行效果如下
![](http://blog.caofeng.me/images/flutter7.png)

## Demo项目解析
我现在还没有看过任何Dark的语法和Flutter语法，直接看lib目录下的main.dart，有详细的说明。
```dart
//导入material主题
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  // This widget is the root of your application.
  // 应用根组件
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      // 定义App名字
      title: 'Flutter Demo',
      theme: ThemeData(
        // This is the theme of your application.
        //
        // Try running your application with "flutter run". You'll see the
        // application has a blue toolbar. Then, without quitting the app, try
        // changing the primarySwatch below to Colors.green and then invoke
        // "hot reload" (press "r" in the console where you ran "flutter run",
        // or simply save your changes to "hot reload" in a Flutter IDE).
        // Notice that the counter didn't reset back to zero; the application
        // is not restarted.
        //定义App主题，可以尝试修改成其他颜色
        primarySwatch: Colors.blue,
      ),
      //定义应用首页 
      home: MyHomePage(title: 'Flutter Demo Home Page'),
    );
  }
}

//自定义首页
class MyHomePage extends StatefulWidget {
  MyHomePage({Key key, this.title}) : super(key: key);

  // This widget is the home page of your application. It is stateful, meaning
  // that it has a State object (defined below) that contains fields that affect
  // how it looks.

  // This class is the configuration for the state. It holds the values (in this
  // case the title) provided by the parent (in this case the App widget) and
  // used by the build method of the State. Fields in a Widget subclass are
  // always marked "final".

  final String title;

  @override
  _MyHomePageState createState() => _MyHomePageState();
}

// 首页状态管理
class _MyHomePageState extends State<MyHomePage> {
  int _counter = 0;

  //  增加点击量
  void _incrementCounter() {
    setState(() {
      // This call to setState tells the Flutter framework that something has
      // changed in this State, which causes it to rerun the build method below
      // so that the display can reflect the updated values. If we changed
      // _counter without calling setState(), then the build method would not be
      // called again, and so nothing would appear to happen.
      _counter++;
    });
  }

    //构建控件
  @override
  Widget build(BuildContext context) {
    // This method is rerun every time setState is called, for instance as done
    // by the _incrementCounter method above.
    //
    // The Flutter framework has been optimized to make rerunning build methods
    // fast, so that you can just rebuild anything that needs updating rather
    // than having to individually change instances of widgets.
    return Scaffold(
        // 定义导航栏
      appBar: AppBar(
        // Here we take the value from the MyHomePage object that was created by
        // the App.build method, and use it to set our appbar title.
        title: Text(widget.title),
      ),
      body: Center(
        // Center is a layout widget. It takes a single child and positions it
        // in the middle of the parent.
        //定义子控件
        child: Column(
          // Column is also layout widget. It takes a list of children and
          // arranges them vertically. By default, it sizes itself to fit its
          // children horizontally, and tries to be as tall as its parent.
          //
          // Invoke "debug painting" (press "p" in the console, choose the
          // "Toggle Debug Paint" action from the Flutter Inspector in Android
          // Studio, or the "Toggle Debug Paint" command in Visual Studio Code)
          // to see the wireframe for each widget.
          //
          // Column has various properties to control how it sizes itself and
          // how it positions its children. Here we use mainAxisAlignment to
          // center the children vertically; the main axis here is the vertical
          // axis because Columns are vertical (the cross axis would be
          // horizontal).
          // 居中显示
          mainAxisAlignment: MainAxisAlignment.center,
          children: <Widget>[
            Text(
              'You have pushed the button this many times:',
            ),
            Text(
              '$_counter',
              style: Theme.of(context).textTheme.display1,
            ),
          ],
        ),
      ),
      //加号按钮
      floatingActionButton: FloatingActionButton(
        onPressed: _incrementCounter,
        tooltip: 'Increment',
        // 按钮样式，内置了一些按钮
        child: Icon(Icons.add),
      ), // This trailing comma makes auto-formatting nicer for build methods.
    );
  }
}
```
## 初体验
开发过程还是比较流畅，不想以前开发Android那样，跑个Demo都要搞很久，现在教程也比较大。语法目前来看还是很好懂，改下代码，看下效果，很快就会有感谢的认识。热更新很实用，改点东西，马上就可以看到效果。

控件嵌套定义，这个语法有点麻烦。


