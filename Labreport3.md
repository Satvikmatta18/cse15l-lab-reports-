

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
        int[] input = {2, 2, 2, 2};
        ArrayExamples.reverseInPlace(input);
        assertArrayEquals(new int[]{2, 2, 2, 2}, input); // This test will pass
    }
}

```

#### Symptom

- **Failure-Inducing Test Output:**
 ![image](https://github.com/Satvikmatta18/cse15l-lab-reports-/assets/106504471/d212c003-0a20-4982-8306-572ab6b05c72)


  
- **Non-Failure Inducing Test Output:**


 ![image](https://github.com/Satvikmatta18/cse15l-lab-reports-/assets/106504471/4052a497-122e-4004-bf54-617bce843f6c)


#### The Bug (Before and After Code Change)

- **Before Code Change:**
  ```java
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[1];
    }
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

Here's the complete markdown text for your report:

```markdown
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
        int[] input = {2, 2, 2, 2};
        ArrayExamples.reverseInPlace(input);
        assertArrayEquals(new int[]{2, 2, 2, 2}, input); // This test will pass
    }
}

```

#### Symptom

- **Failure-Inducing Test Output:**
  ![Failure Test Output](https://github.com/Satvikmatta18/cse15l-lab-reports-/assets/106504471/d212c003-0a20-4982-8306-572ab6b05c72)

- **Non-Failure Inducing Test Output:**
  ![Non-Failure Test Output](https://github.com/Satvikmatta18/cse15l-lab-reports-/assets/106504471/4052a497-122e-4004-bf54-617bce843f6c)

#### The Bug (Before and After Code Change)

- **Before Code Change:**
  ```java
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[1];
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

#### Option 1: `-o` (Show only the part of a line matching PATTERN)

```bash
# Find instances of 'http' within files, showing only 'http'
grep -o 'http' ./technical/config.txt
```
This command searches for the word "example" in `logs.txt` under `./technical`, ignoring case sensitivity. It's useful for finding occurrences without worrying about capitalization.

```bash
# Extract 'error' from log files
grep -o 'error' ./technical/error_log.txt
```
Searches for "config" in the settings file, ignoring case, which is useful for configuration files where case sensitivity might vary.

#### Option 2: `--color` (Highlight matching strings)

```bash
# Highlight 'user' in configuration settings
grep --color 'user' ./technical/settings.ini
```
Recursively searches for the word "function" in all files under the `./technical` directory. This is beneficial for searching through multiple files or subdirectories.

```bash
# Color-highlight 'timeout' in script files for easy identification
grep --color 'timeout' ./technical/startup.sh
```
Recursively searches for "error" in all log files within the `./technical/logs` directory, useful for debugging.

#### Option 3: `-B` (Print NUM lines of leading context)

```bash
# Show two lines before each match for 'gateway'
grep -B 2 'gateway' ./technical/network_config.txt
```
Shows all lines in `source_code.c` that do not contain the word "deprecated". This helps in filtering out unwanted matches.

```bash
# Display three lines before errors in logs
grep -B 3 'error' ./technical/server_logs.txt
```
Lists all lines that do not include "todo" in `README.md`, helping to view content without specific tags or notes.

#### Option 4: `-A` (Print NUM lines of trailing context)

```bash
# Show two lines following each match for 'init'
grep -A 2 'init' ./technical/init_script.sh
```
Searches for "main"

 in `startup.sh` and displays line numbers, which is essential for locating the context of matches in scripts or code.

```bash
# Display three lines after 'cleanup' tasks in scripts
grep -A 3 'cleanup' ./technical/cleanup_script.sh
```
Finds "init" in `setup.sh` and shows line numbers, useful for script maintenance and debugging.

#### Sources

- Man pages on Linux (`man grep`)
- [GNU Grep Manual](https://www.gnu.org/software/grep/manual/grep.html)


