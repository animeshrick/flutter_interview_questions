# flutter_interview_questions

## What is tree shaking in Flutter?
-> Tree shaking is an optimization technique to remove the unused module in 
the bundle during the build process.It is a dead code elimination technique used 
to optimize the code.

<h2>What is Flex box in Flutter?</h2>
->The Flex class in Flutter is used to display its children in a one-dimensional 
array. With this widget, you can control theaxis where the children are placed. 
This axis is called as the main axis.

## stf lifecycle 
-> createState,initState(),didChangeDependencies(),build(),
didUpdateWidget(),setState(),deactivate(),dispose()

- createState(): When the Framework is instructed to build a StatefulWidget, it 
immediately calls createState()

- mounted is true: When createState creates your state class, a buildContext is 
assigned to that state. buildContext is, overly simplified, the place in the 
widget tree in which this widget is placed. Here's a longer explanation. All 
widgets have a bool this.mounted property. It is turned true when the buildContext 
is assigned. It is an error to call setState when a widget is unmounted.

- initState(): This is the first method called when the widget is created (after the 
class constructor, of course.) initState is called once and only once. It must call 
super.initState().

- didChangeDependencies(): This method is called immediately after initState on the 
first time the widget is built.

- build(): This method is called often. It is required, and it must return a Widget.

- didUpdateWidget(Widget oldWidget): If the parent widget changes and has to rebuild 
this widget (because it needs to give it different data), but it's being rebuilt with 
the same runtimeType, then this method is called. This is because Flutter is re-using 
the state, which is long lived. In this case, you may want to initialize some data again, 
as you would in initState.

- setState(): This method is called often from the framework itself and from the developer. 
Its used to notify the framework that data has changed

- deactivate(): Deactivate is called when State is removed from the tree, but it might be 
reinserted before the current frame change is finished. This method exists basically because 
State objects can be moved from one point in a tree to another.

- dispose(): dispose() is called when the State object is removed, which is permanent. 
This method is where you should unsubscribe and cancel all animations, streams, etc.

- mounted is false: The state object can never remount, and error will be thrown 
if setState is called.


## Getter and Setter Methods 
--->Getter and setter methods are the class methods used to 
manipulate the data of the class fields. Getter is used to read or get the data of 
the class field whereas setter is used to set the data of the class field to some 
variable.
#### Ex:
- class Gfg {
- String geekName;
- String get get_geek_name{return geekName;}
- set set_geek_name (String name) {this.geekName = name;}
- //set set_geek_name (String name) {geekName = name;}
- }

- void main()
- {
- Gfg geek = new Gfg();
- geek.geek_name = "GeeksForGeeks";
- print("Welcome to ${geek.geek_name}");// op-Welcome to GeeksForGeeks
- }

## BuildContext() 
--->Every Flutter widget has an @override build() method with the argument 
of BuildContext.Every Widget has its own build() and its context.The BuildContext is the 
parent of the widget returned by the build() method.Helps to locate of the Widget 
in the widget tree.

## Dart static Keyword & Variable 
--->static [data_type] [variable_name];
The static keyword is used to declare the class variable and method.The static variable 
or methods are the same for every instance of the class.It generally manages the memory 
for the global data variable.

## Instance Method in Dart:
Unless the method is declared as static it is classified as an instance method in a 
class. They are allowed to access instance variables. 
To call the method of this class you have to first create an object.

## didchangedependancies():
In Flutter, didChangeDependencies() is called only a few moments after the state loads its dependencies.
With this method, we can use context outside of build().
### want to use MediaQuery.of(context) outside of build():
- @override
- void didChangeDependencies() {
-     // MediaQuery.of(context)
-     super.didChangeDependencies();
- }
- Widget build(BuildContext context) {
-    /* */
- }

## didUpdateWidget(Widget oldWidget):
didUpdateWidget() is called if the parent widget changes and has to rebuild this widget (because it 
needs to give it different data), but it's being rebuilt with the same runtimeType, then this method 
is called.This is because Flutter is re-using the state, which is long lived.

## deactivate():
The framework calls this method whenever it removes this State object from the tree. dispose, which 
is called after deactivate if the widget is removed from the tree permanently.
