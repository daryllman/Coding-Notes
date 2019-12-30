# Flutter Framework App Development

Here are my simplified notes for Flutter App Development, using DART programming language.      

Used for building iOS & Android Phone Apps, Web Apps, etc.

# Table of Contents

1. **Introduction**
   1. Why Flutter
   2. The Anatomy of a Flutter App
   3. Setup & Installation
2. **Section 2: Creating an App - first steps**
   1. MaterialApp Class
   2. Formatting Code
   3. Hot Reload Feature
   4. Scaffolding a Flutter App
   5. Planning the Structure of a Flutter App
   6. Adding Custom App Icons
   7. Testing your Flutter App
3. **Variables**
4. **Arithmetic Operations**
5. Methods
6. ....

<br>

****

<br/>



# Section 1: Introduction to Flutter Framework

## Why Flutter?

- Used for building IOS Apps, Android Apps, Web Apps.

- **One Codebase** for both IOS and Android App development (Only need to maintain this one codebase for any changes/updates to app)     

  > Only need to know one language - Dart      
  >
  > Dart is used to build phone apps (Flutter), Web Apps (Hummingbird)

- Good support over **apps of different screen sizes** (phones, tablets, tv screens, etc....)     

  > This is important as there will be too many screen sizes to support manually:      
  >
  > Apple: ipadpro, ipadair, phones.....      
  >
  > Android: Open-sourced - meaning anyone can create their own smart devices with whatever screen size

- Flexible Layout System

  > Flutter is a UI Toolkit that makes it easy for developers to design beautiful interfaces for all sorts screen sizes and devices.      
  >
  > Comes with many pre-built widgets to use       
  >
  > 

- It is all about the **Widget**-based development for flutter

- **Hot Reload system**: Seeing your UI changes almost immediately as soon as you click "save" - way faster development

- For deeper development, you get to see the **original source code** of widgets etc. as Flutter is Open-Source      

  Benefits: You are aware of the exact behavior of components and you can create your own components based off on the original source code.

  > Such things are a mystery for many iOS components.

## The Anatomy of a Flutter App

Everything inside a Flutter App are **widgets** - you are building widgets upon widgets

- Imagine the widget tree

```mermaid
graph LR
A[Scaffold]  --> B[App Bar]
A --> C[Container]
C --> D[Column]
D --> F[Text]
D --> H[Row]
H --> I[Text]
H --> J[Icon]
```

- Scaffold is the base blank screen for the app
- AppBar is a pre-built widget that looks and acts like an app bar
- Container is a box that holds widgets inside it
- Column contains a list of widgets that scroll vertically - arranged on top of one another
- Row contains a list of widgets that scroll horizontally - arranged side by side of  one another

## Setup & Installation

##### Code editor

 Android Studio, Visual Studio Code.      

Preferred to use Android Studio as its easier to work with emulator and android packages. Some tools are specially developed for Android Studio.

##### Testing Android Apps from Flutter

Easy to use physical Android phones, or Android Emulators

##### Testing iOS Apps from Flutter

You will need a mac to test! (security reasons from Apply - Code Signing). Even for the iOS Simulator.

<br/>

Can try using **Codemagic** to "Build, test and deliver your Flutter apps in record time". - Continuous integration and delivery for Flutter Apps

<br/>

#### Installing Flutter

1. Go to Flutter website and install Flutter sdk: https://flutter.dev/docs/get-started/install/windows.

   > Note: Install in a file path that does not require elevated privileges. Recommended C:\src\flutter

2. Add File Path for Flutter

   For windows: Edit environment variables for your account --add location of bin folder

   ```
   Once done, you should be able to check this in your Command Prompt:
   
   flutter --version
   ```

3. Use flutter doctor to check that set up is good for flutter to work well

   ``` 
   Type in Command Prompt:
   flutter doctor
   ```

   > This is quite a useful tool as it checks all the dependencies, including whether you have downloaded Flutter plugin on android studio

4. Install Flutter Plugin on Android Studio

   Go to Settings > Plugins       

   Type in 'Flutter' and install it. Afterwards you will have to restart the IDE for plugin changes to take place.     

   Once this is done, you should be able to see "Start a new Flutter project" in you welcome screen or when you create a new project     

