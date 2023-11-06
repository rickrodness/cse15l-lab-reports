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

When the `testReverseInPlaceFailure` test case is run, it is expected to reverse the array in place, but due to the bug, the original array remains unchanged after the method call. This is because the loop in the method incorrectly assigns the elements, resulting in each element being swapped twice and ending up in its original position.

The symptom of the bug manifests as a failed assertion in the JUnit test case, indicating that the expected output (a reversed array) does not match the actual output (the original, unchanged array).


![Image](lab-report-3-2.png)

### Symptom of `reversed` Method Bug

The `reversed` method is supposed to return a new array with the elements of the original array in reverse order. However, due to the bug, the returned array contains all zeros. This happens because the elements of the `newArray` are never actually assigned from `arr`. Instead, the method erroneously attempts to modify the original `arr` which is not only incorrect but also does not change `newArray`.

The symptom is observed as a failing test case where the expected reversed array does not match the actual returned array, which consists of all zeros.

**Before Code Change:**
```java
for(int i = 0; i < arr.length; i += 1) {
  arr[i] = newArray[arr.length - i - 1];
}
```
- In the original reversed method, the assignment was incorrectly updating the input array arr instead of the new array newArray. This led to the unexpected change of arr and the newArray not updating.
  
**After Code Change:**  

```java
for(int i = 0; i < arr.length; i += 1) {
  newArray[i] = arr[arr.length - i - 1];
}
```
- In the corrected version we correctly populate newArray with elements from arr in reverse order and return the new reversed array.

  
# Part 2 - Researching Commands

## grep Command Usage

### Option -i (Ignore case)

**Example 1:**

```bash
grep -i "dog" ./quotes/dog_quotes.txt
```

**Explanation:** Searches for the string "dog" in `dog_quotes.txt` ignoring case sensitivity. Useful for finding matches regardless of how the text is capitalized.

**Example 2:**

```bash
grep -i "loyal" ./quotes/canine_admiration.txt
```

**Explanation:** Looks for the word "loyal" in `canine_admiration.txt`, case-insensitively. This helps when you're unsure of the text's capitalization.

### Option -c (Count)

**Example 1:**

```bash
grep -c "friend" ./quotes/dog_friendship.txt
```

**Explanation:** Counts the number of times "friend" appears in `dog_friendship.txt`. It quantifies the mention of friendship related to dogs.

**Example 2:**

```bash
grep -c "companion" ./quotes/dog_companionship.txt
```

**Explanation:** Gives the count of the word "companion" in `dog_companionship.txt`. Useful for understanding the frequency of certain words.

### Option -r (Recursive)

**Example 1:**

```bash
grep -r "puppy" ./quotes/
```

**Explanation:** Recursively searches for "puppy" in all files within the `./quotes` directory. It allows searching through multiple files at once.

**Example 2:**

```bash
grep -r "best friend" ./quotes/
```

**Explanation:** Searches for the phrase "best friend" throughout all files in the `./quotes` directory recursively. It's useful for finding phrases in a large collection of documents.

### Option --color (Color match)

**Example 1:**

```bash
grep --color "happy" ./quotes/dog_happiness.txt
```

**Explanation:** Highlights the term "happy" in the output from `dog_happiness.txt`, making it easier to spot.

**Example 2:**

```bash
grep --color "playful" ./quotes/puppy_playtime.txt
```

**Explanation:** Highlights "playful" in `puppy_playtime.txt`, useful for quickly locating the word in the text output.


