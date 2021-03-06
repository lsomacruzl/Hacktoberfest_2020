<h1 align="center">Makefile</h1>


<p align="center">
  <img src="/blogs/img/makefile/mlogo.png" height=400 width=800>
</p>
  
                                                            
Makefile is based on a utility provided by GNU known as make utility. It is basically the information that tells make how to recompile a system comes from reading a data base called the makefile. The GNU make utility was implemented by Richard Stallman and Roland McGrath. This utility is helpful in automatic compiling of large chunk of programs (mainly in C/C++) to reduce the amount of manpower required in compiling and recompiling programs.

Once we build a makefile ,we need not to worry about running gcc and g++ commands rather than the makefile will do all the job with its execution command.


<h1 align="center">Naming Convention of the file</h1>


Naming of a makefile is standard as make utility search some particular key terms while searching the files.

Names that can be used while creating makefile: makefile, Makefile, GNUmakefile
Among all these names, ‘Makefile’ is most common and recommended to be used as file name.


<h1 align="center">Variables</h1>


A variable is a name defined in a makefile to represent a string of text, called the variable’s value. These values are substituted by explicit request into targets, prerequisites, recipes, and other parts of the makefile. 
Variables are accessed by ‘$’ symbol.


<h1 align="center">Basic structure of makefile</h1>


The simplest structure of makefiles include rules which states the target , prerequesites and the command we want to perform known as recipe.

Prerequisites :- These are the files which are necessary to implement a recipe.

Recipe :- Set of commands which are to be implemented to generate targets.

Targets :- The targets are file names separated by spaces which will be the made when the recipe will be executed.

Syntax of a rule =>

                  targets : prerequisites
                  
                             recipe
                                  
(Note that the recipe is written after a tab space in a new line.)

Example => 

            compile: hello.cpp

                     g++ hello.cpp


<h1 align="center">Hands On Example</h1>


First create some cpp files and a header file to provide a whole code to the compiler in a distributive manner.

1. main.cpp
 
<p align="center">
  <img src="/blogs/img/makefile/m8.png" height=300 width=700>
</p>

2. factorial.cpp
 
<p align="center">
  <img src="/blogs/img/makefile/m7.png" height=300 width=700>
</p>

3. hello.cpp

<p align="center">
  <img src="/blogs/img/makefile/m9.png" height=300 width=700>
</p>
 
4. functions.h

<p align="center">
  <img src="/blogs/img/makefile/m6.png" height=300 width=700>
</p>
 


The simple g++ command is used in terminal in normal ways without makefiles but it gets tedious if number of files increases. 


 <p align="center">
  <img src="/blogs/img/makefile/m1.png" height=200 width=1200>
</p>
 


Now create a makefile named as “Makefile”.


 <p align="center">
  <img src="/blogs/img/makefile/m2.png" height=250 width=1200>
</p>


Inside the makefile, write a simple target and g++ command in the recipe.


<p align="center">
  <img src="/blogs/img/makefile/m3.png" height=200 width=1200>
</p>

 
Now run simple ‘make’ command which will by default implement the first rule.


<p align="center">
  <img src="/blogs/img/makefile/m4.png" height=250 width=1200>
</p>
 
 
Also, a specific rule can also be implemented in a list of rules by using command ‘make <target-name>’.




Here’s a example for above command. Update the makefile with atleast two rules and then implementing specific rules. 


<p align="center">
  <img src="/blogs/img/makefile/m10.png" height=200 width=1200>
</p>


<p align="center">
  <img src="/blogs/img/makefile/m5.png" height=400 width=1200>
</p>
 


 

Now update the makefile to create various rules for the example of distributive compiling.


  <p align="center">
  <img src="/blogs/img/makefile/m11.png" height=400 width=1200>
</p>
 
 
Here, object files (.o) are generated from the source code files and then all the result is generated by compiling all the object files.

Also note that, the ‘clean’ target is used to delete all object files and result file here. 

  
<p align="center">
  <img src="/blogs/img/makefile/m12.png" height=250 width=1200>
</p>  


<p align="center">
  <img src="/blogs/img/makefile/m13.png" height=250 width=1200>
</p>  
 

Here ‘make all’ will find the prerequisites for all target, will analyse how this prerequisite can be generated from the source code files like here result need all object files and object files need source code files for their creation.

Also, we know about the DRY (Don’t repeat yourself) thing and we can see that our current makefile has considerable amount of code repetition such as g++ and -c in all recipes.


 <p align="center">
  <img src="/blogs/img/makefile/m11.png" height=400 width=1200>
</p>

                                                                
 We can reduce code repetition by using variables in makefile.
 Assign g++ and its flags in some variables, we can also do this with file names but we will keep it simple.


<p align="center">
  <img src="/blogs/img/makefile/m14.png" height=400 width=1200>
</p>
 

Here we have assigned ‘g++’ in ‘CC’ and ‘-c -Wall’ in ‘CFLAGS’ and access them with ‘$’ sign as shown.

 
<p align="center">
  <img src="/blogs/img/makefile/m15.png" height=400 width=1200>
</p> 
 
  
By following these simple rules and conventions of makefile, we can use them in big projects to reduce man power with compiling program files every time.


