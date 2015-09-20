Argument Parser
===========
&emsp;A program designed, coded, and built by a group of seven people.
 This program was designed as a vehicle for understanding the scrum process.
It was completed over ten weeks, with two week iterations as our sprints.
This program was written in Java. It contains seventy unit tests, four acceptance
tests, and has ninety-eight percent code coverage. Also included is multiple
demonstrations to show the functionality of the code.

&emsp;In the Argument Parser program are four class files to handle different
functionality and storage of multiple arguments, and there are also nine
different exception classes included. 

#Classes#
###ArgumentParser###
&emsp;This is the main class used in the program. It can add any amount of both
types of arguments to be expected, add arguments to a specified group, set the
program description, stop the program and return a help menu, and print the program
information. There are multiple types of arguments used in this program, positional
arguments and named arguments. 

Named arguments are given as `argument1`

Positional arguments are given as `--argument2`

Shorthand arguments have the same functionality as positional arguments are given as `-a3`

###Argument###
&emsp;This class is used to hold the positional arguments given to the program.
Positional arguments in this program are those without any dashes before the 
argument itself.


###NamedArgument###
&emsp;This class inherits most of its functionality from the Argument class.
What is different about this is these arguments can be put in any order when
parsed by the program. These arguments can also be set to be required, be used
in a defined shorthand, or placed in a group of arguments.

###XMLManager###
&emsp;This class is used to save and load arguments into an XML file. When an
argument is saved it saves:
- Type of argument
- The name of the argument
- The description of the argument
- The type of argument
- The restricted values
- If the argument is required or named.
- If the named argument is referenced by shorthand.

#Exceptions#
###ArgumentAlreadyInGroupException###
&emsp;When an argument is already in a group and is being added to the same group,
this exception is thrown.

###InvalidArgumentException###
&emsp;When an argument value does not match the appropriate type defined by the
argument, this exception is thrown.

###MissingArgumentValueException###
&emsp;When an argument is called with no value , this exception is thrown.

###NotAllArgumentsUsedException###
&emsp;Thrown when not all required arguments are used.

###NotEnoughArgumentsException###
&emsp;Thrown when not enough arguments are used.

###NotInGroupException###
&emsp;Thrown when the user tries to get the name of a group an argument is in,
but that argument is not in a group.

###NotInTheSameGroupException###
&emsp;An exception thrown when two arguments are trying to be used, but they are
not in the same group.

###TooManyArgumentsException###
&emsp;An exception that is thrown when too many arguments are being used.

###UnknownArgumentException###
&emsp;An exception that is thrown when a requested argument can not be found.