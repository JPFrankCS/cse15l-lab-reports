# Lab Report 1 - Remote Access and FileSystems
Developing skills in remote access and filesystem is vital for programmers and anybody else who uses computers in their day to day. Here I'll outline basic commands like cd, ls, and cat, and explain various use cases for all of them. Throughout, the command, pwd (print working directory) is used to display the directory the program is in at certain points in the code.

---
Lets start with cd (change directory) when it has no arguments/paths:
```
[user@sahara ~]$ pwd
/home
[user@sahara ~]$ cd 
[user@sahara ~]$ pwd
/home
```
As we can see here, when the command was run, the programmer was in their home directory and as we can see, there was no change in the working directory after running the cd command. We get this output, or rather this lack of output becuase we are telling the computer to change the working directory but not specifying what to change that directory to, leading the system to stay in its origional directory. While this is not the goal most programmers have when using cd, it is also not an error as no error messages are thrown.   

Lets now examine what happens when running cd with a path to a directory as its argument:
```
[user@sahara ~]$ pwd
/home
[user@sahara ~]$ cd lecture1/
[user@sahara ~/lecture1]$ pwd
/home/lecture1
```
In this case, given a path to a directory ('lecture1') as the argument, cd changes the working directory to the directory given as the argument (in this case, 'lecture1'). When the command was run, the working directory was the home directory and after running the command, the directory is the argument passed in. This works because the 'lecture1' directory was inside of the home directory, so when the programmer used the cd command, the computer could successfully locate and switch to the directory entered in the argument. This is the intended function of cd and does not cause any errors.   

Finally, lets look at what happens when cd is run with a path to a file as the argument:
```
[user@sahara ~/lecture1]$ pwd
/home/lecture1
[user@sahara ~/lecture1]$ cd Hello.java
bash: cd: Hello.java: Not a directory
[user@sahara ~/lecture1]$ pwd
/home/lecture1
```
When the command was run, the working directory was the lecture1 directory and the user attempted to change the working directory to the Hello.java file. Here we see that from the first to the third line, the working directory was not changed because cd can only change the directory to another directory and not a file as the code here attempts to do. Running the code seems to cause an error seen in the middle line of code. This error is thrown because the user attemped to pass a file into the cd command when the cd command only functions when passed directories/files.

---
Next, we can examine the ls (list) command when it is not given any arguments
```
[user@sahara ~/lecture1]$ ls
Hello.class Hello.java messages README
```
The command was run in the working directory 'lecture1' and listed all files and folders in the lecture1 directory. Note that it did not open any folders in this directory, merely displaying their names and nothing inside of them. We get this output becuase having no arguments to ls means that it is run in its current directory, that being lecture1. Due to this, it prints the names of the files and folder inside of the lecture1 direcotry.

Now, what will happen when ls is run with a directory path as an argument?
```
[user@sahara ~/lecture1]$ ls messages/
el-lt.txt en-us.txt es-mx.txt zh-cn.txt
[user@sahara ~/lecture1]$
```
This command was run in the working directory 'lecture1' and listed all the files inside of the messages directory. This happened because ls was given another directory as an argument, leading it to list the files inside of that passed in directory. Note that while the code technically enters the messages directory and lists its files, the third line of code shows that the active directory remains lecture1. There is no error thrown by this code.

Next, lets look at the ls command when it has a file path as its argument
```
[user@sahara ~/lecture1]$ ls Hello.java
Hello.java
```
This command is run in the working directory 'lecture1' and output the name of the file that was passed into it. This happened because ls was passed a single file so the only file name it could output is the very file it was passed. It wasn't passed a folder, so it wouldn't be able to list the contents of that folder. There is no error in the code.

---
Finally, what does the cat (concatonate) command do when run with no arguments?
```
[user@sahara ~/lecture1]$ cat
a
a
test
test
```
This command is run in the lecture1 directory and has no immediate effect except for the dissapearance of the prompt (user@sahara...). However, whenever any text is entered to the terminal, that same text is printed on the next line. This is because cat is not given any folders or files to print, so it asks the user what it should print and goes on to print that to the terminal. This will go on until the user enters control-c. This does not cause any errors to be thrown.

What happens when cat has a directory path as an argument?
```
[user@sahara ~/lecture1]$ cat messages/
cat: messages/: Is a directory
```
This command, run in the lecture1 directory prints the message seen here. While the cat command expects a file to be passed as argument, it recognizes that messages/ is a directory and informs the user of that fact. This is not an error, rather it is a print statement by the cat command.

Finally, what if the cat command has a file path as an argument?
```
[user@sahara ~/lecture1]$ cat Hello.java
import java.io.IOException;
import java.nio.charset.StandardCharsets;
import java.nio.file.Files;
import java.nio.file.Path;

public class Hello {
  public static void main(String[] args) throws IOException {
    String content = Files.readString(Path.of(args[0]), StandardCharsets.UTF_8);    
    System.out.println(content);
  }
```
This command is run in the lecture1 directory and prints the contents of the file passed in as argument. This is the function of the cat command as it prints the contents of its arguments. If two files were passed as arguments it would print both. Notice that despite this being a java file and not a text file, cat prints it as if it is a plaintext file. There are no errors thrown with this use of cat.