5. Download a Phone Emulator (if you do not have one yet)

   Open AVD manager > Choose a phone (recommended Nexus series) > Choose an OS     

   > For Emulated Performance: Graphics, recommended to use Hardware for faster performance.

**You are set up to use flutter and dart to develop flutter apps for Android!**

<br/>







# Section 2: Creating an App - first steps

## MaterialApp Class

This is an important app to use as your app's scaffold.     

Taps straight into the **Material Design** that is being used by many app creators - standard design templates that can be used straight.          

https://material.io/design/

Built by Google     

#### Basic barebones app with MaterialApp:

```
import 'package:flutter/material.dart';

void main() => runApp(MaterialApp(home: Text('Hello world')));
```

#### Center Widget

To center other widgets, you can place them into a **Center Widget**

> Note how Flutter is made up of Widgets ---including this centering behaviour

```
import 'package:flutter/material.dart';

void main() => runApp(MaterialApp(home: Center(child: Text('Hello world'))));
```

## Formatting Code

#### Using in-built re-formatter: **"Reformat Code with dartfmt"**     

BUT to use this, we need to add a comma at each parenthesis of hierarchy to signal to dartfmt formatter of the hierarchy of widgets. ie.     

###### FROM THIS:   

```
import 'package:flutter/material.dart';

void main() => runApp(MaterialApp(home: Center(child: Text('Hello world'))));
```

###### TO THIS:

```
import 'package:flutter/material.dart';

void main() => runApp(MaterialApp(home: Center(child: Text('Hello world'),),),);

```

###### Click "Reformat Code with dartfmt"

```
import 'package:flutter/material.dart';

void main() => runApp(
      MaterialApp(
        home: Center(
          child: Text('Hello world'),
        ),
      ),
    );

```

> This will automatically arrange and format code in a very readable format.

###### Change the fat arrow '=>' to curly braces '{}' for better readability

```
import 'package:flutter/material.dart';

void main() { runApp(
      MaterialApp(
        home: Center(
          child: Text('Hello world'),
        ),
      ),
    );
}
```

## Hot Reload Feature

One of the key features of Flutter: 

### **Hot Reload**    

Allows almost instant changes to UI to be seen (but there are caveats for this useful feature)     

> Ie. Changes can only be seen for Hot Reload for a few instances - not for all kinds of changes

#### Changes must be inside a Flutter Stateless or Stateful widget

We can create our own **StatelessWidget** by using the boilerplate code for building a stateless widget       

```
class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Container();
  }
}
```

We just have to throw everything that we coded for the app into this StatelessWidget.

```
import 'package:flutter/material.dart';

void main() { runApp(
  MyApp()
    );
}
class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Center(
        child: Text('Hello world'),
      ),
    );
  }
}

```

Now any changes that you do under this stateless widget of MyApp will be reflected using **Hot Reload **     

Almost 'live' changes - updates in fractions of seconds

> Saves us a lot of time by recompiling and building app - especially for huge apps.     
>
> Especially if you make a lot of minute UI changes.

Note: You will not lose the in-app data.

### Hot Restart

If you want to test the app from the start    

It acts like Hot Reload, but it refreshes whatever in-app data/progress you have done.

## Scaffolding a Flutter App

Place whatever you need onto the scaffold - like a background to the app.    

https://api.flutter.dev/flutter/material/Scaffold-class.html       

```
import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(),
    );
  }
}
```

### Components you can add: 

- appBar - a component (properties: title, backgroundColor,....)

- backgroundColor

- body

- drawer

- floatingActionButton

- bottomNavigationBar

- ... etc

  > visit https://api.flutter.dev/flutter/material/Scaffold-class.html#instance-properties  to find more

eg for appBar:

```
import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(
          title: Text('I AM RICH'),
          backgroundColor: Colors.blueGrey[900],
        ),
      ),
    );
  }
}
```

> Useful to use the Material Colors from MaterialDesign.     
>
> https://material.io/design/color/the-color-system.html#tools-for-picking-colors      
>
> We can do this as we are using a MaterialApp.

### Body

This is where the main content of the scaffold class is placed at.

##### Image widget

Note that there are many different types of libraries for Image. Need to choose the right one.     

https://api.flutter.dev/flutter/widgets/Image-class.html

Properties:      

- image
- repeat
- height
- width
- color
- alignment
- ....etc

