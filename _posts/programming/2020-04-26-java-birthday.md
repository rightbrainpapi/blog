---
title: Java Birthday Program
author: Darnell Simon
date: 2020-04-26 12:30:00 -0400
categories: [Programming, Java]
tags: [java]
---

<div style="width:100%;display:flex; justfy-content:center" ><img style="width:20rem;"
src="https://cdn.glitch.com/b75055dd-03c2-47e5-9f5d-7923ac439cc1%2Fbirthday.jpg?v=1587923774470"/></div>

Today we will be working on a brief Java program that takes a person's input of the current month and year, and their date of birth to determine the person's age.<br><br>

---

There are a variety of ways to solve this challenge but we will look at one approach.
Let's use do a little backward design figure this out.<br>

## Our Goal: Print the persons age.

- First we'll need to:
  - Ask the person for the current date
  - Ask the person for their date of birth
- Second we'll need to:
  - Store the person's response to each question in variables
  - Subtract the date of birth from the current date
- Finally we'll need to:
  - Return our caluclation to the user
  - Start the process over again.

---

## Task 1 - Ask User for Info

- We will need to create a two prompt user statements

  - Example:
    ```java
    public static void promptUser(){
        System.out.println("Please do as I ask.");
        System.out.println("Enter four zeros to stop.");
    }
    ```

## Solution 1.1 - Ask User for Info

---

```java
package birthdays;

public class Birthdays {

    public static void main(String[] args) {
        getCurrentDate();
        promptUser();
    }

    public static void getCurrentDate (){
        System.out.println("Enter the current month followed by the current year."); // asks for current date
        currentMonth = sc.nextDouble(); // receives the current month and stores in var
        currentYear = sc.nextDouble();  // receives the current year and stores in var
    }

    public static void promptUser(){
        System.out.println("Please enter your birth month, birth year as well as"); // asks for birth date
        System.out.println("Enter four zeros to stop."); // indicator to break out of program
    }


}
```

Now that we've created two methods to asked the user for the current date and their date of birth we need a way to save the users input.
Lets add a package call Scanner and a few variables.

## Solution 1.2 - Store Input to Variable

---

```java
package birthdays;

import java.util.Scanner; // allows us to scan in the users input

public class Birthdays {
  static Scanner sc = new Scanner(System.in); // initializing a new scanner called sc
  static double currentMonth, currentYear; // declare two doubles

  public static void main(String[] args) {
	double birthMonth,birthYear,age; // adding variables to the main method
	getCurrentDate();
	promptUser();
	birthMonth = sc.nextDouble();
	birthYear = sc.nextDouble();
  }

  public static void getCurrentDate (){
	System.out.println("Enter the current month followed by the current year.");
	currentMonth = sc.nextDouble(); // sc receives the current month and is stored in var
	currentYear = sc.nextDouble();  // sc receives the current year and is stored in var
  }

  public static void promptUser(){
	System.out.println("Please enter your birth month, birth year as well as");
	System.out.println("Enter four zeros to stop."); // indicator to break out of program
  }
}
```

As you may notice we do several things here.

- First we:
  - import java.util.Scanner
  - initialize a new scanner called sc within the Birthday class.
  - declare two doubles currentMonth and Current Year within the Birthday class.
- Secon we:
  - while in the main method we set
    - `currentMonth = sc.nextDouble();` & `currentYear = sc.nextDouble();`
- Finally we:
  - Go down to the getCurrentDate method to set currentMonth = sc.nextDouble(); & currentYear = sc.nextDouble();

Our next and final tax is using that information to calculate the age.

## Solution 1.3 - Completing Birthday Caluclation

---

```java
package birthdays;

import java.util.Scanner;

public class Birthdays {
  static Scanner sc = new Scanner(System.in);
  static double currentMonth, currentYear;


  public static void main(String[] args) {
	double birthMonth,birthYear,age;
	getCurrentDate();
	promptUser();

	birthMonth = sc.nextDouble();
	birthYear = sc.nextDouble();

	// equation to determine age saved to age variable
	age = currentYear - birthYear + (currentMonth - birthMonth)/12;

	System.out.printf("For %.0f and %.0f your age is %.1f%n%n", birthMonth, birthYear, age);
  }

  public static void getCurrentDate (){
	System.out.println("Enter the current month followed by the current year.");
	currentMonth = sc.nextDouble();
	currentYear = sc.nextDouble();
  }

  public static void promptUser(){
	System.out.println("Please enter your birth month, birth year as well as");
	System.out.println("Enter four zeros to stop.");
  }
}
```

In the recently completed section you see we've added the equation which determines the a person birthday.
Running the code above should allow us to calculate at least 1 age. However what if we wanted to continuously calculate a variety of ages?<br><br>Well, we'd need a loop and a way to break out of that loop. Let's do that now.

## Solution 1.4 - Create a Loop

---

```java
package birthdays;

import java.util.Scanner;

public class Birthdays {
	static Scanner sc = new Scanner(System.in);
    static double currentMonth, currentYear;


  public static void main(String[] args) {
	double birthMonth,birthYear,age;
	getCurrentDate();
	promptUser();

	birthMonth = sc.nextDouble();

	// Create a while loop
	while(birthMonth > 0){
	  // MOVED: birth year input
	  birthYear = sc.nextDouble();
      // MOVED: equation to determine age saved to age variable
	  age = currentYear - birthYear + (currentMonth - birthMonth)/12;

	  System.out.printf("For %.0f and %.0f your age is %.1f%n%n", birthMonth, birthYear, age);

	  promptUser();
	  birthMonth = sc.nextDouble(); // scan to see if 0000 has been enter
	}
  }

  public static void getCurrentDate (){
	System.out.println("Enter the current month followed by the current year.");
	currentMonth = sc.nextDouble();
	currentYear = sc.nextDouble();
  }

  public static void promptUser(){
	System.out.println("Please enter your birth month, birth year as well as");
	System.out.println("Enter four zeros to stop.");
  }
}
```

In this final segment simply created a while loop with the condition to run so long as a birth month has been entered.<br>If 0000 has been entered then we will break out of the program.<br><br>

Great, so we are finished. Running the above program should produce the following results for the following current date and birthday 04 2020 & 05 1990

```console
run:
Enter the current month followed by the current year.
04 2020
Please enter your birth month, birth year as well as
Enter four zeros to stop.
05 1990
For 5 and 1990 your age is 29.9

Please enter your birth month, birth year as well as
Enter four zeros to stop.
```

This concludes the 4 tasks. To see the GitHub Gist click [here](https://gist.github.com/rightbrainpapi/4745d9812895e00ebecb3cdb4e382fe7.js)

[^footnote]: The footnote source.
