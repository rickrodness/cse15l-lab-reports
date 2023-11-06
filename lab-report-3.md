# Lab Report 3: Bugs and Commands

## Part 1 - Bugs

### Bug in `reverseInPlace` Method

#### Failure-Inducing Input

```java
@Test
public void testReverseInPlaceFailure() {
  int[] original = {1, 2, 3, 4, 5};
  ArrayExamples.reverseInPlace(original);
  assertArrayEquals(new int[]{5, 4, 3, 2, 1}, original); // This will fail with the original code.
}
```
### Non-Failure-Inducing Input
```java
@Test
public void testReverseInPlaceSuccess() {
  int[] original = {1, 2, 3, 4, 5};
  ArrayExamples.reverseInPlace(original);
  assertArrayEquals(new int[]{1, 2, 3, 4, 5}, original); // Incorrect test that would pass mistakenly.
}
```
**Symptom**

[!Image]()

**Before**
```java
for(int i = 0; i < arr.length; i += 1) {
  arr[i] = newArray[arr.length - i - 1];
}
```
**After**  

```java
for(int i = 0; i < arr.length; i += 1) {
  newArray[i] = arr[arr.length - i - 1];
}
