# Lab Report 3: Bugs and Commands

## Part 1 - Bugs

### Bug in `reverseInPlace` from Lab 4 

#### Failure-Inducing Input

```java
@Test
public void testReverseInPlaceFailure() {
  int[] original = {1, 2, 3, 4, 5};
  ArrayExamples.reverseInPlace(original);
  assertArrayEquals(new int[]{5, 4, 3, 2, 1}, original); // This will fail 
}
```
### Non-Failure-Inducing Input
```java
@Test
public void testReverseInPlaceSuccess() {
  int[] original = {1, 2, 3, 4, 5};
  ArrayExamples.reverseInPlace(original);
  assertArrayEquals(new int[]{1, 2, 3, 4, 5}, original); // Incorrect test that passes
}

```
**Tests**

![Image](lab-3-1.png)

### Symptom of `reverseInPlace` Bug

When the `testReverseInPlaceFailure` test case is run, we expect it to reverse the array in place, but due to the bug, the original array does not properly update. This is because the loop in the method incorrectly assigns the elements, resulting in each element being swapped twice and ending up in its original position.

The symptom of the bug generates a failed assertion in the test case, indicating that the expected output (a reversed array) does not match the actual output (the original array).


![Image](lab-report-3-2.png)

### Symptom of `reversed` Method Bug

The `reversed` method is supposed to return a new array with the elements of the original array in reverse order. But, due to the bug, the returned array contains all zeros. This happens because the elements of the `newArray` are never actually assigned from `arr`. Instead, the method tries to modify the original `arr` which is not correct and does not change `newArray`.

The symptom is observed as a failing test case where the expected reversed array does not match the actual returned array, which consists of all zeros.

**Before Code Change:**
```java
for(int i = 0; i < arr.length; i += 1) {
  arr[i] = newArray[arr.length - i - 1];
}
```
- In the original reversed method, the assignment was incorrectly updating the input array arr instead of the new array newArray. This leeds to the unexpected change of arr and the newArray not updating.
  
**After Code Change:**  

```java
for(int i = 0; i < arr.length; i += 1) {
  newArray[i] = arr[arr.length - i - 1];
}
```
- In the corrected version we correctly populate newArray with elements from arr in reverse order and return the new reversed array.

  
# Part 2 - Researching Commands

## grep Command Usage

### grep -n "text" grep.txt

**Example 1:**

![Image](line-number-1.png)  


**Explanation:** Searches through 911 reports to find which line the word `Hello` appears on
- Useful for finding where specific words are within files. 

**Example 2:**

![Image](line-number-2.png)  


**Explanation:** Look for the word **"Abuse"** in .txt files in the `Media`  directory
- Useful when you're trying to find every occurrence of a word. Can help find all the files where abuse occurred. 

### Option -c (Count)

**Example 1:**

![Image](recursive+line.png)  


**Explanation:** Counts the number of times **"and"** appears in the `911report` directory 
- Useful to quantify the number of occurrences of the word

**Example 2:**

![Image](recursive+line2.png)  


**Explanation:** Returns the number of times the word **"emergency"** in the `chapter-1.txt` file inside of the 911report directory 

### Option -rn (Recursive number)

**Example 1:**

![Image](grep-count-1.png)  


**Explanation:** Recursively searches for the word **"algorithm"** in all files within the `./technical` directory
- Allows for searching through multiple files at once 

**Example 2:**

![Image](grep-count-2.png)  


**Explanation:** Searches for a more specific phrase **"algorithm analysis"** throughout all files in the `./technical` directory
- Useful for finding key phrases in a large collection of documents, perhaps for research purposes. 

### Option --color (Color match)

**Example 1:**

![Image](color-match-1.png)  


**Explanation:** Highlights the term "mortality" in the file `./468-6708-3-10.txt` from biomed directory
- Allows for highlighting specific words making it easier to spot

**Example 2:**

![Image](color-match-2.png)  


**Explanation:** Highlights "fine" in `Abuse_Penalties` making it easier to find the specific fines associated with crimes. 


### Works Cited: 

[FreeCodeCamp Grep](https://www.freecodecamp.org/news/grep-command-in-linux-usage-options-and-syntax-examples/)


