# Lab Report 3: Bugs and Commands

## Part 1 - Bugs

### Bug in `reversed` Method from Lab 4

#### Failure-Inducing Input:

```java
@Test
public void testReversedFailure() {
    int[] original = {1, 2, 3, 4, 5};
    int[] result = ArrayExamples.reversed(original);
    assertArrayEquals(new int[]{5, 4, 3, 2, 1}, result); // This will fail with the buggy code.
}

@Test
public void testReversedNonFailure() {
    int[] original = {};
    int[] result = ArrayExamples.reversed(original);
    assertArrayEquals(new int[]{}, result); // This should pass even with the buggy code.
}
``` 

**Explanation:**
- The failure-inducing input tests whether the reversed method can correctly reverse a populated array. The buggy implementation fails this test by incorrectly reversing the elements.

- The non-failure-inducing test checks the behavior of the reversed method with an empty array. Since reversing an empty array should yield an empty array, this test would pass even with the buggy implementation of the reversed method.

**Symptom of reversed Method Bug:**
- When the testReversedFailure test case is run, we expect it to reverse the array, but due to the bug, the returned array has all elements set to zero. This is because the loop in the method incorrectly assigns values from an uninitialized newArray, resulting in a zero-filled array.

- The symptom of the bug manifests as a failed assertion in the JUnit test case, indicating that the expected output (a reversed array) does not match the actual output (an array filled with zeros).

**Before Code Change:**
```java
static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
        arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
}
```
- In the original reversed method, the assignment mistakenly updates the input array arr instead of the new array newArray, leading to unexpected alteration of arr and newArray not being correctly populated.

**After Code Change:** 
```java
static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
        newArray[i] = arr[arr.length - i - 1];
    }
    return newArray;
}
```

- In the corrected version, newArray is properly populated with elements from arr in reverse order, and this new reversed array is what is returned from the method.








--- 
  
## Part 2 - Researching Commands
### Grep Command Usage:

## grep -n 
- This command prints out the matches for the text along with the line numbers. 

## **Example 1:**

**Input:** `grep -n "Hello" ./technical/911report/*.txt`
**Output**: 
```
./technical/911report/chapter-1.txt:682:    At 10:39, the Vice President updated the Secretary on the air threat conference: Vice President:
There's been at least three instances here where we've had reports of aircraft  
approaching Washington-a couple were confirmed hijack. And, pursuant to the President's  
instructions I gave authorization for them to be taken out. Hello?
```

**Explanation:** Searches through 911 reports to find where the word appears and on which line **"Hello"** is located. Which is useful for finding where specific words are within files.

--- 
## **Example 2:** 

**Input:** `grep -n "Abuse" ./technical/government/Media/*.txt`
**Output**:
```./technical/government/Media/Abuse_penalties.txt:5: Abuse penalties questioned
./technical/government/Media/Abuse_penalties.txt:14: In 2001, county judges heard 98 Protection From Abuse cases,
./technical/government/Media/Abuse_penalties.txt:29: Are we sending those who repeatedly violate Protection From Abuse
./technical/government/Media/Domestic_Violence_Ruling.txt:68: Abuse and Domestic Violence, said she disagreed with Judge
./technical/government/Media/Targeting_Domestic_Violence.txt:56: Groups to apply for the grant: Help for Abused Women and their
./technical/government/Media/Targeting_Domestic_Violence.txt:72: Candace Waldron, executive director of Help for Abused Women and
```


**Explanation:** Look for the word **"Abuse"** in .txt files in the `Media`  directory
- Useful when you're trying to find every occurrence of a word. Can help find all the files where abuse occurred. 
--- 

## Option -rn (Recursive number)
- The **`-r`** option tells grep to search recursively, meaning it will look into every file within the /technical directory and all of its subdirectories.
- adding the **`-n`** includes the line numbers for the results

## **Example 1:**

**Input:** ` grep -rn "algorithms" technical/`
**Output**:
```
technical/911report/chapter-12.txt:1030:                called algorithms, are just beginning to be used. Travel history, however, is still
technical/biomed/1471-2105-2-8.txt:11:        general genefinding algorithms. The number and diversity of
technical/biomed/1471-2105-2-8.txt:709:            The full description of the algorithms associated to
technical/biomed/1471-2105-2-8.txt:711:            algorithms requires two kind of emission
technical/biomed/1471-2105-2-8.txt:771:          Alignment and scoring algorithms
technical/biomed/1471-2105-2-8.txt:778:          Viterbi and/or Forward algorithms and SCFG CYK and/or
technical/biomed/1471-2105-2-8.txt:779:          Inside algorithms. The OTH and COD pair-HMM alignment
technical/biomed/1471-2105-2-8.txt:786:          standard algorithms. Consider the RNA model. Recall that
technical/biomed/1471-2105-2-8.txt:803:          To combine the desired features of the two algorithms,
technical/biomed/1471-2105-2-8.txt:858:          Stormo/Haussler parsing algorithms add one order of
... 
...
...
technical/plos/journal.pbio.0020439.txt:184:        biological landscape. Algorithms are procedures for manipulating symbols. Some algorithms
technical/plos/journal.pbio.0020439.txt:196:        structures, algorithms, theories or models, and means of computation (typically software
technical/plos/journal.pbio.0020439.txt:199:        cancer cells) with algorithms for correlation and hierarchical clustering.
technical/plos/journal.pbio.0020439.txt:207:          Lee 1903) in a study of human inheritance—and clustering algorithms, which apparently h
```

