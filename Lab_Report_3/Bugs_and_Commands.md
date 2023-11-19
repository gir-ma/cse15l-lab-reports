# Lab Report 3 - Bugs and Commands (Week 5)
**Part 1 - Bugs**
* A failure-inducing input for the buggy program, as a JUnit test and any associated code 
```
@Test 
	public void testReverseInPlace() {
    int[] input1 = { 1,2,3,4 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 4,3,2,1 }, input1);
	}
``` 
  
* An input that doesn’t induce a failure, as a JUnit test and any associated code 
```
@Test 
	public void testReverseInPlace() {
    int[] input1 = { 4 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 4 }, input1);
	}
``` 
  
* The symptom, as the output of running the tests (provide it as a screenshot of running JUnit with at least the two inputs above)
![image](failure_inducing.png)<br>
I tried to run a test for a buggy code with two diffirent inputs. The first one has four numbers and the test failed ```arrays first differed at element [2]; expected:<2> but was:<3>```; but with the second test I used an input that doesn't induce failure, one digit, and the test returned no failure eventhough we know it has bugs.<br>
  
* The bug, as the before-and-after code change required to fix it
  # Before 
```
static void reverseInPlace(int[] arr) {
     for(int i = 0; i < arr.length; i += 1){
      arr[i] = arr[arr.length - i - 1];
    }
  }
```
This code trys to reverse an array in place, but iIt uses the same array to store both the original and reversed values, overwriting the original values before they can be properly reversed. If I use input {4,3,2,1}, the result will be {1,2,1,1}.<br>
# After fixed the bug
```
static void reverseInPlace(int[] arr) {
     for(int i = 0; i < arr.length/2; i += 1){
      int tempo = arr[i];//arr.length/2
      arr[i] = arr[arr.length - i - 1];
      arr[arr.length-i-1] = tempo;
    }
  }
```
In this one, it iterates through the first half of the array up to ```arr.length/2```. During each iteration, it swaps the element at index i with the element at the corresponding position from the end ```arr.length - i - 1```. The temporary variable ```temp``` is used to ensure that the original values are not overwritten before they are swapped. So this code reverses the array in correctly without losing data.<br>
# **Part 2 - Researching Commands**
**4 interesting command-line options or alternate ways to use the command ```find```**
* ```-name``` This option is used to search for files and directories by name. It allows you to specify a name or use wildcards to match names.<br>
_example 1_
```
girma@Gimma MINGW64 ~/Documents/GitHub/docsearch (main)
$ find -name "chapter-1.txt"
./technical/911report/chapter-1.txt
```
_example 2_<br>
Let's say I want to find all files in the project that have "chapter" in their name. We can use the ```-name``` option with a wildcard:<br>

```
girma@Gimma MINGW64 ~/Documents/GitHub/docsearch (main)
$ find -name "*chapter*"
./technical/911report/chapter-1.txt
./technical/911report/chapter-10.txt
./technical/911report/chapter-11.txt
./technical/911report/chapter-12.txt
./technical/911report/chapter-13.1.txt
./technical/911report/chapter-13.2.txt
./technical/911report/chapter-13.3.txt
./technical/911report/chapter-13.4.txt
./technical/911report/chapter-13.5.txt
./technical/911report/chapter-2.txt
./technical/911report/chapter-3.txt
./technical/911report/chapter-5.txt
./technical/911report/chapter-6.txt
./technical/911report/chapter-7.txt
./technical/911report/chapter-8.txt
./technical/911report/chapter-9.txt
```

```-name "*chapter*"``` This part specifies the search criteria. The asterisks (*) then match any characters, so this command finds all files with "chapter" in their name, regardless of the characters before or after it.
This is useful for example when I want to locate files with a specific pattern in their name.<br>


