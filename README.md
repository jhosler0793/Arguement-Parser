Argument Parser
===========
&emsp;A program designed, coded, and built by a group of seven people.
 This program was designed as a vehicle for understanding the scrum process.
It was completed over ten weeks, with two week iterations as our sprints.
This program was written in Java. It contains ninety-two unit tests, four acceptance
tests, and has ninety-seven percent code coverage. Also included is multiple
demos to show the functionality of the code.

##My Role##
&emsp;Throughout the development of this project, I assisted with programming every class
along with unit tests, acceptance tests, and presenting a slideshow during our sprint reviews.

##Requirements##
- A [**JDK**](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)
 is required.
- [**RobotFramework**](http://robotframework.org/)
- [**Gradle**](https://gradle.org/)

##Tools##
- **Gradle**: Build tool
- **Git**: Version control
- **JUnit**: Unit testing
- **Jacoco**: Code coverage
- **RobotFramework**: Acceptance testing
- **Javadoc**: Creating the API

##Features##
###1.) User Friendly###
&emsp; When we were designing the program, we wanted it to be easily understood and accessible. When adding
an argument, we did not want someone to call a multiple methods to set up one argument. So when adding a
positional argument the user would call:

```java
parser.addPositionalArgument("Argument Name", "Argument Description", ArgumentParser.Types.INTEGER);
```

When a user wanted to add a named argument, the user would call:

```java
parser.addNamedArgument("Argument Name", "Argument Description", ArgumentParser.Types.BOOLEAN, false);
```

*All methods are listed and documented in the API*

###2.) Help Command###
&emsp; The help command will display all known information about the program. It will list the argument name,
the argument description, the argument type, if the argument has a default value it will list the default value,
it will display the name and description of the program, and will also display how to place arguments in the command line.

**Example:**
Inside of the PizzaOrder demo is an argument parser with 6 different arguments. When the demo is ran it will check to see if any
of the arguments contain '-h' or '--help'. If it does, then the help will override any other functionality in the program.

*Result when -h or -help is in the given values*
![alt text](http://i.imgur.com/bgeu7DU.png "A command line interface showing how the help command will display information)

###3.) Named Arguments###
&emsp; Named arguments in this program are optional arguments by default. Named arguments can be called by a specified shorthand when
adding the argument to the parser. Every named argument is required to have a default value so that if a named argument was used as a flag
then it would have a value to start at if it wasn't actually parsed.

````
parser.addNamedArgument("Raining", "r", "Is is raining?", ArgumentParser.Types.BOOLEAN, false);
````

&emsp; When wanting to make a named arugment required, the user would use the addRequiredNamedArgument method. Adding an argument using
this method will set a flag inside of the named argument to true, letting the program know this argument is required.

````
parser.addRequiredNamedArgument("Raining", "r", "Is it raining?", ArgumentParser.Types.BOOLEAN, false);
````

&emsp; Named arguments are not required to have a shorthand as shown in the first section of the README. These arguments can also be put in
any order when the program is ran and no problems will occur.

###4.) Positional Arguments###
&emsp; Positional arguments in this program are required by default and do not have a lot of added functionality like named arguments do. These
arguments will always be in the order added to the program and can not be re-ordered. These arguments are added only with the addPositionalArgument method
shown in the first section.

###6.) Grouping Arguments###
&emsp; Arguments can be placed into groups to call all of the arguments at once. This is best shown off in the NumberCrunch demo, where arguments
are added into groups to add, subtract, or multiply the two given arguments. Groups can also be set to be mutually exclusive that is also shown in
the NumberCrunch demo.

**Adding to Group Example**

*In this example, the argument "add" is put in the group "Addition"*
````
parser.addArgumentToGroup("add", "Addition");
````
*Result when the demo is ran:*
![alt text](http://i.imgur.com/C8wVUa1.png "Command line interface showing the result of adding two arguments")

**Mutual Exclusion Example**
*In this example, two arguments in different groups can not be used at the same time.*
````
parser.addArgumentToGroup("add", "Addition");
parser.addArgumentToGroup("sub", "Subtraction");
````
*Result when demo is ran:*
![alt text](http://i.imgur.com/y10U8z0.png "Command line interface showing the result of calling two groups at once")

###7.) Restricted Values###
&emsp; Arguments can also accept only certain values. This is show in the WritePizzaArgs demo. The user gives an object array to
attach to the argument, and the argument will only accept those values.
````
Object[] restrictedSizes = {"small", "Small", "medium", "Medium", "large", "Large"};

p.addPositionalArgument("size", "The size of the pizza (Small, Medium, or Large)", ArgumentParser.Types.STRING);

parser.setRestrictedValues("size", restrictedSizes);
````

If the user tries to give any other values to that argument, an exception will be thrown.

###9.) Additional Values###
&emsp; A named argument can hold more than one value. To do this the user would first set the argument to accept additional values by calling:
````
parser.readyAdditionalValues("Box", 3);
````
This would allow 3 values to be in the argument "Box".

**Example**

When running the program through command line, the argument "Box" will take in the next 3 values following it:

````
java -cp .;..\..\build\classes\main Demo -Box 10 20 30
````

###9.) Save with an XML Manager###
&emsp; When creating this program, our team was also tasked to write and read arguments from an XML file. This is used with the
XMLManager class. It will save every part of the argument to a file including:
- Arugment Name
- Argument Description
- Argument Type
- Number of Restricted Values
- Count of Additional Values
- Default Values

###10.) Error Handling with Created Exceptions###
&emsp; There were nine different exceptions our group had to make to allow errors from our program to be more descriptive.

1. **ArgumentAlreadyInGroupException** - Used for when the user tries to add an argument to a group the argument is already in.
2. **InvalidArgumentException** - When the user tries to put the wrong type of value into an argument, this exception is thrown.
3. **MissingArgumentValueException** - When the value is not included in an argument, this exception is thrown.
4. **NotAllArgumentsUsedException** - When all required arguments are not used, this exception is thrown.
5. **NotEnoughArgumentsException** - Used when a user puts too many arguments or values into the parser.
6. **NotInTheSameGroupException** - Thrown when two or more arguments are trying to be used but are not in the same group.
7. **TooManyArgumentsException** - When there are more arguments than values put into the parser, this exception is thrown.
8. **UnknownArgumentException** - Thrown when the user tries to call an argument that has not been added to the parser.
9. **NotInGroupException** - When a user tries to get the name of a group an argument is in, but the argument is not in a group, this exception is thrown.

###11.) Javadoc API###
&emsp; This library comes with a documented javadoc API for the entire library.

*The javadoc can be built by running the command* `gradle javadoc`

The API is located at:
````
\build\docs\javadoc\index.html
````


##Installation##
&emsp; After ArgumentParser is either cloned or extracted from the .zip file, the demonstrations
included are almost ready to be used. In command line, move to where the gradle.build file is
and then execute the command `gradle build` to build the required files.

*Upon seeing this screen, the demos will be ready to run.*
![alt text](http://i.imgur.com/YUsjSdB.png "A command line interface displaying the successful
compiling of the program.)

##Demos##
&emsp; All demos are available inside the demos folder. Inside are multiple demos
to show the functionality of the code. The NumberCrunch demo will show arguments can
be placed in groups. PizzaDemo2.0 will show required and restricted arguments. 
Shipping demo will show arguments can be called through a shorthand method.
XMLPizzaDemo will show that arguments can be written to and read from an XML file.

##Acknowledgements##
Credit is shared between Jonathan Hosler, Scott Troutman, Elgin Bowman, Adam Ingram,
Brandon Taylor, Pengzheng Yeng, Zachary Alwine.