**Explanation:** Recursively searches for the word **"algorithms"** in all files within the `./technical` directory
- Allows for searching through multiple files at once / directories. I liked this one because I was able to search the entire technical/ directory.  

**Example 2:**

**Input:** ` grep -rn "algorithm analysis" technical/`
**Output**:
```
technical/biomed/1476-4598-2-25.txt:581:        sequencing, and BLAST algorithm analysis. JOH performed
```

**Explanation:** Searches for a more specific phrase **"algorithm analysis"** throughout all files in the `./technical` directory
- Useful for finding key phrases in a large collection of documents, perhaps for research purposes. 

---

### Option -c (Count)

- Prints the number of lines that contain at least one mathc for the patten. 

**Example 1:**

**Input:** ` grep -c "and" ./technical/911report/*.txt`
**Output:**
```
./technical/911report/chapter-1.txt:243
./technical/911report/chapter-10.txt:163
./technical/911report/chapter-11.txt:211
./technical/911report/chapter-12.txt:553
./technical/911report/chapter-13.1.txt:377
./technical/911report/chapter-13.2.txt:295
./technical/911report/chapter-13.3.txt:351
./technical/911report/chapter-13.4.txt:650
./technical/911report/chapter-13.5.txt:762
./technical/911report/chapter-2.txt:289
./technical/911report/chapter-3.txt:926
./technical/911report/chapter-5.txt:383
./technical/911report/chapter-6.txt:484
./technical/911report/chapter-7.txt:471
./technical/911report/chapter-8.txt:225
./technical/911report/chapter-9.txt:569
./technical/911report/preface.txt:54
```


**Explanation:** Counts the number of lines **"and"** appears at least once in the files within the `911report` directory. 
- Useful to see how many lines contain certain words. 


**Example 2:**

**Input:** ` grep -c "emergency" ./technical/911report/chapter-1.txt`
**Output:**
```
6
```


**Explanation:** Returns the number of line the word **"emergency"** appears in the `chapter-1.txt` file. So emergency is on at least 6 of the lines within `chapter-1.txt`

--- 

### Option --color (Color match)

- The `--color` option with `grep` is used to enhance the readability of certain words within a text file by highlighting the matching text. When the pattern is found the word will be highlighted red within the terminal. 

##**Example 1:**

**Input:** `grep --color "mortality" ./technical/biomed/1468-6708-3-10.txt`
**Output:**
```
        "usual care" reduces all-cause *mortality* in a subset of
          all-cause *mortality*, combined CHD (including CHD death,
          As previously reported, all-cause *mortality* did not
        Treatment group differences in *mortality* attributed to
        doxazosin group translates into a higher overall *mortality*
        difference in total *mortality* without any competing causes
```


**Explanation:** Highlights the term **"mortality"** in the file `./468-6708-3-10.txt` from biomed directory
- Allows for highlighting specific words making it easier to spot

## **Example 2:**


**Input:** `grep --color "fine" ./technical/government/Media/*.txt`
**Output:**
```
./technical/government/Media/Abuse_penalties.txt:$100 *fine*.
./technical/government/Media/Abuse_penalties.txt:fine.
./technical/government/Media/Abuse_penalties.txt:costs, plus a $100 fine. No defendants were ordered to pay more
./technical/government/Media/Abuse_penalties.txt:than a $250 fine for violating the court order. In 27 percent of
./technical/government/Media/Abuse_penalties.txt:the fine for violating a PFA is little more than the fine someone
./technical/government/Media/Abuse_penalties.txt:Under state law, the minimum fine for contempt of a PFA is $100;
./technical/government/Media/Abuse_penalties.txt:the maximum fine is $1,000 and up to six months in jail.
./technical/government/Media/Attorney_gives_his_time.txt:"He's such a fine, fine person," said executive director Kris
./technical/government/Media/Eviction_law.txt:Eviction law is fine with local tenant
./technical/government/Media/Law_Schools.txt:schools coined to define the atypical kind of law career they are
./technical/government/Media/Pro-bono_road_show.txt:residents outside of the courthouse's confines.
./technical/government/Media/The_State_of_Pro_Bono.txt:changing the oppressive conditions of confinement in Philadelphia's
./technical/government/Media/Volunteers_Step_Up.txt:that defines our democracy and protects our freedoms.
```

**Explanation:** Highlights **"fine"** in `Abuse_Penalties` making it easier to find the specific fines associated with crimes. 


### Works Cited: 

[FreeCodeCamp Grep](https://www.freecodecamp.org/news/grep-command-in-linux-usage-options-and-syntax-examples/)



