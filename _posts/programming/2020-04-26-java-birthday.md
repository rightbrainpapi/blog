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
- Second we:
  - Go down to the getCurrentDate method to set currentMonth = sc.nextDouble(); & currentYear = sc.nextDouble();

Our next and final tax is using that information to calculate the age.

<!-- ---

## Task 2 - `takeDamage()` Method

- Implement a `takeDamage()` method for the `Pokemon` class which takes a number as an argument and reduces the `.health` of the `Pokemon` by that number.

  - _Note: If `.health` goes below 0, it should be set to 0 instead._
  - Example:
    ```javascript
    console.log(charmander.health); // 30
    charmander.takeDamage(5);
    console.log(charmander.health); // 25
    charmander.takeDamage(2000);
    console.log(charmander.health); // 0
    ```

 <br>

## Solution 1.2 - Take Damage

---

```javascript
function Pokemon(name, attack, defense, health, type) {
	//do something here
	this.name = name;
	this.attack = attack;
	this.defense = defense;
	this.health = health;
	this.type = type;
	this.initHealth = health;
	this.takeDamage = function (number) {
		// Check if health is less than number.
		if (this.health < number) {
			// if less than return health as 0.
			return (this.health = 0);
		} else {
			// if not return the precise difference
			return (this.health = this.health - number);
		}
	};
}

// Squirtle taking damage
var squirtle = new Pokemon("Squirtle", 110, 100, 120, "water");
squirtle.takeDamage(20);
squirtle.takeDamage(100000);
```

## Task 3 - `attackOpponent()` Method

- Implement an `attackOpponent()` method for the `Pokemon` class which takes a `Pokemon` object as an argument (the opponent being attacked). This method should call the `takeDamage()` method of the opposing `Pokemon` and provide the appropriate damage as an argument.
  <br>

`DAMAGE = CURRENT_POKEMON_ATTACK - OPPONENT_POKEMON_DEFENSE`.

- Example:

  ```javascript
  const charmander = new Pokemon("charmander", 12, 8, 30, "fire");
  const bulbasaur = new Pokemon("bulbasaur", 7, 9, 35, "grass/poison");
  console.log(charmander.attack); // 12
  console.log(bulbasaur.defense); // 9
  // 12 attack - 9 defense = 3 damage
  console.log(bulbasaur.health); // 35
  charmander.attackOpponent(bulbasaur); // charmander attacks bulbasaur
  console.log(bulbasaur.health); // 32
  ```

- Attacking a `Pokemon` should do 1 damage **at the very least**. Consider cases in which the `Pokemon` being attacked has a higher `.defense` than the `.attack` of the attacking `Pokemon`.
  <br>

## Solution 1.3 - Attack Opponent

---

```javascript
function Pokemon(name, attack, defense, health, type) {
	//do something here
	this.name = name;
	this.attack = attack;
	this.defense = defense;
	this.health = health;
	this.type = type;
	this.initHealth = health;
	this.takeDamage = function (number) {
		if (this.health < number) {
			return (this.health = 0);
		} else {
			return (this.health = this.health - number);
		}
	};
	this.attackOpponent = function (opponent) {
		//   This should:
		//     [x]  Grab the opponents defense
		//     [x]  Subtract it from the attacker's attack to get the difference (this is the damage points)
		//     [x]  Call the opponent.takeDamage with the damage points as an arguement.
		//     [x]  Return the opponents health
		//     [x]  Account for cases where defense is greater than the attack
		var damage;
		if (this.attack > opponent.defense) {
			// Determined the damaged points by the opponents' defense from the attackers attack save it in a variable
			damage = this.attack - opponent.defense; // call the opponents takeDamage with the newly determined damage points as an arguement
			opponent.takeDamage(damage);
			return opponent.health;
		} else {
			return (opponent.health = opponent.health - 1);
		}
	};
}

// Charmander attacks squirtle.
charmander = new Pokemon("Charmander", 100, 110, 130, "fire");
squirtle = new Pokemon("Squirtle", 110, 100, 100, "water");
charmander.attackOpponent(squirtle);
```

## Task 4 - `display()` Method

- Implement a `display()` method for the `Pokemon` class which takes no arguments and returns a string with the Pokemon's `.name` in all caps, `.type` in all caps and in parenthesis, and `.health` with a forward-slash, " / ", followed by the `.health` the `Pokemon` was initialized with.

  - Example:

    ```javascript
    const pikachu = new Pokemon("pikachu", 9, 10, 25, "electric");
    pikachu.display(); // PIKACHU (ELECTRIC) 25/25

    pikachu.health = 12;
    pikachu.display(); // PIKACHU (ELECTRIC) 12/25
    ```

    <br>

## Solution 1.4 - Display Pokemon

---

```javascript
function Pokemon(name, attack, defense, health, type) {
	//do something here
	this.name = name;
	this.attack = attack;
	this.defense = defense;
	this.health = health;
	this.type = type;
	this.initHealth = health;
	this.takeDamage = function (number) {
		if (this.health < number) {
			return (this.health = 0);
		} else {
			return (this.health = this.health - number);
		}
	};
	this.attackOpponent = function (opponent) {
		var damage;
		if (this.attack > opponent.defense) {
			damage = this.attack - opponent.defense;
			opponent.takeDamage(damage);
			return opponent.health;
		} else {
			return (opponent.health = opponent.health - 1);
		}
	};
	this.display = function () {
		//   This should return a tring with the:
		//      [x]`.name` in all caps
		//      [x]`.type` in all caps and parenthesis
		//      [x]`.health` with a forward-slash "/"
		//      [x] followed by the `.health` the `Pokemon` was initialized with
		nameUp = this.name.toUpperCase();
		typeUp = this.type.toUpperCase();
		currentHealth = this.health;
		initHealth = this.initHealth;
		return `${nameUp} (${typeUp}) ${currentHealth}/${initHealth}`;
	};
}

// Displays a Pokemon named Bulbasaur
const bulbasaur = new Pokemon("bulbasaur", 7, 9, 35, "grass/poison");
bulbasaur.display();
``` -->

This concludes the 4 tasks. To see the GitHub Gist click [here](https://gist.github.com/rightbrainpapi/4745d9812895e00ebecb3cdb4e382fe7.js)

[^footnote]: The footnote source.
