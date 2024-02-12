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
  code
  ```
  After:
  ```
  code
  ```
<Explaination of Why this fixes the bug]

---
Now, lets switch gears and discuss some bash commands. Particularly we'll focus on the find command. There are a wide variety of ways to use the find command and a variety of ways to modify the command in the command line. We'll look at 4 ways to use this command: __, __, __, __.

---
Way 1 - information from ___:
```
code
```
Explaination
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
