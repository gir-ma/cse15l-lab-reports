# Lab Report 3 - Bugs and Commands (Week 5)
**Part 1 - Bugs**
* A failure-inducing input for the buggy program, as a JUnit test and any associated code (write it as a code block in Markdown)
```
@Test 
	public void testReverseInPlace() {
    int[] input1 = { 1,2,3,4 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 4,3,2,1 }, input1);
	}
``` 
  
* An input that doesn’t induce a failure, as a JUnit test and any associated code (write it as a code block in Markdown)
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
  
* The bug, as the before-and-after code change required to fix it (as two code blocks in Markdown)
  ```
static void reverseInPlace(int[] arr) {
     for(int i = 0; i < arr.length; i += 1){
      arr[i] = arr[arr.length - i - 1];
    }
  }
  ```

```
static void reverseInPlace(int[] arr) {
     for(int i = 0; i < arr.length/2; i += 1){
      int tempo = arr[i];//arr.length/2
      arr[i] = arr[arr.length - i - 1];
      arr[arr.length-i-1] = tempo;
    }
  }
```
*     Briefly describe why the fix addresses the issue.
