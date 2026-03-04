# Lab 7: String Comparison and Sorting Cities
**Due Date:** @ 11:59 the night *before* next lab

**Submission:** Push to GitHub repository + Submit link to Blackboard

---

## 📋 Overview
This lab introduces **string comparison** using the `compareTo()` method and applies it to a practical problem: sorting city names alphabetically. You'll learn how Java compares strings, how to use comparison results to make decisions, and how to build logical conditions to handle multiple sorting scenarios.

**Learning Objectives:**
- Use `compareTo()` and `compareToIgnoreCase()` methods to compare strings
- Understand how string comparison returns values indicate alphabetical order
- Build complex boolean expressions using logical operators (`&&`, `||`)
- Implement a sorting algorithm for three strings
- Handle all possible orderings of input data
- Use `Scanner` to read and process user input
- Apply conditional logic to determine output order

---

## 🚀 Getting Started with GitHub Codespaces

### Initial Setup
1. **Accept the assignment** via the GitHub Classroom link provided
2. **Open your repository** in GitHub Codespaces:
   - Click the green "**Code**" button
   - Select "**Codespaces**" tab
   - Click "**Create codespace on main**"
3. **Wait for the environment to load** (this may take 1-2 minutes on first launch)
4. **Explore your workspace** - On the left side, you'll see the file explorer with:
   - `README.md` (this file)
   - `InClass7_FirstName_LastName.java` - for your in-class activity
   - Other supporting files

**Note:** You will create the `Lab7_FirstName_LastName.java` file yourself. Update all filenames and class headers with your actual first and last name.

---

## 📚 Understanding String Comparison

Strings are fundamental in programming—they represent names, addresses, messages, and countless other types of data. Being able to compare and sort strings is essential for organizing data, searching efficiently, and creating user-friendly applications.

### The compareTo() Method
Java provides the `compareTo()` method for comparing strings lexicographically (dictionary order, based on Unicode values).

**Syntax:**
```java
int result = string1.compareTo(string2);
```

**Return values:**
- **Negative number:** `string1` comes **before** `string2` alphabetically
- **Zero:** Both strings are **identical**
- **Positive number:** `string1` comes **after** `string2` alphabetically

**Examples:**
```java
String city1 = "Austin";
String city2 = "Dallas";

int result = city1.compareTo(city2);  // Returns a negative number
// Why? "Austin" comes before "Dallas" alphabetically
```

```java
String city1 = "Houston";
String city2 = "Dallas";

int result = city1.compareTo(city2);  // Returns a positive number
// Why? "Houston" comes after "Dallas" alphabetically
```

```java
String city1 = "Austin";
String city2 = "austin";

int result = city1.compareTo(city2);  // Returns a negative number
// Why? Uppercase letters have lower Unicode values than lowercase
```

### Case-Insensitive Comparison
To ignore case differences (treating "Austin" and "austin" as the same), use `compareToIgnoreCase()`:

```java
String city1 = "Austin";
String city2 = "austin";

int result = city1.compareToIgnoreCase(city2);  // Returns 0
// They are considered equal when ignoring case
```

### Using Comparison Results in Conditions
You can use the result in an `if` statement to make decisions:

```java
String city1 = "Austin";
String city2 = "Dallas";

if (city1.compareToIgnoreCase(city2) < 0) {
    System.out.println(city1);  // Print Austin first
    System.out.println(city2);  // Then print Dallas
} else {
    System.out.println(city2);  // Print Dallas first
    System.out.println(city1);  // Then print Austin
}
```

### Sorting Three Items
Sorting three strings requires comparing pairs to determine the correct order. There are **six possible orderings** when the user enters three different cities:

1. city1, city2, city3 (already in order)
2. city1, city3, city2
3. city2, city1, city3
4. city2, city3, city1
5. city3, city1, city2
6. city3, city2, city1

**Key insight:** Use logical operators to combine comparisons and determine which city comes first, second, and third.

---

## 📝 Part 1: In-Class Activity (Participation Points)
**File to Work With:** `InClass7_FirstName_LastName.java`

### Task
Write a program that accepts **two city names** from the user and prints them in alphabetical order. This simpler two-city comparison will prepare you for sorting three cities in the main lab.

**Requirements:**
1. **Update** the filename and class name with your actual first and last name
2. **Import** Scanner at the top of your file
3. **Declare variables** to store:
   - The first city name (`String`)
   - The second city name (`String`)
