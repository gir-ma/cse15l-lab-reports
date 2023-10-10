# **The basic filesystem commands** <br> 
Below are some examples of how to command file system that I learned in the first week of my class.<br>
```cd``` **Change Directory**
is used to change the current working directory in the terminal.<br> 
![image](cd.png)<br>
The ```cd``` command without any argument redirected me to the home directory. Because I was already in the home directory, the command without argument stays in the same working area we already are. The ```cd``` commond with a path to directory as an argument change the working directory to the given path, in my case it changed my working area from ```home``` to ```messages``` . But when I pass the path to file- ```cd en-us.txt``` it returns that its not a directory.<br>
```ls``` **List**
is used to list the contents of the current directory.<br> 

![image](ls.png) <br>
The ```ls``` command without any argument returned the two folders I have in ```home```, ```lecture1``` and ```trial1``` because those are the immidiete contents in that specific area. Also when I pass the ```ls``` command with path to directory, it lists the files in that directory. But when I pass it with path to file as an argument, it return the actual path of the file because there is no other directory or file in it.<br>
```cat``` **Concatenate**
is used to display the contents of a file in the terminal.<br> 

![image](cat.png) <br>
When I use the ```cat``` command without no argument in home working directory, it returns an empty line. When I pass path to directory, it return that it a directroy. But when I pass a path to a file as an argument it displayed the message in the file. 
