# FAQ'S

## FAQs {#faqs}

* [How do I extract files in Windows?](https://samaritan1011001.gitbooks.io/flutter-swiggy-app/content/faqs.html#extract)
* [How do I customise the app?](https://samaritan1011001.gitbooks.io/flutter-swiggy-app/content/faqs.html#customise)
* [How do I style widgets?](https://samaritan1011001.gitbooks.io/flutter-swiggy-app/content/faqs.html#style)
* [How do I decide which widget must be stateful and which one must be stateless?](https://samaritan1011001.gitbooks.io/flutter-swiggy-app/content/faqs.html#state)
* [How do I go about learning Flutter if I already know React Native?](https://samaritan1011001.gitbooks.io/flutter-swiggy-app/content/faqs.html#flutter-for-rn)
* [None of the above, I have a different query](https://samaritan1011001.gitbooks.io/flutter-swiggy-app/content/faqs.html#none)

#### How do I extract files in Windows? {#how-do-i-extract-files-in-windows}

I want to extract files in Windows.

**Solution:**

• Unzip the file.

• Right click on the extracted file and select \`View files\`.

**NOTE:**We don't provide support for Windows. It's completely buyer's responsibility.

#### How do I customize the app? {#how-do-i-customize-the-app}

I need to customise certain widgets used in the app. How can I do it?

**Solution:**

The whole app is made modular , so customising the widgets used in the app will be a cakewalk. Every reusable widget used in the app are separated into different dart files under the components directory. Each of these widgets take the required parameters and a list of data items. These widgets can be modified to app requirements and is completely modular in structure.

Consider we have a custom component called customWidget which is structured as follows:

```text
import 'package:flutter/material.dart';
import 'package:food_ordering_app/screens/Home/style.dart';

class customWidget extends StatelessWidget {
String text;
customWidget({this.text});
  @override
  Widget build(BuildContext context) {
    Size screenSize = MediaQuery.of(context).size;
    return 
          new Container(
            height: screenSize.height / 4,
            width: screenSize.width,
            decoration: new BoxDecoration(
              color: Colors.black54,
            ),
            child: new Center(
                child:
                  new Text(
                    text,
                    textAlign: TextAlign.center,
                    style: new TextStyle(
                      fontWeight: FontWeight.bold,
                      color: Colors.white,
                    ),
                  ),
                ),
          );

  }
}
```

The above component renders a container of the specified size with the text given to it, in the centre. This custom widget can be used all over the app by passing varying text to be displayed. The usage of this component is shown below:

```text
 @override
  Widget build(BuildContext context) {
    return new Scaffold(
        body: new ListView(
          children: 
<
Widget
>
[
            new customWidget(text:"Hello"),
            new customWidget(text:"World!"),
          ],
        ),
      );
  }
```

#### How do I style widgets? {#how-do-i-style-widgets}

I need to use custom colours and also use certain primary colours and themes across my whole app.

**Solution:**

Under the Theme directory exists a `style.dart` that specifies the primary `ThemeData.`

ThemeData has several parameters which can be used to specify style properties to be used across the app.  
Specify these in one place and use it across the app as shown below:

```text
ThemeData appTheme = new ThemeData(
  primaryColor: new Color.fromRGBO(12, 100, 249, 1.0),
  primaryTextTheme: new TextTheme(
    display1: new TextStyle(
      color: new Color.fromRGBO(68, 68, 68, 1.0),
      fontSize: 16.0,
      fontWeight: FontWeight.bold,
    ),
```

Usage:

1. Pass it to the theme property of the MaterialApp widget.
2. ```text
   new MaterialApp(
   theme:appTheme,
   )
   ```
3. Use it as shown below:

   ```text
   backgroundColor:Theme.of(context).backgroundColor
   ```

#### How do I decide which widget must be stateful and which one must be stateless? {#how-do-i-decide-which-widget-must-be-stateful-and-which-one-must-be-stateless}

**Solution:**

**1. Figure out which widgets must be Stateful and Stateless**

Widgets in Flutter can be Stateful or Stateless, depending on whether they depend on some state. If a widget changes—the user interacts with it, it’s Stateful; otherwise it can be Stateless. Stateful widgets are useful when the part of the user interface you are describing can change dynamically.

**2. If using Stateful widget, decide which object manages the widget’s state.**

There are three main ways to manage state:

* The widget manages its own state.
* The parent manages the widget’s state.
* A mix-and-match approach

How do you decide which approach to use? The following principles should help you decide:

* If the state in question is user data, for example the checked or unchecked mode of a checkbox, or the position of a slider, then the state is best managed by the parent widget.
* If the state in question is aesthetic, for example an animation, then the widget itself best manages the state.
* When in doubt, let the parent widget manage the child widget’s state.

**3. Subclass StatefulWidget and State.**

The `MyStatefulWidget` class manages its own state, so it overrides `createState()` to create the State object. The framework calls `createState()` when it wants to build the widget. In this example, `createState()` creates an instance of `_MyStatefulWidgetState`, which is implemented in the next step.

```text
class MyStatefulWidget extends StatefulWidget {
  MyHomePage({Key key, this.title}) : super(key: key);
  final String title;

  @override
  _MyStatefulWidgetState createState() =
>
 new _MyStatefulWidgetState();
}

class _MyStatefulWidgetState extends State
<
MyStatefulWidget
>
 {

  @override
  Widget build(BuildContext context) {
    ...
  }
}
```

**4. Plug the stateful widget into the widget tree.**

Add your custom stateful widget to the widget tree in the app’s build method.

```text
  // This widget is the root of your application.
  @override
  Widget build(BuildContext context) {
    return new MaterialApp(
      title: 'Flutter Demo',
      theme: new ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: new MyStatefulWidget(title: 'State Change Demo'),
    );
  }
}
```

#### How do I go about learning Flutter if I already know React Native? {#how-do-i-go-about-learning-flutter-if-i-already-know-react-native}

**Solution:**

You have come to the right place! We have got you covered. Check out the official "[Flutter for React Native Developers](https://flutter.io/flutter-for-react-native/)" document.

#### None of the above, I have a different query? {#none-of-the-above-i-have-a-different-query}

The above listed FAQs were not of your help? Facing some other issues?

**Solution:**

We provide our customers with lively support and welcome all your issues. We request you to provide a short description of the visible symptoms of the error that you are facing. If applicable, include error messages, screen shots, and stack traces. If applicable, submit a step-by-step walkthrough of how to reproduce the issue.