```
import 'dart:ui';

import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        backgroundColor: Colors.blueGrey,
        appBar: AppBar(
          title: Text('I AM RICH'),
          backgroundColor: Colors.blueGrey[900],
        ),
        body: Image(
          image: NetworkImage('https://images.unsplash.com/photo-1575616652983-23b9a2987012?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=634&q=80'),
        ),
      ),
    );
  }
}

```

What if you want to center an image?

> Tip: Click on Image widget and use Alt+Enter: "Wrap with Center"     
>
> Flutter will automatically wrap the whole image widget in a Center widget
>
> ```
> import 'dart:ui';
> 
> import 'package:flutter/material.dart';
> 
> void main() {
>   runApp(MyApp());
> }
> 
> class MyApp extends StatelessWidget {
>   @override
>   Widget build(BuildContext context) {
>     return MaterialApp(
>       home: Scaffold(
>         backgroundColor: Colors.blueGrey,
>         appBar: AppBar(
>           title: Text('I AM RICH'),
>           backgroundColor: Colors.blueGrey[900],
>         ),
>         body: Center(
>           child: Image(
>             image: NetworkImage('https://images.unsplash.com/photo-1575616652983-23b9a2987012?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=634&q=80'),
>           ),
>         ),
>       ),
>     );
>   }
> }
> 
> ```

###### To use Image from our local app folder:

We have to go to pubspec.yaml and uncheck the Assets section

```
 # To add assets to your application, add an assets section, like this:
 # assets:
  #  - images/a_dot_burr.jpeg
  #  - images/a_dot_ham.jpeg
```

Insert the correct directory and file we want to use:

```
# To add assets to your application, add an assets section, like this:
  assets:
    - images/diamondImage.jpeg
```

This tells our flutter app about this particular asset - after which we can use this asset anywhere in our flutter app, eg main.dart

<br/>

## Planning the Structure of a Flutter App

There are many tools that can be used to plan the structure of any app, not just flutter app. It is essentially like a diagram or a flowchart to see the hierarchy of widgets for flutter app.     

Can use www.draw.io  to plan.    

Note for the app above:     

```mermaid
graph LR
AA[Material App] --> A
A[Scaffold]  --> B[App Bar]
A --> C[Center]
A --> CC[Color]
C --> IM[Image]
B --> T[Text]
B --> Co[Color]

```

> THE POWER OF FLUTTER APP - LEVERAGING THE POWER OF PRE-BUILT WIDGETS FROM FLUTTER TO BUILD IOS & ANDROID APPS:     
>
> All of these in under 30 lines of written code

## Adding Custom App Icons

Go to www.appicon.co     

Good platform to generate app icons for different devices: iPhone, iPad, Android, etc...       

This generates all the required files and formats for android and ios

###### Android

Go to android>app>src>main>res     

Delete all existing mipmap folders and copy the generated mipmap folders in.    

Make sure the names of the icons in the mipmap folders must be "ic_launcher"    

> Note: Recent designs of Android Icons are Circular style         
>
> How to resize/reformat style:       
>
> Go to res folder and create new Image Asset      
>
> Go to path and pick the image of the icon you want       
>
> Manually resize every app icon you want so that it looks good.     
>
> This will manually replace all the existing app icons you have in your mipmap folders.

###### iOS

Go to ios>Runner>Assets.xcassets     

Delete Assets.xcassets folder and copy the generated Assets.xcassets folder in.     

<br/>

> All your App Icons for Android and iOS are updated with the new one!!

## Testing your Flutter App

### Android

###### Enable Developer Mode

Go to Settings>About Phone>Software Information      

Keep tapping on Build number until it says you have enabled developer mode      

###### Enable USB Debugging

Go to Settings> Developer Options       

Enable USB debugging     

###### Connect Your Phone with USB

Check "Always allow from this computer" to save much hassle

###### Run App from Android Studio

On Android Studio, select your phone instead of the emulator phone     

Load app into your phone!



## External Resources to incorporate in App

- www.icons8.com

  Beautiful Illustrations and Icons by artists

- www.vecteezy.com

  larger list of icons

- www.canva.com

  > Remember to credit the artworks from artists





## Title 1

```
ssdsadasd
```

<br/>

****

Credits: https://github.com/londonappbrewery/Flutter-Course-Resources