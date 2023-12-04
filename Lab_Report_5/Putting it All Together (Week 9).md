# Lab Report 5 - Putting it All Together (Week 9)
**Part 1 – Debugging Scenario**<br>
Design a debugging scenario, and write your report as a conversation on EdStem. It should have:<br>

<div class="message" style="background-color: #f0f0f0; padding: 10px; border-radius: 5px; margin: 10px 0;">
  <p><strong>Student:</strong> Hi there! For my Lab_report 3 I'm trying to do add a method to the ArrayExamples class, with this class I wanted to calculate average without the lowest value. But its not passing my test code. I've attached the error output I got from the test.
![image](L5_error.png)
</p>
</div>
<div class="message" style="background-color: #d3e5fc; padding: 10px; border-radius: 5px; margin: 10px 0; text-align: right;">
  <p><strong>TA:</strong> Hello! Have you tried printing out the values before and after the loop where the bug is located. Let me know wheather you have unother question and what you find from your output</p>
</div>
<div class="message" style="background-color: #f0f0f0; padding: 10px; border-radius: 5px; margin: 10px 0;">
  <p><strong>User A:</strong> Thank you for the guide, After trying the method you told me, now I can see the error is occuring on the comparison if statement. It's returning 3 as lowest value while the correct value should've been 1. The lowest values is not updating after each iteration.
Here is the screenshot of my output.</p>
</div>


*Information needed about the setup:<br>
    + I used the code we used for lab 3 [https://github.com/gir-ma/lab3.git] this file contains ```ArrayTests.java```,  ```ArrayExamples.class```, ```ArrayExamples.java ```, ```ArrayTest.class ```, ```ArrayTest.java```, ```CommandScript.sh```.<br>
   
   + The snippet of the code with bug before fixing the bug is: <br>
  
    ```
    static double averageWithoutLowest(double[] arr) {
    if(arr.length < 2) { return 0.0; }
    double lowest = arr[0];
    for(double num: arr) {
      if(num == lowest) { lowest = num; }
    }
    double sum = 0;
    for(double num: arr) {
      if(num != lowest) { sum += num; }
    }
    return sum / (arr.length - 1);
  }```
   + The full command line (or lines) you ran to trigger the bug<br>
    ```
for(double num: arr) {
      if(num == lowest) { lowest = num; }
    }```
  + A description of what to edit to fix the bug<br>
To fix the bug following the TA's response I updated the loop like the following,<br>
   
    ```
    for(double num: arr) {
      System.out.println("Current value: " + num);
      if(num == lowest) { lowest = num; }
      System.out.println("Updated lowest value: " + lowest);
    }```
Then I fixed the line as follow and got the right output.<br>

```
  for(double num: arr) {
      System.out.println("Current value: " + num);
      if(num < lowest) { lowest = num; }
      System.out.println("Updated lowest value: " + lowest);
    }
```

**Part 2 – Reflection**<br>
In a couple of sentences, describe something you learned from your lab experience in the second half of this quarter that you didn’t know before. It could be a technical topic we addressed specifically, something cool you found out on your own building on labs, something you learned from a tutor or classmate, and so on. It doesn’t have to be specifically related to a lab writeup, we just want to hear about cool things you l
