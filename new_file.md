# Lab Report 1
## Remote Access and Filesystem

![Image](CS15L_1.png)

1. The working directory was `/home` when running the following commands: 
   - `ls` returned `lecture1` because the `ls` command lists all the files in the current directory. 
 
   - `cd` returned nothing because we are already inside the root directory named `home`.
   
   - `cat` allows us to read and write directly to a file. It did not do anything because we fed it zero arguments.
     

![Image](CS15L_2.png)

2. The working directory was `/home` when running the following commands:
 
   - `ls` returned `Hello.class Hello.java messages` because the `ls` command lists all the files inside of the directory `lecture1`. 
 
   - `cd` moved the working directory inside of `lecture1`. 
     
   - `cat` returned an error because `lecture1` is a directory, not a file we can read and write to. 
     

![Image](CS15L_3.png)

3. The working directory was `/lecture1` when running the following commands: 
 
   - `ls` returned a list of all the files with the name `Hello.java`.
   - `cd` command with a file as an argument threw an error because the file is not a directory.
   - `cat` with a file as the argument returned the contents of the file right on the command line.




   
