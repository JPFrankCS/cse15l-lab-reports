### Bugs and Commands 

---
Today, lets start by looking at bugs and testing. We'll be looking at a method called `reverseInPlace` that takes an `int[] arr` as argument and is meant to reverse the input array.  
Here is a failure inducing input for the program:
```
@Test
public void testReverseInPlace() {
    int[] input1 = { 5, 6, 7, 8 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 8, 7, 6, 5 },input1);
}
```
Despite this, there are still inputs that don't cause a failure such as:
```
@Test 
public void testReverseInPlace() {
    int[] input2 = { 3 };
    ArrayExamples.reverseInPlace(input2);
    assertArrayEquals(new int[]{ 3 }, input2);
}
```
Now lets look at the result of running these tests:
[image]
This failure is called a symptom. Now that we know the symptom and the input that leads to it, lets take a look at the code:  
  Before:
  ```
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
  ```
  After:
  ```
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length/2; i ++) {
      int temp = arr[i];
      arr[i] = arr[arr.length - i - 1];
      arr[arr.length - i -1] = temp;
    }
  }
  ```
Initially, the code simply replaced the first half of the array with the values in the second half in reverse order, as it should. However, when it got to the second half of the array, it then replaced the second half with the first half. While this would have worked if the array hadn't been modified, it has been, so in the second half of the `for` loop, the second half is being replaced with the first half, which has already been overridden with the second half. This results in an array like `[1,2,3,4]` being reversed into `[4,3,3,4]` instead of `[4,3,2,1]` as it should have. The fix seen in the after works because the value from that first half of the array is stored in a temporary `int` variable before the element is overriden with the corrosponding element from the back half of the array. That `int` can then be put into the second half of the array in its correct spot, fixing the bug. Also note that the `for` loop only iterates through half the array becuase both halves of the array are being worked on in the new code above.

---
Now, lets switch gears and discuss some bash commands. Particularly we'll focus on the `find` command. There are a wide variety of ways to use the `find` command and a variety of ways to modify the command in the command line. We'll look at 4 ways to use this command: `-type`,` __`,` __`, `__`. All information on this command and its modifiers came from https://linuxhandbook.com/find-command-examples/ (linuxhandbook.com).

---
`-type`
```
[user@sahara ~/docsearch/technical]$ find . -type f | head
./911report/chapter-3.txt
./911report/chapter-11.txt
./911report/chapter-13.5.txt
./911report/chapter-9.txt
./911report/chapter-7.txt
./911report/chapter-8.txt
./911report/chapter-13.1.txt
./911report/chapter-5.txt
./911report/chapter-10.txt
./911report/chapter-13.2.txt
```
Note that the `| head` command simply shortens the output to a readable level and is beyond the scope of this discussion of the `find` command. Here, the command depicted searches the current directory and prints relative paths to all files. This is due to the `-type f` telling the program to look for files as opposed to directories. This may be useful if the programmer wants to count or work with all the files in their file structure without working with any directories.
```
code
```
Explaination

---
Way 2 - information from ___:
```
code
```
Explaination
```
code
```
Explaination

---
Way 3 - information from ___:
```
code
```
Explaination
```
code
```
Explaination

---
Way 4 - information from ___:
```
code
```
Explaination
```
code
```
Explaination
