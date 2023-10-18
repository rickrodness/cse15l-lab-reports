# Lab Report 1
## Remote Access and Filesystem

![Image](CS15L_1.png)

1. The working directory was `/home` when running the following commands:

   a. `ls` returned `lecture1` because the `ls` command lists all the files in the current directory. In this case, the directory was `/home`, so it listed the only directory inside of home, which was `lecture1`. No error occurred since the output is what I would expect, as `lecture1` is the only visible item inside the current working directory.

   b. `cd` returned nothing because we are already inside the root directory named `home`. No error occurred.

![Image](unnamed.png)

   c. `cat` without any arguments does not display anything because it requires a file to read from. No error occurred. It seemed to respond back whatever I typed after back to the terminal. This is because `cat` is reading from the keyboard and echoing my inputs to the screen.

2. The working directory was `/home` when running the following commands:

![Image](image_1.png)

   a. `ls` returned `Hello.class Hello.java messages` because the `ls` command lists all the files inside of the directory `lecture1`. No error occurred.

![Image](image_2.png)

   b. `cd` moved the working directory inside of `lecture1`. No error occurred.

![Image](image_3.png)

   c. `cat` with `lecture1` as an argument prompted the user that `lecture1` is a directory, not a file we can read or write to. An error did occur when calling the `cat` command with a directory; this is not allowed.

3. The working directory was `/lecture1` when running the following commands:

![Image](image_4.png)

   a. `ls` returned a list of all the files with the name `Hello.java`. No error occurred.

![Image](image_5.png)

   b. `cd` command with a file as an argument threw an error because the file is not a directory. An error occurred because the file is not a directory we can move to; `cd` is for changing to a different directory.

![Image](image_6.png)

   c. `cat` with a file as the argument returned the contents of the file right on the command line. No error occurred.



   