4. **Prompt** the user to enter the first city name
5. **Prompt** the user to enter the second city name
6. **Compare** the two cities using `compareToIgnoreCase()`
   - *Hint:* Check if the result is less than 0, equal to 0, or greater than 0
7. **Print** the cities in alphabetical order
   - If city1 comes before city2, print city1 first, then city2
   - Otherwise, print city2 first, then city1
8. **Add detailed comments** throughout your code explaining:
   - What the program does overall (at the top)
   - What each variable stores
   - How `compareToIgnoreCase()` works
   - Why you check if the result is less than 0
   - What each if/else branch does

### Example Outputs
```
Enter the first city: Dallas
Enter the second city: Austin

Cities in alphabetical order:
Austin
Dallas
```

```
Enter the first city: Houston
Enter the second city: San Antonio

Cities in alphabetical order:
Houston
San Antonio
```

```
Enter the first city: Austin
Enter the second city: austin

Cities in alphabetical order:
Austin
austin
```
*(Note: Both are printed because they're equal alphabetically, just printed in the input order)*

### What You Should Figure Out
Think about:
- What Scanner method reads strings with spaces? (Hint: not `next()`)
- How do I check if one string comes before another?
- What does a negative return value from `compareToIgnoreCase()` mean?
- Do I need two separate if/else blocks or just one?
- Should I use `compareTo()` or `compareToIgnoreCase()`?

---

🚦 **STOP! Checkpoint** 🚦

Before you go any further, take a moment to **commit and sync your work so far** to reflect your In-Class 7 work.

Not sure how? Skip to the ["📤 Submitting Your Lab"](#-submitting-your-lab) instructions near the end of this document!

---

**You will receive full participation credit for completing and submitting this in-class exercise. Your code must be finished and clearly commented.**

---

## 🎯 Part 2: Graded Lab Assignment (100 Points)
**File to Create:** `Lab7_FirstName_LastName.java`

### Purpose
A delivery company is developing an address catalog for selecting package delivery locations. To make the catalog efficient and user-friendly, locations must be sorted alphabetically. You will write a sorting algorithm that accepts three city names and prints them in alphabetical order.

This program emphasizes:
- Using `compareToIgnoreCase()` to perform case-insensitive string comparisons
- Building complex boolean expressions with logical operators (`&&`, `||`)
- Analyzing all possible input orderings to produce correct output
- Implementing a multi-conditional algorithm that handles six different scenarios
- Understanding how comparison methods return values indicate ordering

**Important:** Only the `InClass7_FirstName_LastName.java` file is provided as a starter template. You must create the lab file from scratch, including:
- Proper class header with comments
- Correct class name matching your filename
- `public static void main(String[] args)` method
- All necessary imports

This is an essential skill for building programs independently!

### Step-by-Step Instructions

#### Step 1: Create Your Java File (Required)
- Create the file `Lab7_FirstName_LastName.java`
- **Update** the filename and class name with your actual first and last name
- **Example:** If your name is Maria Garcia, create `Lab7_Maria_Garcia.java` with class name `Lab7_Maria_Garcia`

#### Step 2: Add File Header Comments (5 points)
At the top of your file, include a comment block summarizing:
- Your name
- The date
- The purpose of the program (sorting three cities alphabetically)

```java
/**
 * Name: [Your Name]
 * Date: [Today's Date]
 * Purpose: Sort three city names in alphabetical order using string comparison
 */
```

#### Step 3: Import Scanner (2 points)
```java
import java.util.Scanner;
```

#### Step 4: Declare Variables (5 points)
You will need variables to store the three city names. You may also find it helpful to declare variables for comparison results or boolean values, though this is optional.

**Required:**
- Three `String` variables for the three cities

**Optional (but potentially helpful):**
- Boolean variables to store comparison results
- Integer variables to store `compareToIgnoreCase()` results

#### Step 5: Create Scanner and Prompt for Cities (9 points total - 3 per city)
Create a Scanner object and prompt the user to enter three city names:

```java
Scanner input = new Scanner(System.in);
System.out.print("Enter the first city: ");
// Read the first city...

System.out.print("Enter the second city: ");
// Read the second city...

System.out.print("Enter the third city: ");
// Read the third city...
```

**Important:** Use the appropriate Scanner method to read **entire city names** including spaces (like "San Antonio" or "New York").

**Think about:** What Scanner method reads an entire line of text, not just one word?

#### Step 6: Compare and Sort the Cities (84 points)
This is the heart of the assignment! You need to determine the alphabetical order and print the cities accordingly.

**Your program must handle all six possible orderings:**
1. city1 ≤ city2 ≤ city3 → Print: city1, city2, city3
2. city1 ≤ city3 ≤ city2 → Print: city1, city3, city2
3. city2 ≤ city1 ≤ city3 → Print: city2, city1, city3
4. city2 ≤ city3 ≤ city1 → Print: city2, city3, city1
5. city3 ≤ city1 ≤ city2 → Print: city3, city1, city2
6. city3 ≤ city2 ≤ city1 → Print: city3, city2, city1

**Each correct ordering is worth 14 points.**

**Approach:**
Use nested `if-else` statements with comparison methods to determine which city comes first, second, and third.

**Strategy example:** 
- First, determine which city comes first alphabetically (compare all three)
- Then, determine which of the remaining two comes second
- The third city is what's left

**Alternative strategy:**
- Use a series of if-else conditions that check all six possible orderings

**Hints:**
- Use `compareToIgnoreCase()` for case-insensitive comparison
- Check if the result is `< 0` (first string comes before second)
- Combine comparisons with `&&` (both conditions must be true)
- Example: `if (city1.compareToIgnoreCase(city2) < 0 && city1.compareToIgnoreCase(city3) < 0)`
  - This checks if city1 comes before both city2 AND city3

**Think about:**
- How do I check if city1 comes before both city2 and city3?
- If city1 comes first, how do I determine whether city2 or city3 comes second?
- Can I nest an if-else inside another if-else?
- Should I check all comparisons in one big if-else chain, or break it into smaller parts?

### Example Program Flows

**Example 1:**
```
Enter the first city: Dallas
Enter the second city: Austin
Enter the third city: Houston

Cities in alphabetical order:
Austin
Dallas
Houston
```
- Input order: Dallas, Austin, Houston
- Alphabetical order: Austin, Dallas, Houston

**Example 2:**
```
Enter the first city: San Antonio
Enter the second city: Houston
Enter the third city: Austin

Cities in alphabetical order:
Austin
Houston
San Antonio
```
- Input order: San Antonio, Houston, Austin
- Alphabetical order: Austin, Houston, San Antonio

**Example 3:**
```
Enter the first city: Austin
Enter the second city: Dallas
Enter the third city: Houston

Cities in alphabetical order:
Austin
Dallas
Houston
```
- Input order: Austin, Dallas, Houston
- Alphabetical order: Austin, Dallas, Houston (already sorted!)

**Example 4:**
```
Enter the first city: El Paso
Enter the second city: corpus christi
Enter the third city: Amarillo

Cities in alphabetical order:
Amarillo
corpus christi
El Paso
```
- Demonstrates case-insensitive sorting

---

## 🎓 Assumptions

To keep this lab focused on string comparison and sorting logic, you may assume:
- The user enters three **different** city names (no duplicates)
- Case does **not** matter (use case-insensitive comparison)
- You do NOT need to validate that the input is actually a city name
- You do NOT need to handle empty input or special characters
- Each city name can contain spaces (like "San Antonio")

---

## 📊 Grading Rubric

| Criteria | Points |
|----------|---------|
| **Comment summarizing the program** | 5 |
| **Importing and declaring the Scanner** | 2 |
| **Prompt for first city** | 3 |
| **Prompt for second city** | 3 |
| **Prompt for third city** | 3 |
| **Correctly handling ordering 1** (city1, city2, city3) | 14 |
| **Correctly handling ordering 2** (city1, city3, city2) | 14 |
| **Correctly handling ordering 3** (city2, city1, city3) | 14 |
| **Correctly handling ordering 4** (city2, city3, city1) | 14 |
| **Correctly handling ordering 5** (city3, city1, city2) | 14 |
| **Correctly handling ordering 6** (city3, city2, city1) | 14 |
| **TOTAL** | **100** |

---

## 💡 Tips for Success

1. **Start simple** - Get the in-class two-city version working first
2. **Test all six orderings** - Try entering cities in different orders to verify all cases work
3. **Draw it out** - Write the six possible orderings on paper before coding
4. **Use meaningful variable names** - Consider `city1`, `city2`, `city3` or `firstCity`, `secondCity`, `thirdCity`
5. **Comment your logic** - Explain which ordering each if-else block handles
6. **Use `compareToIgnoreCase()`** - Remember case doesn't matter
7. **Understand the return value** - Negative means first string comes before second
8. **Test with real city names** - Use cities you know to verify the sorting makes sense

### Common Pitfalls to Avoid
- **Using `next()` instead of `nextLine()`** - `next()` only reads one word, so "San Antonio" would be read as just "San"
- **Forgetting `< 0` in comparisons** - You need to check if the result is less than, equal to, or greater than zero
- **Not handling all six orderings** - Make sure your logic covers every possible input order
- **Using `compareTo()` instead of `compareToIgnoreCase()`** - Case matters with `compareTo()`, which could give wrong results
- **Confusing comparison direction** - If `city1.compareTo(city2) < 0`, then city1 comes **before** city2

### Debugging Strategy
If your program doesn't work for all cases:
1. **Test each ordering individually** - Enter cities in each of the six possible orders
2. **Add print statements** - Print comparison results to see what values you're getting
3. **Trace through your logic** - For each test case, manually follow your if-else chain
4. **Check your boolean logic** - Make sure `&&` and `||` are used correctly

---

## 📤 Submitting Your Lab

### Using VS Code in Codespaces

1. **Stage your changes:**
   - Click the **Source Control** icon in the left sidebar (looks like a branching diagram)
   - You'll see your changed files under "Changes"
   - Click the **+** button next to each file to stage it (or click the + next to "Changes" to stage all)

2. **Commit your changes:**
   - Type a descriptive message in the text box at the top (e.g., "Completed Lab 7")
   - Click the **✓ Commit** button (or press Ctrl+Enter)

3. **Push to GitHub:**
   - Click the **•••** (three dots) menu in the Source Control panel
   - Select **Push** (or click the cloud icon with an up arrow)
   - Your changes are now on GitHub!

4. **Submit to Blackboard:**
   - Go to your GitHub repository in a web browser
   - Copy the URL from the address bar
   - Submit this URL to the Lab 7 assignment on Blackboard

### Verification
To verify your submission worked:
- Visit your GitHub repository
- You should see your Java files updated with recent commit timestamps
- Click on your files to ensure the latest code is visible

---

## 🆘 Getting Help

If you get stuck:
1. **Review the concept sections** in this README
2. **Check the example outputs** - Make sure you understand what the program should do
3. **Test with the in-class two-city version** - If that works, extend the logic to three cities
4. **Ask during lab time** - Your instructor and TAs are there to help
5. **Use office hours** - Don't wait until the last minute
6. **Work with classmates** - Discuss approaches and logic, but write your own code

**Academic Integrity Reminder:** You may discuss concepts and approaches with others, but your code must be your own work. Copying code from others or online sources is a violation of academic integrity.

---

## 🎉 You've Got This!

String comparison and sorting are fundamental programming skills. While sorting three items might seem straightforward, handling all possible cases requires careful logical thinking—exactly the kind of problem-solving skills that make you a better programmer. Take your time, test thoroughly, and don't hesitate to ask for help!

Good luck! 🚀

💡 **Fun Tip:** Consider taking a screenshot of your terminal output after running your program with different city combinations! Then, try to figure out how to add that screenshot file to your repository directory as part of your lab submission. (This is a great way to document your work and practice using GitHub for more than just code!)

---

## Commit Your Changes
### Step 1. Use VS Code's Source Control panel:
   - Click the Source Control icon in the left sidebar
   - Type a commit message describing your changes
   - Click "Commit" then "Sync Changes" to push your code

### Step 2: Verify Submission
After pushing your changes, visit your assignment repository on GitHub Classroom. Confirm that your latest code and commit message appear, and that your files are named correctly. 

### Step 3: Submit to Blackboard Assignment
Once you have verified your submission on GitHub Classroom, copy the URL of your assignment repository and submit this GitHub repository link to Blackboard as confirmation that you are DONE.

**InClass7_FirstName_LastName.java (Participation points):**
Full credit is awarded for completing and submitting the in-class exercise, regardless of output or minor errors.

**Excellent work!** You've reached Lab 7, and this assignment introduces you to the powerful world of string comparison and sorting algorithms. This lab challenges you to think logically about all possible orderings and to build conditional structures that handle each case correctly. Working with the `compareTo()` method and logical operators will deepen your understanding of how computers compare and organize text data—skills that apply to databases, search engines, and countless other applications. Remember, every programmer has wrestled with sorting logic—embrace the challenge, break down the problem into smaller comparisons, and don't hesitate to test your code with all six possible orderings. You're building the foundation for more advanced algorithms!

**Important:** This lab template includes `InClass7_FirstName_LastName.java` with helpful comment guidance to get you started. Focus on completing both the in-class exercise and the main lab assignment. Do NOT edit or tamper with any test files if they appear in your repository. These files are used for autograding and checking your work.