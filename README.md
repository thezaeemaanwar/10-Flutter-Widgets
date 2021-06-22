# 10-Flutter-Widgets
# Dart Programming Language
## Loops
At times, certain instructions require repeated execution. Loops are an ideal way to do the same. A loop represents a set of instructions that must be repeated. In a loop’s context, a repetition is termed an iteration.
Dart has the following types of loops:
- For loop
- While loop
- Do while loop
## Lists
 A very commonly used collection in programming is an array. Dart represents arrays in the form of List objects. A list is simply an ordered group of objects. The dart:core library provides the List class that enables the creation and manipulation of lists.
Lists can be classified as
- Fixed Length List
- Growable List
## Maps
The Map object is a simple key/value pair. Keys and values in a map may be of any type. A Map is a dynamic collection. In other words, Maps can grow and shrink at runtime.
Maps can be declared in two ways −
- Using Map Literals
- Using a Map constructor
Here is the syntax for both:

```dart
  var identifier = {key1:value1, key2:value2 [,.....,key_n:value_n]}
 
  // Using Map constructor 
  var identifier = new Map();
  map_name[key] = value;
 
```
## Functions
Functions are the building blocks of readable, maintainable, and reusable code. A function is a set of statements to perform a specific task. Functions organize the program into logical blocks of code. Once defined, functions may be called to access code. This makes the code reusable. Moreover, functions make it easy to read and maintain the program’s code.
Classes
Dart is an object-oriented language. It supports object-oriented programming features like classes, interfaces, etc. A class in terms of OOP is a blueprint for creating objects. A class encapsulates data for the object. Dart gives built-in support for this concept called class.

Syntax:
```dart 
  class class_name {  
    <fields> 
    <getters/setters> 
    <constructors> 
    <functions> 
  }
 ```

# Main Concepts
## Layouts
The core of Flutter’s layout mechanism is widgets. In Flutter, almost everything is a widget—even layout models are widgets. The images, icons, and text that you see in a Flutter app are all widgets. But things you don’t see are also widgets, such as the rows, columns, and grids that arrange, constrain and align the visible widgets.
Following are the steps to create a flutter widget layout:
- Select a layout widget such as Text or Image
- Create a visible widget
- Add the visible widget to the layout widget such as container, gridView or listView.
## Assets
Flutter apps can include both code and assets (sometimes called resources). An asset is a file that is bundled and deployed with your app and is accessible at runtime.
Flutter uses the pubspec.yaml file, located at the root of your project, to identify assets required by an app.
Here is an example:
```yaml
  flutter:
    assets:
      - assets/icon.png
      - assets/background.svg
```   

## Images & Icons
Image is a widget that displays an image.
Here is an example:

```dart
  const Image(
    image: NetworkImage(url),
  ),
```

To use the Icon Class make sure you set uses-material-design: true in your project's pubspec.yaml file in the flutter section. This ensures that the MaterialIcons font is included in your application. This font is used to display the icons. 

## Navigation
Most apps contain several screens for displaying different types of information. 
The next few sections show how to navigate between two routes, using these steps:
- Create two routes.
- Navigate to the second route using Navigator.push().
- Return to the first route using Navigator.pop().

# Input and Outputs
## Input & Selections
Input and selection widgets are used to take user inputs in various forms such as:
- Checkbox - allows users to select multiple options
- Date & Time Picker - dialog window to select date and time
- Radio Button - Allow user to only select one option
- Slider - allows user to select from a range of values
- Switch - toggle the state of a single setting option
- Text Field - allows users to input text
## Dialogs
A dialog is a common component used within mobile applications to notify or draw the attention of the user to a specific part of the screen.
There are four types of dialogs in flutter:
- Alert - displays information with acknowledgment actions
- Simple - Displays only a list of action items
- Confirmation - Display a list of options to choose from
- Full Screen - Display a full-screen dialog for data entry
## Alerts Dialogs
An alert dialog is a useful feature that notifies the user with important information to make a decision or provide the ability to choose a specific action or list of actions. It is a pop-up box that appears at the top of the app content and the middle of the screen.
# Different Widgets
## User-defined Widgets
Everything’s a widget in Flutter. So wouldn't it be nice to know how to make your own? There are several methods to create custom widgets, but the most basic is to combine simple existing widgets into the more complex widget that you want.
Following is an example of a custom widget:
```dart
  import 'package:flutter/material.dart';
 
  class  TextFieldWidget extends StatelessWidget {
    final String _hintText;
    TextFieldWidget({this._hintText});
    @override
    Widget build(BuildContext context) {
      return Container(
        child : Padding(
          padding: const EdgeInsets.all(20.0),
          child: TextField(    
            decoration: InputDecoration(
              hintText: _hintText,
              enabledBorder: OutlineInputBorder(borderSide: BorderSide(color: Colors.black)),
              border: OutlineInputBorder(
                borderSide: BorderSide(color: Colors.pink, width: 32.0),
                ),
            ),
          ),
        ),
      );
    }
  }
 
```
## Buttons
Buttons are the graphical control element that provides a user to trigger an event such as taking actions, making choices, searching for things, and many more. They can be placed anywhere in our UI like dialogs, forms, cards, toolbars, etc.
Following are the types of buttons available in flutter:
- Raised Button
- Elevated Button
- Text Button
- Icon Button
- Outlined Button
- Floating Action Button
- InkWell Button
- PopupMenu Button
- Drop Down Button

