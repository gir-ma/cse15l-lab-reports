## **The basic filesystem commands** <br> 
Below are some examples of how to command file system that I learned in the first week of my class.<br>  
```cd``` **Change Directory**
is used to change the current working directory in the terminal.<br> 
![image](cd.png)<br>
**with no argument**
* Working diroctory: ```/home```
* Explanation: The ```cd``` command without any argument redirected me to the home directory. 
* Output: not error but it's empty. Because I was already in the home directory, the command without argument stays in the same working area we already are.

**with a path to a directory as an argument**
* Working diroctory: ```/home```
* Explanation: The ```cd``` command with the argument ```/lecture1/messages``` changed my working diroctory to ```/home/lecture1/messages```. 
* Output: No error

**with a path to a file as an argument**
  * Working diroctory: ```/home/lecture1/messages```
  * Explanation: The ```cd``` command with the path to a file as an argument  ```cd en-us.txt``` it returns that its not a       directory.<br> 
  * Output: Error, Because cd means change directory, the agrument followed by cd is a path to a file, thus causing an         error

  
```ls``` **List**
is used to list the contents of the current directory.<br> 

![image](ls.png) <br>
**with no argument**
* Working diroctory: ```/home```
* Explanation: The ```ls``` command without any argument returned the two folders I have in ```home```, ```lecture1``` and ```trial1``` because those are the immidiete contents in that specific area.
* Output: No error;  ```lecture1``` , ```trial1```

**with a path to a directory as an argument**
* Working diroctory: ```/home```
* Explanation: when I pass the ```ls``` command with path to directory, it lists the files in that directory
* Output: No error; ```en-us.txt```, ```es-mx.txt```,  ```vi.txt```, ```zh-cn.txt```

**with a path to a file as an argument**
 * Working diroctory: ```/home```
 * Explanation: when I pass it with path to file as an argument, it return the actual path of the file because there       is no other directory or file in it.
 * Output: No error:

```cat``` **Concatenate**
is used to display the contents of a file in the terminal.<br> 

![image](cat.png) <br>
**with no argument**
* Working diroctory: ```/home```
* Explanation: This command prints out the contents of one or more files given by the arguments as the path. However, without a file path as an argument, this command will not print anything and will instead wait for the user to enter something. 
* Output:  not error but it's empty.

**with a path to a directory as an argument**
* Working diroctory: ```/home```
* Explanation: Since this command typically displays the contents of files provided by one or more file paths, using a path to a directory as an argument does not work in this case. 
* Output: error message stating that the given path is a directory 

**with a path to a file as an argument**
* Working diroctory: ```/home```
* Explanation: When a path to a file is specified by the cat command, the content inside the file will be printed.
* Output: the content of the es-mx.txt file
 
