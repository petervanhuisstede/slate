---
title: Dolores M. Etter's Introduction to C (for Python)

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - c

toc_footers:
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  # - errors

search: true

code_clipboard: true
---

# An Introduction to Engineering Problem Solving

Etter concentrates on the language parts of C that an engineer needs
to solve typical engineering problems.

Because C is a small language, concentrating on the topics concerning
engineering and problem solving results in a condensed text that presents
a minimal viable way for writing useful programs.

Here we use the structure of "Introduction to C" published in 1998,
with 121 pages a small programming book indeed, to explore the Python
programming language.

## An Engineering Problem-Solving Methodology

Problem solving techniques bind together various areas: Computing,
mathematics, physics, etc.

Etter proposes the following 5 steps problem-solving method:

1. State the problem clearly;
2. Describe the input and the output information;
3. Work the problem by hand for a simple set of data;
4. Develop a solution and convert it into a computer program;
5. Test the solution using a variety of data.

### Problem Statement

Example: Compute the straight-line distance between 2 points in a
plane.

### Input/Output Description

input   |  function |  output
-----   |  -------- |  ------
point 1 |  ?        |  distance between two points
point 2 |           | 

### Hand Example

Even for simple problems an important step (NEVER TO BE
SKIPPED!). Here you work out the details of the problem solution: Take
a simple set of numbers (input) and compute the output.

> p1 = (1,5); p2 = (4,7)

Here we use the following coordinates for p1 and p2:
	
> distance = sqrt(side1^2 + side2^2) <br />
> distance = sqrt((4-1)^2 + (7-5)^2) <br />
> distance = sqrt(13) <br />
> distance = 3.61

Now, the distance between 2 points is the hypothenuse of the right
triangle. Which brings us to the application of the Pythagorean
theorem.

Note that we can infer very useful information from our hand
example. Types of input (two numbers) and output (one number):
integers and floats; we probably need to call in a math library to
provide the sqrt function, and we need to show (print) the result.

### Algorithm Development

```C
/*
Program chapter 1.1: points.c
Compute the distance between 2 points
*/
#include <stdio.h>
#include <math.h>

int main() {
	// Declare and initialize variables
	double x1=1, y1=5, x2=4, y2=7,
		side_1, side_2, distance;
	// Compute the sides of a right triangle
	side_1 = x2 - x1;
	side_2 = y2 - y1;
	distance = sqrt(side_1*side_1 + side_2*side_2);
	// Print the distance
	printf("The distance between the 2 points is: %5.2f\n", distance);
	// Exit the program gracefully
	return 0;
}
```