## TabBars
Flutter provides a convenient way to create a tab layout. To add tabs to the app, we need to create a TabBar in TabBarView and attach them with the TabController. The controller will sync both so that we can have the behavior which we need. Let us see step by step how to create a tab bar in the Flutter application.
```dart
  TabBar(
    tabs: [
      Tab(icon: Icon(Icons.directions_car)),
      Tab(icon: Icon(Icons.directions_transit)),
      Tab(icon: Icon(Icons.directions_bike)),
    ],
  ),
 ```


# Forms and APIs
## Forms
Flutter forms are used as input forms. 
> For Example, we might need to input information such as email, first name, last name etc. For this purpose, forms can come in handy.

Syntax:
```dart
 
  Form(  
     Key: _formKey,
     Child: Column(
        Children: <Widget>[
             // Add TextFormFields Here
        ],
     ),
  )
 
```
This widget acts as a container for form fields. Form Widget requires children at least. These are keys and a child. Key is a Global Key of form state. It is unique to every form and helps in identification that is then used in the validations. Child is a widget that contains data to be shown inside of the form.
We can also apply validations of the form fields. These validations can be applied by using the TextFormField widget.
	

Example:
 ```dart
     Form(
          key: formKey,
          child: Column(
            children: [
              Padding(padding: EdgeInsets.only(top: 40.0)),
              TextFormField(
                onSaved: (value) => {
                  this.setState(() {
                    name = value;
                  })
                },
                validator: (String value) {
                  return (value == null || value == "")
                      ? 'Do not leave the name empty.'
                      : null;
                },
                keyboardType: TextInputType.name,
              ),
              ElevatedButton(
                child: Text("Register"),
                style: ButtonStyle(
                  alignment: Alignment.center,
                ),
              ),
            ],
          ),
        ),
```
## REST API Integration
For applications to work efficiently, fetching and sending data to the internet is very important. To do so, different APIs are used. To consume REST APIs, dart and flutter provide http package.

We can consume REST API in flutter by following steps:
1. Add the http package
2. Make a network request using the package
3. Convert response into Dart object
4. Fetch and display data with flutter
		
Syntax to make a network request:

To fetch the data
```dart
  Future<http.Response> fetchAlbum() {
    return http.get(Uri.parse(fetchURL));
  }
```
To send the data
```dart
  Future<http.Response> createAlbum(String title) {
    return http.post(
      Uri.parse('https://jsonplaceholder.typicode.com/albums'),
      headers: <String, String>{
        'Content-Type': 'application/json; charset=UTF-8',
      },
      body: jsonEncode(<String, String>{
        'title': title,
      }),
    );
  }
 
```
Example:
```dart
 Future fetchRecords() async {
   var uri = Uri.parse("https://pcc.edu.pk/ws/list/eventplanningservices.php");
   final response = await http.get(uri);
   if (response.statusCode == 200) {
     return jsonDecode(response.body);
   } else {
     throw Exception("Failed to retrieve data");
   }
 }
 
  Future sendRecords() async {
    var sendURI =
        Uri.parse("https://pcc.edu.pk/ws/create/eventplanningservices.php");
    var response = await http.post(sendURI,
        body: jsonEncode({
          "title": “Sports Day”,
          "Description": “A Day full of enthusiasm for students”,
          "type": “co-curricular”
        }));
    var result = jsonDecode(response.body);
    showDialog(
        context: context,
        builder: (BuildContext context) {
          return AlertDialog(
            title: Text(
              "Sent Data",
            ),
            content: Text(result['message']),
            actions: [
              TextButton(
                  onPressed: () => {Navigator.pop(context)},
                  child: Text("Okay"))
            ],
          );
        });
  }
```
# Images in Flutter
There are times when we need images from users. These can be profile images, cover images, a gallery for some profile and so on. For this purpose, flutter provides the camera API and we can also use different packages available for that. 
In this example, we are using Image_Picker package for both image capture and upload. Its syntax is:

  
ImagePicker.getImage(source: ImageSource)
 

