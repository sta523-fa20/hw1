# STA 523 :: Homework 1

## Introduction

The Hamming distance is a distance metric for comparing the number of bit
positions that are different in two strings or integers. In this assignment,
you'll create a function that computes a modified Hamming distance for R
objects that are of type character, numeric, and logical.

This modified Hamming distance is defined as follows.

**Strings**: The modified Hamming distance between two equal length strings
is the number of positions at which the letters are different.

- "**r**ight" and "**f**ight" has a modified Hamming distance of 1
- "s**top**" and "s**eek**" has a modified Hamming distance of 3

**Numeric**: The modified Hamming distance between two equal length numbers is
the number of positions at which the digits are different.

- 59**0**1 and 59**1**1 has a modified Hamming distance of 1
- 1**1578** and 1**2241** has a modified Hamming distance of 4

**Logical**: The modified Hamming distance between two boolean values is either
1 or 0 depending on if the two values are different or identical, respectively.

More examples are given in the section titled Task 1.

## Tasks

### Task 0

Briefly look over the below style guides and decide on a coding style that is
best for you.

- [Shawn's learnr tutorial on code style](http://knight.stat.duke.edu:3939/code_style/)
- [The tidyverse style guide](https://style.tidyverse.org)
- [Google’s R Style Guide](https://google.github.io/styleguide/Rguide.html)

With the exception of what is given further below, we won't be
wholly enforcing a specific style in this course, but be consistent and
loosely follow the above guidelines. Below are a few style implementations you
must follow throughout the semester:

1. all code and narrative spans a maximum of 80 characters per line;
2. provide meaningful names when applicable;
3. be consistent in all aspects of your code style.

### Task 1

Write a function in R called `mh_distance()` that computes the modified hamming
distance between two boolean values, numeric quantities, or words.

**Arguments**

- `x`: Takes an atomic vector of length one. Must be one of logical, numeric, or
	character.
- `y`: Takes an atomic vector of length one. Must be one of logical, numeric, or
	character.

**Value**

The function should return the modified Hamming distance between `x` and `y`.

The function should return `-1` if `x` and `y` are not both logical, numeric,
or character; `x` and `y` do not have the same number of digits or letters;
`x` or `y` contain decimal values; `x` or `y` take on `NA`, `NaN`,
`Inf` or `-Inf`. A warning should be provided to let the user know why the
returned value is `-1`. Warning messages can be implemented with function
`warning()`.

**Examples**

```r
> mh_distance(x = 543251, y = 543251)
[1] 0
```

```r
> mh_distance(x = "abc", y = "rtc")
[1] 2
```

```r
> mh_distance(x = TRUE, y = FALSE)
[1] 1
```

```r
> mh_distance(x = 5237, y = 11523)
[1] -1
Warning message:
In mh_distance(x = 5237, y = 11523) :
  x and y do not have the same number of digits or letters
```

```r
> mh_distance(x = Inf, y = -Inf)
[1] -1
Warning message:
In mh_distance(x = Inf, y = -Inf) : x or y cannot be NA, NaN, Inf, or -Inf
```

**Odds and ends**:

- You may find functions `strsplit()` and `nchar()` helpful.

- You may only use functions and operators available in `base` R.

- You do not need to handle special characters in strings
	(words such as `"can't"`) or situations where a user may pass in `NULL`.

- Please use code comments as you see fit. However, you do not need to document
	every line; there is a write-up portion in Task 4.

### Task 2

Perform testing and validation of your function. Try the test cases provided
and include additional test cases in your R Markdown document to demonstrate
the robustness of your function. This may inspire you to go back and refactor
your code. Your function should appropriately handle invalid inputs as
described above by providing an informative warning message and returning `-1`.
There will be a hidden set of test cases that will be used for grading purposes.
The more cases your function handles in the correct manner, the better your
grade will be on this assignment.

### Task 3

Function `mh_distance()` is not vectorized. Write a loop to compute
the modified Hamming distance for the pair of vectors given in the R Markdown
file. For those element pairs that have a valid modified Hamming distance
(not `-1`), a statement should be printed stating the distance for the
given pair. An example is given below.

Two example vectors:

```r
w <- c("cat", "dog", "horse", "fish")
v <- c("cat", "hog", "houses", "chip")
```

Example output:

```r
[1] "The modified Hamming distance between cat and cat is 0"
[1] "The modified Hamming distance between dog and hog is 1"
[1] "The modified Hamming distance between fish and chip is 4"
```

**Odds and ends**:

- You may find function `paste0()` helpful in formatting your output.
	```r
	> paste0("This", " is", " an example with paste0!")
	[1] "This is an example with paste0!"
	```


### Task 4

Include a brief write-up that describes how you approached the problem and
constructed your solution for Task 1. At a minimum, your write-up should

- discuss how you handled possible invalid inputs;
- explain some of your code choices;
- and describe any weaknesses with your code and resulting function.

## Essential details

### Deadline and submission

**The deadline to submit Homework 1 is Wednesday, September 2 at 11:59pm EST.**
Only your final commit and code in the master branch will be graded.
Do not forget to push your work to your assigned repository on GitHub before
the deadline.

### Help

- Post your questions in the #hw1 channel on Slack. Explain your error / problem
  in as much detail as possible or give a reproducible example that generates
  the same error. Make use of the code snippet option available in Slack.

- Visit the instructor or TAs in Zoom office hours.

- The instructor and TAs will not answer any questions about this assignment
 	within six hours of the deadline.

### Academic integrity

This is an individual assignment. You may communicate with others in the
course, but you must write-up your own solution. As a reminder, any
code you use directly or as inspiration must be cited.

To uphold the Duke Community Standard:

- I will not lie, cheat, or steal in my academic endeavors;
- I will conduct myself honorably in all my endeavors; and
- I will act if the Standard is compromised.

Duke University is a community dedicated to scholarship, leadership, and
service and to the principles of honesty, fairness, respect, and accountability.
Citizens of this community commit to reflect upon and uphold these principles in
all academic and non-academic endeavors, and to protect and promote a culture of
integrity. Cheating on exams and quizzes, plagiarism on homework assignments and
projects, lying about an illness or absence and other forms of academic
dishonesty are a breach of trust with classmates and faculty, violate the Duke
Community Standard, and will not be tolerated. Such incidences will result in a
0 grade for all parties involved as well as being reported to the University
Judicial Board. Additionally, there may be penalties to your final class grade.
Please review Duke’s Standards of Conduct.

### Grading

Your code will be evaluated for its accuracy, efficiency, and style.

| **Topic**             | **Points** |
|-----------------------|-----------:|
| Tasks 1 & 2           |         16 |
| Task 3                |          4 |
| Task 4                |          3 |
| 3 commits minimum     |          3 |
| Code style and format |          3 |
| Named R code chunks   |          1 |
| **Total**             |     **30** |

*Documents that fail to knit after minimal intervention will receive a 0*.

## References

1. Google’s R Style Guide. (2020). https://google.github.io/styleguide/Rguide.html.

2. Wickham, H. (2020). The tidyverse style guide. https://style.tidyverse.org/.
