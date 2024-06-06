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