ImageSource can be either gallery or camera. After capturing/selecting an image, its path is stored in a variable of type File and can be used in the application/ upload it to the database.
## Capturing

```dart
 import 'package:image_picker/image_picker.dart';
 
 ImagePicker imagePicker = ImagePicker();
 File _image;
 
 _imageFromCamera() async {
     try {
       PickedFile capturedImage =
           await imagePicker.getImage(source: ImageSource.camera);
       final File imagePath = File(capturedImage.path);
       if (capturedImage == null) {
         showAlert(
             bContext: context,
             title: "Error choosing file",
             content: "No file was selected");
       } else {
         setState(() {
           _image = imagePath;
         });
       }
     } catch (e) {
       showAlert(
           bContext: context, title: "Error capturing image file", content: e);
     }
   }
 
```
## Uploading

```dart
 import 'package:image_picker/image_picker.dart';
 
 ImagePicker imagePicker = ImagePicker();
 File _image;
 
 _imageFromGallery() async {
    PickedFile uploadedImage =
        await imagePicker.getImage(source: ImageSource.gallery);
    final File imagePath = File(uploadedImage.path);
 
    if (uploadedImage == null) {
      showAlert(
          bContext: context,
          title: "Error choosing file",
          content: "No file was selected");
    } else {
      setState(() {
        _image = imagePath;
      });
  }
 
```
# Theme and Tab Views
## Theme
To share colors and font styles throughout an app, use themes. You can either define app-wide themes or use Theme widgets that define the colors and font styles for a particular part of the application.
Following is an example of how to create a theme for an app:TabBars
```dart
MaterialApp(
  title: appName,
  theme: ThemeData(
    // Define the default brightness and colors.
    brightness: Brightness.dark,
    primaryColor: Colors.lightBlue[800],
    accentColor: Colors.cyan[600],
 
    // Define the default font family.
    fontFamily: 'Georgia',
 
 // Define the default TextTheme. Use this to specify the default
// text styling for headlines, titles, bodies of text, and more.
    textTheme: TextTheme(
      headline1: TextStyle(fontSize: 72.0, fontWeight: FontWeight.bold),
      headline6: TextStyle(fontSize: 36.0, fontStyle: FontStyle.italic),
      bodyText2: TextStyle(fontSize: 14.0, fontFamily: 'Hind'),
    ),
  ),
  home: MyHomePage(
    title: appName,
  ),
);
 
```
## TabBarView
Flutter provides a convenient way to create a tab layout. To add tabs to the app, we need to create a TabBar in TabBarView and attach them with the TabController. The controller will sync both so that we can have the behavior which we need. Let us see step by step how to create a tab bar in the Flutter application.
```dart	
  
  TabBarView(
    children: [
        Icon(Icons.directions_car),
        Icon(Icons.directions_transit),
        Icon(Icons.directions_bike),
      ],
  ),
```

## TabController
It provides coordination between tabBar and tabBarView.The index property is the index of the selected tab and the animation represents the current scroll positions of the tab bar and the tab bar view. The selected tab's index can be changed with animateTo.
```dart
  
  class MyTabbedPage extends StatefulWidget {
    const MyTabbedPage({ Key? key }) : super(key: key);
    @override
    _MyTabbedPageState createState() => _MyTabbedPageState();
  }
 
  class _MyTabbedPageState extends State<MyTabbedPage> with  SingleTickerProviderStateMixin {
    static const List<Tab> myTabs = <Tab>[
      Tab(text: 'LEFT'),
      Tab(text: 'RIGHT'),
    ];
 
    late TabController _tabController;
 
    @override
    void initState() {
      super.initState();
      _tabController = TabController(vsync: this, length: myTabs.length);
    }
 
  @override
  void dispose() {
    _tabController.dispose();
    super.dispose();
  }
 
    @override
    Widget build(BuildContext context) {
      return Scaffold(
        appBar: AppBar(
          bottom: TabBar(
            controller: _tabController,
            tabs: myTabs,
          ),
        ),
        body: TabBarView(
          controller: _tabController,
          children: myTabs.map((Tab tab) {
            final String label = tab.text!.toLowerCase();
            return Center(
              child: Text(
                'This is the $label tab',
                style: const TextStyle(fontSize: 36),
              ),
            );
          }).toList(),
        ),
      );
    }
  }
 
```
