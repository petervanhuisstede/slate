---
title: Dolores M. Etter's Introduction to C

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - c: C

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
#include <stdlib.h>
#include <math.h>

int main() {
	/* Declare and initialize variables */
	double x1=1, y1=5, x2=4, y2=7,
		side_1, side_2, distance;
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

# Simple C Programs

