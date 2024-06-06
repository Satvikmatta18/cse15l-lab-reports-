# Lab Report 1

## `cd` Command Usage

### Command with No Arguments
![cd with no arguments](https://github.com/Satvikmatta18/cse15l-lab-reports-/assets/106504471/20fb4c5e-226b-4af6-a899-dd1954ea196a)
- **Command:** `cd`
- **Working Directory Before Command:** `/home`
- **Explanation:** Running `cd` with no arguments defaults to changing the current working directory to the user's home directory. In this case, since the user was already in `/home`, there is no visible change.
- **Error:** No error.

### Command with a Path to a Directory as an Argument
![cd to a directory](https://github.com/Satvikmatta18/cse15l-lab-reports-/assets/106504471/86f5510f-ab3f-426f-966d-b125bceb99b2)
- **Command:** `cd lecture1`
- **Working Directory Before Command:** `/home`
- **Explanation:** This command changes the current working directory to the directory `lecture1` within `/home`.
- **Error:** No error.

### Command with a Path to a File as an Argument
![cd to a file error](https://github.com/Satvikmatta18/cse15l-lab-reports-/assets/106504471/b801b828-b1a6-4c29-877c-a019c372178b)
- **Command:** `cd lecture1/messages/en-us.txt`
- **Working Directory Before Command:** `/home/lecture1`
- **Explanation:** This command attempts to change the directory to a file, which is not possible. The `cd` command is intended only for changing directories.
- **Error:** Yes, an error because `cd` cannot navigate to a file.

## `ls` Command Usage

### Command with No Arguments
![ls with no arguments](https://github.com/Satvikmatta18/cse15l-lab-reports-/assets/106504471/cd70f0f5-ca27-471b-b338-cdf5659d6b92)
- **Command:** `ls`
- **Working Directory Before Command:** `/home`
- **Explanation:** Lists all contents of the current working directory, which is `/home`.
- **Error:** No error.

### Command with a Path to a Directory as an Argument
![ls a directory](https://github.com/Satvikmatta18/cse15l-lab-reports-/assets/106504471/764ac6c6-4c3b-4a25-8340-6a412d15b86f)
- **Command:** `ls lecture1`
- **Working Directory Before Command:** `/home`
- **Explanation:** Lists all contents within the specified directory `lecture1`.
- **Error:** No error.

### Command with a Path to a File as an Argument
![ls a file](https://github.com/Satvikmatta18/cse15l-lab-reports-/assets/106504471/e98bfba1-0902-4a2e-ae0b-4b52d683336c)
- **Command:** `ls messages/en-us.txt`
- **Working Directory Before Command:** `/home/lecture1/messages`
- **Explanation:** Lists the specified file `en-us.txt` showing its details within its directory.
- **Error:** No error.

## `cat` Command Usage

### Command with No Arguments
![cat with no arguments](https://github.com/Satvikmatta18/cse15l-lab-reports-/assets/106504471/f0f573fb-84e5-44b2-9710-d462f62ab3fc)
- **Command:** `cat`
- **Working Directory Before Command:** `/home`
- **Explanation:** The `cat` command without arguments waits for input from the terminal, expecting to concatenate from stdin.
- **Error:** No error, but requires user input to proceed.

### Command with a Path to a Directory as an Argument
![cat a directory error](https://github.com/Satvikmatta18/cse15l-lab-reports-/assets/106504471/392831b8-6ee6-4057-a973-3301a9a4cacd)
- **Command:** `cat Lecture1`
- **Working Directory Before Command:** `/home`
- **Explanation:** Attempting to use `cat` on a directory results in an error because `cat` is designed to read files, not directories.
- **Error:** Yes, an error because directories cannot be displayed using `cat`.

### Command with a Path to a File as an Argument
![cat a file](https://github.com/Satvikmatta18/cse15l-lab-reports-/assets/106504471/b35c5abc-e2d8-49ec-85ec-90f7521a629d)
- **Command:** `cat messages/en-us.txt`
- **Working Directory Before Command:** `/home`
- **Explanation:** This command displays the contents of the file `en-us.txt`. "Hello World!" is displayed, verifying that the file contains readable text.
- **Error:** No error.




# LAB REPORT 5 

---

# Input-Induced Division Dilemma

Hey, 

I've been working on a simple Java program that takes two numbers from the user and calculates their quotient. However, something weird is going on. Check out this screenshot:

Here's the relevant part of my code:

```java
import java.util.Scanner;

public class QuotientCalculator {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter the numerator: ");
        int numerator = scanner.nextInt();

        System.out.print("Enter the denominator: ");
        int denominator = scanner.nextInt();

        int result = calculateQuotient(numerator, denominator);
        System.out.println("The quotient is: " + result);
    }

    private static int calculateQuotient(int numerator, int denominator) {
        return numerator / denominator;
    }
}
```

Any ideas on what might be causing this division dilemma?

---

## TA's Response

Hey Satvik,

It looks like you might be facing a classic issue with division by zero. Users might be entering a zero as the denominator, causing the program to throw an `ArithmeticException`. Let's add some validation to handle this scenario. Try modifying your `calculateQuotient` method like this:

```java
private static int calculateQuotient(int numerator, int denominator) {
    if (denominator == 0) {
        System.out.println("Error: Cannot divide by zero!");
        return -1; // Or handle it appropriately
    }
    return numerator / denominator;
}
```

Give it a shot, and let's see if we can fix this arithmetic anomaly!

---

## Terminal Output after Modification

```
Enter the numerator: 10
Enter the denominator: 0
Error: Cannot divide by zero!
The quotient is: -1
```

---

## Bug Description

The issue arises when the user enters zero as the denominator, leading to a division by zero exception. The modification includes a validation check to handle this scenario and provides an appropriate error message.

---

## Setup Information

### File & Directory Structure

```
- project_directory
  - QuotientCalculator.java
```

### Contents of QuotientCalculator.java

```java
import java.util.Scanner;

public class QuotientCalculator {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter the numerator: ");
        int numerator = scanner.nextInt();

        System.out.print("Enter the denominator: ");
        int denominator = scanner.nextInt();

        int result = calculateQuotient(numerator, denominator);
        System.out.println("The quotient is: " + result);
    }

    private static int calculateQuotient(int numerator, int denominator) {
        if (denominator == 0) {
            System.out.println("Error: Cannot divide by zero!");
            return -1; // Or handle it appropriately
        }
        return numerator / denominator;
    }
}
```

### Full Command Line to Trigger the Bug

```bash
javac QuotientCalculator.java
java QuotientCalculator
```

### Description of What to Edit to Fix the Bug

Ensure that the `denominator` entered by the user is always non-zero to avoid division by zero errors.

---

## Reflection

In the second half of this quarter, I learned a lot about handling exceptions and input validation in Java, which is crucial for writing robust programs. Additionally, I gained a better understanding of debugging techniques and how to simulate real-world scenarios to identify and fix bugs efficiently.

A Note on Grading at the End of the Quarter
There will not be a resubmission window for Lab Report 5, so do your best to be thorough, creative, and clear in your submission and make sure to submit by the deadline.



