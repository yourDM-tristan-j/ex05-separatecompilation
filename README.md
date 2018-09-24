## Exercise: Separate Compilation (25 Points)

The objective of this project is to familiarize your self with namespaces and separate compilatin.

The first thing you will need to do is fork and clone this assignment
from GitHub. Follow the instructions 
[here](https://github.com/sbcc-cs140-fall2018/Course-Information/wiki)
to get started. 

Be sure that you fork the project first and use the URL from
the forked project when you clone it in CLion.

This assignment is based on the Programming Project 1 from Chapter 11 of the text book, Absolute C++, on page 510 (5th Edition). 

This exercise is intended to illustrate namespaces and separate compilation in your
development environment. You should use the development environment you regularly 
use in this course for this exercise. In a file `f.h` , place a declaration of `std::string f( )`
in namespace `edu::vcccd::vc::csv13::A`. In a file `g.h`, place a declaration of `std::string g( )` in namespace `A` . In files
`f.cc` and `g.cc` , place the definitions of `std::string f( )` and `std::string g( )`, respectively.
Place the definitions of `std::string f( )` and `std::string g( )` in namespace `edu::vcccd::vc::csv13::A` . The functions
should return the file they are contained in using the `__FILE__` macro defined as part
of the standard C++. Like:

`return __FILE__;`

This line of code will return the path to the `.cc` file and should look something like:

`/home/aknight/CS140/separatecompilation/src/f.cc`

on Linux and Mac and something like:

`C:\Users\aknight\CS140\separatecompilation\src\f.cc`

on Windows. The unit tests included with this project should work with either output.

In another file, `main.cc` , put your main function, `#include` the minimum collection of files to provide
access to the names from namespace `edu::vcccd::vc::csv13::A` . In your main function call the functions
`f` then `g` . Compile, link, and execute using your development environment. While this executable will
not be part of the testing, I will check for it as part of the last 5 points of the assignment.

This project acted as a basis for this assignment, and as such the description here is the source of truth. Remember: when in doubt consult this assignment description.

### Writing the code for this Project

Writing the code for this project is very simple. You will create five files: separate headers for each of the `f` and `g` functions and implementations of these functions in the corresponding `.cc` files, and `main.cc`.

You will write two functions called `A::f` and `A::g`, each in their own `.cc` file. These two functions return the path
to their implementation file, as explaine above.

##### f.h and g.h

First you'll need to create `f.h` and `g.h`. These files must be named exactly this. If you misspell, or use different capitalization, the test program will not compile.

In CLion in the project explorer, right-click the `include` directory
and chose `New => C++ Header File`. 

Under **Name** fill in f. CLion will add the `.h` extension. Press **OK**. You should now see the file `f.h` in
the project explorer in the `include` directory.

Write your declaration of the `f` in here in the `edu::vcccd::vc::csv13::A` namespace.

Repeat this same process for `g.h`

##### Implementation

Next you'll need to create the implementation, separately from the declaration, of the `A::f` and `A::g` functions. This should be done in `f.cc` and `g.cc` files, respectively, in the `src` directory. Make sure these files have the extension `.cc` and are not named `main.cc`. 

In CLion in the project explorer, right-click the `src` directory
and chose `New => C++ Source File`. 

Under **Name** fill in
f. CLion will add the extension, but by default 
adds the `.cpp` extension. All projects in this class will
use the `.cc` extension. Select `.cc` in the **Type** drop-down
and press **OK**. You should now see the file `f.cc` (or whatever you named the file) in
the project explorer in the `src` directory.

Write your implementation of the `f` in here in the `edu::vcccd::vc::csv13::A` namepspace.

Repeat this same process for `g.cc`

#### main()

For this project you will need to create a `main()` function in a file named `main.cc` in the `src` directory. It is very important that you name it exactly this way, or things might not compile properly.

In CLion in the project explorer, right-click the `src` directory
and chose `New => C++ Source File`. 

Under **Name** fill in
main. CLion will add the extension, but by default 
adds the `.cpp` extension. All projects in this class will
use the `.cc` extension. Select `.cc` in the **Type** drop-down
and press **OK**. You should now see the file `main.cc` in
the project explorer in the `src` directory.

### Running the code for this project

Running this code should be straightforward. In the drop-down 
menu in the upper right-hand corner you should see a *Run
Configuration* called `SeparateCompilation | Debug`. Make sure this 
configuration is selected and press the play button next to it.
In the **Run** view below the code you should see the output 
of running the program. It should look something like this:

```bash
/home/aknight/CS140/separatecompilation/src/f.cc
/home/aknight/CS140/separatecompilation/src/g.cc

Process finished with exit code 0
```
Success! Now you can move on to testing your code.

### Testing the code for this project

Testing the code for this project is similar to running your code
as outlined above. In the drop-down menu in the upper right-hand
corner select the configuration `SeparateCompilation_Gtest` and press the 
play button next to it. In the **Run** view below the code you should
see the output of running these tests. It should look something
like this:

```bash
Running main() from gtest_main.cc
[==========] Running 2 tests from 1 test case.
[----------] Global test environment set-up.
[----------] 2 tests from MovieReviewsTest
[ RUN      ] MovieReviewsTest.F
[       OK ] MovieReviewsTest.F (0 ms)
[ RUN      ] MovieReviewsTest.G
[       OK ] MovieReviewsTest.G (1 ms)

Your unit test score is 20 out of 20
The assignment is worth a total of 25 where the remaining points
comes from grading related to documentation, algorithms, and other
criteria.

[----------] 2 tests from MovieReviewsTest (1 ms total)

[----------] Global test environment tear-down
[==========] 2 tests from 1 test case ran. (1 ms total)
[  PASSED  ] 2 tests.

Process finished with exit code 0
```

Remember, You should also see your score for this
assignment minus code styling points which I will add later.

### Submitting the code for this project

First, right click on the project name, then select `Git -> Commit Directory...`. 
Make sure only the files you want to push are selected, `main.cc`, `f.h`, `g.h`, `f.cc` and `g.cc`.
Then uncheck `Perform code analysis` and `Check TODO`. It's OK to leave them checked,
but committing will take longer. Leave `Run git hooks` checked. Put a message in `Commit Message`
and then press the **Commit** button. If anything goes wrong check the _Version Control_ view
in the lower left corner and select the _Console_ tab.
 
Finally, right click on the project name,
then select `Git -> Repository -> Push...`. Follow the onscreen directions
and press **OK**. This step will run the tests again, check that everything is OK
and then submit them to the cloud to have the tests run for grading.

If you do not understand these directions, or wish to do them on the command
line rather than in CLion, then read these [directions](https://github.com/sbcc-cs140-fall2018/Course-Information/wiki/How-to-Turn-In-Every-Project).