[Python Exercise 1: Re-write the file points.c in Python]
[Python Exercise 2: What are the main difference between the points.c
file and your points.py?

List the steps to take to get to the solution. We decompose the
problem into an outline of simple steps (decomposition outline):

1. Give values to the 2 points
2. Compute the length of the 2 sides of the right triangle generated
   by the two points
3. Compute the distance between the two points (equal to the length of
   the hypothenuse of the triangle)
4. Print the distance between the 2 points

For this program to run we need to compile it and run the compiled
executable. For this we use a simple Makefile that is placed in the
same directory as the source file "points.c"

```shell
make
```

Our Makefile gets the libraries lined up and yields the executable
file "points". Which again we can run from the CLI.

```shell
./points
```

Which prints the result of our computation in the terminal.

> The distance between the 2 points is:  3.61

[Python Exercise 3: Check the working of your Python file. What are
the different ways (on your computer) to run the Python file?]

```shell
PROGNAME = [name without the .c]
objects = 
CFLAGS = -g -Wall `pkg-config --cflags apophenia glib-2.0` -std=gnu11 -O3
LDLIBS = `pkg-config --libs apophenia glib-2.0`

$(PROGNAME): $(objects)
```

A simple Makefile I often use (context dependent).

# Simple C Programs

## Objectives of this section

- Learn to write a simple C program
- Use C statements that define constants and variables
- Learn how to do simple arithmetic in C
- Use C statements to read input from the keyboard, and print output
  to the screen
- Read about mathematical functions used to solve (engineering)
  problems

## Program Structure

In the previous section we saw a small, but complete C program (points.c) that
calculated the distance between two points on a plane.

```c
/*
Program chapter 1.1: points.c
Compute the distance between 2 points
*/
```

The lines between the markers `/* .. */` are comments to make the
program readable (for future users or for oneself in the near future).

[Python Exercise 4: Describe the way(s) to add comments to Python files.]

```c
#include <stdio.h>
#include <math.h>
```

The next two lines are so-called *preprocessor directives* which give
instructions to the compiler before the actual program is compiled:
`<stdio.h>` stands for standard Input/Output and provides for the use
of the `printf()` function, `<math.h>` provides the `sqrt()`
function. The arrows indicate that both functions belong to the
*Standard C Library*.

[Python Exercise 5: What libraries did you have to include in your
points.py to get the program to work? What is the syntax of these
imports?]

```c
int main() {
	[...]
}
```

Every C program has a `main()` function which is the entry and exit
point of the program. `main()` contains two kinds of commands:

1. Declarations
2. Statements

[Python Exercise 6: Did your points.py have a main() function? Do
Python programs use a main function? And if so, what does it normally
do?]

```c
int main() {
	/* Declare and initialize variables. */
	double x1=1, y1=5, x2=4, y2=7,
        side_1, side_2, distance;
}
```

*Declarations* define the memory locations that the statements will
use. Hence the type indications like `double` (The compiler needs to
allocate a little more space for `doubles` then for `intergers`). In
our program we declare 7 variables that are all of the type `double`;
four of the variables (our two points on the plane) are initialized,
three are not.

[Python Exercise 7: How did you handle the declaration and
initialization of variables in your points.py?]

```c
int main() {
    /* Compute the sides of a right triangle */
    side_1 = x2 - x1;
    side_2 = y2 - y1;
    distance = sqrt(side_1*side_1 + side_2*side_2);
    /* Print the distance */
    printf("The distance between the 2 points is: %5.2f\n", distance);
    /* Exit the program gracefully */
    return 0;
}
```

*Statements* specify the operations to be performed in the
program. Here we see our handwork return in the calculation of the
variable `distance`. After computing the distance using the
Pythagorean theorem, we use the `printf()` to print the result.

The last line is just a convention to gracefully exit the main
function.

To sum up, we have just seen the *general form* of a C program:

*preprocessing directives* <br />
main() { <br />
    *documentation* <br />
    *declarations*; <br />
    *statements*; <br />
} <br />

## Constants and Variables

*Constants* in C are specific values that are used in C
statements. Think a working value for Pi like 3,1416 (or, more
precise: 3.141593).

*Variables* are memory locations that are given a name (identifier)
and one uses the name to reference the value stored in that memory
location. Often people use metaphors to explain this concept of
*variables*, like:

- Mailbox metaphor (name -> mailbox that contains mail)
- Library metaphor (shelfmark -> location where you find a book)

```c
double x1=1, y1=5, x2=4,y2=7,
    side_1, side_2, distance;
```

This snippet from our small program can be seen as a *memory
snapshot*:

variable name | mailbox | type (size) of mailbox
------------- | ------- | ----------------------
x1 | 1 | double
y1 | 5 | double
x2 | 4 | double
y2 | 7 | double
side\_1 | ? | double
side\_2 | ? | double
distance | ? | double

Some mailboxes contain a value, we call these variables *initialized*;
other mailboxes are yet to be filled with values (but they have
already got a size assigned in order to be able to hold the values
that we are going to send them!).

And just like we developed an idea what to program in order to
calculate the distance between two points on the plane by using pencil
and paper, we can use *memory snapshots* to track what a program is
doing.

[Python Exercise 8: Did you declare types of variables in your
points.py? If not, are there ways to check if and what types Python
uses internally for the variables in your points.c? Suppose you want
to add types to the variables you declare in points.py, is that
possible in Python and, if so, how is it accomplished?]

In C the rules for selecting valid names for variables are:

- A name must begin with an alphabetic character or an underscore;
- Alphabetic characters in names can be lowercase or uppercase (C is
  *case sensitive*!!!);
- A name can contain digits (0-9), but not as the first character;
- One can not use C keywords as names for variables.

In C these are the *reserved keywords* (31):

col 1 | col 2 | col 3 | col 4
----- | ----- | ----- | -----
auto | double | int | struct
break | else | long | switch
case | enum | register | typedef
char | extern | return | union
const | float | short | unsigned
continue | for | signed void | volatile
default | goto | sizeof | while
do | if | static

[Python Exercise 9: Draw up a list or table of (reserved) keywords in
Python.]

### Scientific Notation (vs. Floating Point Notation)

1.5 == 1.5e0
25.6 == 2.56e1 (2.56x10e1)
-0.004 == 4.0e-3

### Numeric Data Types

```c
#include <stdio.h>
#include <limits.h>
/* Determine the ranges of the numeric data types (on your computer)
*/
int main() {
    // Signed types
    printf("Signed char min: %d\n", SCHAR_MIN);
}
```

Numeric data types: Integers or floating point values

Integers are specified by types: *short*, *int*, and *long*. Ranges
are *system dependent*

Floats are specified by types: *float* (single-precision), *double*
(double-precision), and *long double* (extended precision). Again,
precision and range are *system dependent*

### Symbolic Constants

```c
#define PI 3.141593 // No semicolon!
```

Simple directives like:

### Assignment Statements

identifier = expression; [where = reads as: "is assigned the value
of"]

expression can be:

- constant
- another variable
- the result of an operation

Be careful to assign values to variables that have different data
types; one must use data conversions

### Data conversions

Data conversions (signed) are safe from low to high:

high:

- long double
- double
- float
- long integer
- integer
- short integer

low:

### Practice

```c
/* practice_p25 */
#include <stdio.h>

int main() {
    // 1
    int a = 27, b = 6, c;
    c = b % a;
    printf("Value of c is: %d\n", c);
    
    // 2
    int d = 27, e = 6;
    float f;
    f = d / (float)e;
    printf("Value of f is: %f\n", f);
    
    // 3
    int h;
    float i = 6, j = 18.6;
    h = j / i;
    printf("Value of h is: %d\n", h);
    
    // 4
    int k = 6;
    float l, m = 18.6;
    l = (int)m / k;
    printf("Value of l is: %f\n", l);
}
```

Predict the value and its type computed by each of the following sets
of statements. First use pencil and paper. Then write a small C
program to check your answers.

    practice_p25<br />
    ---<br />
    1.<br />
    int a = 27, b = 6, c<br />
    ...<br />
    c = b % a<br />
    
    2.<br />
    int d = 27, e = 6<br />
    float f<br />
    ...<br />
    f = d / (float)e<br />
    
    3.<br />
    int h<br />
    float i = 6, j = 18.6<br />
    ...<br />
    h = j / i<br />
    
    4.<br />
    int k = 6<br />
    float l, m = 18.6<br />
    ...<br />
    l = (int)m / k<br />

If you do the pencil and paper version and keep track of the type of
the values that we compute, you will see that you can use that
information to write the actual program.

[python exercise: 10] Use the Python repl to calculate the results in
Python and compare them to the results generated by the C
program. Write about the differences between C and Python.

<b>Priority of Operators</b>
