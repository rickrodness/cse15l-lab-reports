# Lab Report: Debugging Scenario

## Part 1 - Debugging Scenario on EdStem

### Original Post by Student

**Title:** Unexpected Output in ListExamples.merge Method

**Body:**
Hi all,

I'm encountering an odd issue with the `merge` method in our `ListExamples` Java class. When I run our JUnit tests, one of the tests (`testMerge2`) fails, but `testMerge1` passes. The issue seems to be with merging lists where both have multiple elements. Here's a screenshot showing the terminal output:

![Terminal Output: Failing JUnit Test for ListExamples.merge Method](path/to/screenshot1.png)

My guess is that there's a problem in the loop that merges the elements, possibly with the index handling. Has anyone faced something similar? Any help would be appreciated!

---

### Response from TA

**Body:**
Hi,

It looks like an indexing issue in the merge loop. Can you insert a print statement in the `merge` method to print the contents of `result` at each step of the loop and share the output? This could give us more insight into how the elements are being merged.

---

### Follow-up Post by Student

**Body:**
Thanks for the suggestion! After adding the print statement, I noticed that elements from the second list were not being added correctly. Here's the updated terminal output with the print statements:

![Terminal Output: Debugging Output for ListExamples.merge Method](path/to/screenshot2.png)

The problem seems to be that the index for the second list isn't being incremented correctly in the loop. I was incrementing `index1` instead of `index2`.

---

## Debugging Scenario Setup Information

### File & Directory Structure

- `ListExamples.java` (Java class with `merge` method)
- `ListExamplesTests.java` (JUnit test class for `ListExamples`)
- `test.sh` (Bash script to compile and run JUnit tests)
- `lib/` (Directory containing JUnit and Hamcrest JAR files)

### Contents of Each File Before Fixing the Bug

- **ListExamples.java:**
  ```java
  public class ListExamples {
    // ... other methods ...

    static List<String> merge(List<String> list1, List<String> list2) {
      // ... code ...
      while(index2 < list2.size()) {
        result.add(list2.get(index2));
        index1 += 1;  // Bug: Should be index2
      }
      // ... code ...
    }
  }
  ```
- **ListExamplesTests.java:** (Your provided test cases)
- **test.sh:** (Your provided bash script)

### Command Line to Trigger the Bug

```bash
bash test.sh
```

### Fixing the Bug

- In `ListExamples.java`, change `index1 += 1;` to `index2 += 1;` in the `merge` method to correctly increment the index of the second list.