* ```-type``` this option is used to filter files or directories based on their type (e.g., regular files, directories, symlinks, named pipes, sockets).<br>
_example 1_
```
girma@Gimma MINGW64 ~/Documents/GitHub/docsearch/technical/911report (main)
$ find -type f
./chapter-1.txt
./chapter-10.txt
./chapter-11.txt
./chapter-12.txt
./chapter-13.1.txt
./chapter-13.2.txt
./chapter-13.3.txt
./chapter-13.4.txt
./chapter-13.5.txt
./chapter-2.txt
./chapter-3.txt
./chapter-5.txt
./chapter-6.txt
./chapter-7.txt
./chapter-8.txt
./chapter-9.txt
./preface.txt
```
This ```-type``` connected with find command help us to reduce our search scope by the type of the file; in this case it'll return only the files.
_example 2_<br>
To find all directories in my project. I can use the ```-type``` option with the argument ```d``` to filter for directories:
```
girma@Gimma MINGW64 ~/Documents/GitHub/docsearch (main)
$ find -type d
.
./.git
./.git/hooks
./.git/info
./.git/logs
./.git/logs/refs
./.git/logs/refs/heads
./.git/logs/refs/remotes
./.git/logs/refs/remotes/origin
./.git/logs/refs/remotes/upstream
./.git/objects
./.git/objects/info
./.git/objects/pack
./.git/refs
./.git/refs/heads
./.git/refs/remotes
./.git/refs/remotes/origin
./.git/refs/remotes/upstream
./.git/refs/tags
./lib
./technical
./technical/911report
./technical/biomed
./technical/government
./technical/government/About_LSC
./technical/government/Alcohol_Problems
./technical/government/Env_Prot_Agen
./technical/government/Gen_Account_Office
./technical/government/Media
./technical/government/Post_Rate_Comm
./technical/plos
```
```-type d``` specifies the search criteria, it filters for directories, so this command finds and lists only directories in the specified location. This is useful when we want to focus specifically on directories and exclude regular files from the search results.<br>

* ```-size``` limits the search for files by size.<br>
_example 1_
```
girma@Gimma MINGW64 ~/Documents/GitHub/docsearch (main)
$ find -size +180k
./.git/objects/pack/pack-9155f305b04899d32718c159a69aedd038c25dbf.pack
./lib/junit-4.13.2.jar
./technical/911report/chapter-13.4.txt
./technical/911report/chapter-13.5.txt
./technical/911report/chapter-3.txt
./technical/government/About_LSC/commission_report.txt
./technical/government/Env_Prot_Agen/bill.txt
./technical/government/Env_Prot_Agen/multi102902.txt
./technical/government/Gen_Account_Office/d01591sp.txt
./technical/government/Gen_Account_Office/GovernmentAuditingStandards_yb2002ed.txt
./technical/government/Gen_Account_Office/pe1019.txt
./technical/government/Gen_Account_Office/Statements_Feb28-1997_volume.txt
```
This limits the size of the file we are looking for. It'll return the files in this terminal those has only less that the given size.<br> 

_example 2_

```
girma@Gimma MINGW64 ~/Documents/GitHub/docsearch (main)
$ find -size +800k
./.git/objects/pack/pack-9155f305b04899d32718c159a69aedd038c25dbf.pack
```

```-size +800M``` This part specifies the search criteria. The ```+``` before 800M means files larger than 800 megabytes. This command will find and list all files in the current directory and its subdirectories that are larger than 800 megabytes. 

* ```-mtime``` is used to search for files based on their modification time, allowing you to find files modified within a specific time frame.<br>
_example 1_

```
girma@Gimma MINGW64 ~/Documents/GitHub/docsearch/technical/911report (main)
$ find -mtime -1
./chapter-1.txt
```
This command will locate files modified within the past 1 days in 911report directory.<br>

_example 2_


```
girma@Gimma MINGW64 ~/Documents/GitHub/docsearch (main)
$ find -mmin -120
./.git/FETCH_HEAD
./.git/logs/refs/remotes/origin/HEAD
./.git/logs/refs/remotes/upstream/HEAD
./.git/objects
./.git/refs/remotes/origin
./.git/refs/remotes/origin/HEAD
./.git/refs/remotes/upstream
./.git/refs/remotes/upstream/HEAD
```

This command will find files modified less than 2 hours ago in the home directory. The -mtime option in the find command operates in terms of 24-hour periods. If we need to search for files based on a time frame in hours rather than days, we can use the ```-mmin``` option to search by minutes. we can also adjust the ```+``` and ```-``` sign to specify the given time ago or in less than a given time.<br>

_source_:[https://www.redhat.com/sysadmin/linux-find-command]<br>
ChatGPT,  
prompt: "How can we use the command find -time with different time frame like days and hours?"
