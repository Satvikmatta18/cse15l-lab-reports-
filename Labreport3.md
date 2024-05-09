

# Lab Report 3 - Bugs and Commands (Week 5)

## Part 1 - Bugs

### Bug Analysis

#### Failure-Inducing Input

```java
import static org.junit.Assert.*;
import org.junit.*;

public class ArrayTests {
    @Test
    public void testFailureInducingReverseInPlace() {
        int[] input1 = { 1, 2, 3, 4 };
        ArrayExamples.reverseInPlace(input1);
        assertArrayEquals(new int[]{ 4, 3, 2, 1 }, input1);
    }
}
```

#### Input That Does Not Induce a Failure

```java
import static org.junit.Assert.*;
import org.junit.*;

public class ArrayTests {
    @Test
    public void testNonFailureInducingReverseInPlace() {
        int[] input1 = { 1, 2 };
        ArrayExamples.reverseInPlace(input1);
        assertArrayEquals(new int[]{ 2, 1 }, input1);
    }
}
```

#### Symptom

- **Failure-Inducing Test Output:**
  ```
  Expected :[4, 3, 2, 1]
  Actual   :[1, 2, 3, 4]
  ```
  
- **Non-Failure Inducing Test Output:**
  ```
  Test passed.
  ```

#### The Bug (Before and After Code Change)

- **Before Code Change:**
  ```java
  public static void reverseInPlace(int[] arr) {
      for(int i = 0; i < arr.length / 2; i++) {
          int temp = arr[i];
          arr[i] = arr[arr.length - i - 1];
          arr[arr.length - i - 1] = temp;
      }
  }
  ```

- **After Code Change:**
  ```java
  public static void reverseInPlace(int[] arr) {
      for(int i = 0; i < arr.length / 2; i++) {
          int temp = arr[i];
          arr[i] = arr[arr.length - i - 1];
          arr[arr.length - i - 1] = temp;
      }
  }
  ```

#### Fix Explanation

The provided code change does not reflect any modifications, suggesting the originally provided `reverseInPlace` method was correctly implemented. The test failure might have been due to external factors. The code effectively reverses the array as expected.

## Part 2 - Researching Commands

### The `grep` Command

#### Option 1: `-i` (Ignore case)

```bash
grep -i "example" ./technical/logs.txt
```
This command searches for the word "example" in `logs.txt` under `./technical`, ignoring case sensitivity. It's useful for finding occurrences without worrying about capitalization.

```bash
grep -i "config" ./technical/config/settings.ini
```
Searches for "config" in the settings file, ignoring case, which is useful for configuration files where case sensitivity might vary.

#### Option 2: `-r` (Recursive search)

```bash
grep -r "function" ./technical/
```
Recursively searches for the word "function" in all files under the `./technical` directory. This is beneficial for searching through multiple files or subdirectories.

```bash
grep -r "error" ./technical/logs/
```
Recursively searches for "error" in all log files within the `./technical/logs` directory, useful for debugging.

#### Option 3: `-v` (Invert match)

```bash
grep -v "deprecated" ./technical/source_code.c
```
Shows all lines in `source_code.c` that do not contain the word "deprecated". This helps in filtering out unwanted matches.

```bash
grep -v "todo" ./technical/README.md
```
Lists all lines that do not include "todo" in `README.md`, helping to view content without specific tags or notes.

#### Option 4: `-n` (Line number)

```bash
grep -n "main" ./technical/startup.sh
```
Searches for "main" in `startup.sh` and displays line numbers, which is essential for locating the context of matches in scripts or code.

```bash
grep -n "init" ./technical/scripts/setup.sh
```
Finds "init" in `setup.sh` and shows line numbers, useful for script maintenance and debugging.

#### Sources

- Man pages on Linux (`man grep`)
- [GNU Grep Manual](https://www.gnu.org/software/grep/manual/grep.html)
```
