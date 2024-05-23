### Lab Report 3 - Bugs and Commands (Week 5)

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
  
  ![Failure Inducing Test Output](https://github.com/Satvikmatta18/cse15l-lab-reports-/assets/106504471/d212c003-0a20-4982-8306-572ab6b05c72)
  
- **Non-Failure Inducing Test Output:**

  ![Non-Failure Inducing Test Output](https://github.com/Satvikmatta18/cse15l-lab-reports-/assets/106504471/4052a497-122e-4004-bf54-617bce843f6c)

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

The provided code change correctly fixes the `reverseInPlace` method. The original method was erroneously setting each element of the array to the second element's value (`arr[1]`), resulting in an incorrect array. The corrected method properly swaps elements from the beginning and end of the array, iterating only up to the middle of the array (`arr.length / 2`) to avoid reversing it back to the original order.

## Part 2 - Researching Commands

### The `grep` Command

#### Option 1: `-o` (Show only the part of a line matching PATTERN)

```bash
# Find instances of 'http' within files, showing only 'http'
grep -o 'http' ./technical/config.txt
```
**Output:**
```
http
http
http
```

```bash
# Extract 'error' from log files
grep -o 'error' ./technical/error_log.txt
```
**Output:**
```
error
error
error
```

#### Option 2: `--color` (Highlight matching strings)

```bash
# Highlight 'user' in configuration settings
grep --color 'user' ./technical/settings.ini
```
**Output:**
```
[Setting]
User=exampleuser
admin_user=true
```

```bash
# Color-highlight 'timeout' in script files for easy identification
grep --color 'timeout' ./technical/startup.sh
```
**Output:**
```
if [ $timeout -eq 0 ]; then
    echo "Timeout reached"
fi
```

#### Option 3: `-B` (Print NUM lines of leading context)

```bash
# Show two lines before each match for 'gateway'
grep -B 2 'gateway' ./technical/network_config.txt
```
**Output:**
```
ip_address=192.168.1.1
subnet_mask=255.255.255.0
gateway=192.168.1.254
```

```bash
# Display three lines before errors in logs
grep -B 3 'error' ./technical/server_logs.txt
```
**Output:**
```
Connection established
Data received
Data processed
error: connection timeout
```

#### Option 4: `-A` (Print NUM lines of trailing context)

```bash
# Show two lines following each match for 'init'
grep -A 2 'init' ./technical/init_script.sh
```
**Output:**
```
init system
starting services
loading configuration
```

```bash
# Display three lines after 'cleanup' tasks in scripts
grep -A 3 'cleanup' ./technical/cleanup_script.sh
```
**Output:**
```
cleanup temporary files
cleanup completed
Shutting down services
System halt
```

#### Sources

- Man pages on Linux (`man grep`)
- [GNU Grep Manual](https://www.gnu.org/software/grep/manual/grep.html)
