# Lab Report 1
Developing skills in remote access and filesystem is vital for programmers and anybody else who uses computers in their day to day. Here I'll outline basic commands like cd, ls, and cat, and explain various use cases for all of them. 

---
Lets start with cd (change directory) when it has no arguments/paths:
```
[user@sahara ~]$ cd 
[user@sahara ~]$
```
As we can see here, when the command was run, the programmer was in their home directory and as we can see, there was no change in the working directory after running the cd command. We get this output, or rather this lack of output becuase we are telling the computer to change the working directory but not specifying what to change that directory to, leading the system to stay in its origional directory. While this is not the goal most programmers have when using cd, it is also not an error as no error messages are thrown.   

Lets now examine what happens when running cd with a path to a directory as its argument:
```
[user@sahara ~]$ cd lecture1/
[user@sahara ~/lecture1]$
```
In this case, given a path to a directory ('lecture1') as the argument, cd changes the working directory to the directory given as the argument (in this case, 'lecture1'). When the command was run, the working directory was the home directory and after running the command, the directory is the argument passed in. This works because the 'lecture1' directory was inside of the home directory, so when the programmer used the cd command, the computer could successfully locate and switch to the directory entered in the argument. This is the intended function of cd and does not cause any errors.   

Finally, lets look at what happens when cd is run with a path to a file as the argument:
```
[user@sahara ~/lecture1]$ cd Hello.java
bash: cd:
[user@sahara ~/lecture1]$
```
