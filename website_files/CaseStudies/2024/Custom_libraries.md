---
template: casestudy.html

title: Building a library of STACK functions for use throughout a linear algebra course
authors: Luke Longworth
shortdescription: Considerations when writing a collection of quiz questions in a specialised topic, and using stack_include to achieve this.
cardimage: 
cardimagealt: 
---

# Building a library of STACK functions for use throughout a linear algebra course

Luke Longworth

### Introduction

I have been developing questions and quizzes with STACK for the University of Canterbury, New Zealand, since the end of 2020, and have seen several courses develop original quizzes from scratch in that time. Whilst our questions are of high quality and our courses do well with constructive alignment, I do find myself encountering two problems frequently:

1. The way students must input their answers differs from question to question within a course. For example, should a student give a list of values `[1,2,3]`, a tuple `(1,2,3)`, something more complicated like a matrix `matrix([1],[2],[3])`, or use a matrix input type?
2. I find myself asking myself the question "I know I wrote some code to solve this a few months ago, where did that question go...?" frequently. This problem is twofold: I am needing to copy code between questions (making debugging a nightmare if I find a problem in either place later), and I can't find the working code when I need it!

These problems cannot be solved easily for existing large question banks, nor do I think that the former is inherently a "problem" anyway (it's more that I would like to have a set of rules/standards to break rather than no rubric at all). However, when constructing new quizzes, we can design with these considerations in mind to create a more internally-consistent product. At the end of 2023, the creation of quizzes for our 200-level engineering linear algebra course was sanctioned. This is a course I had been closely involved with for the past few years, and was the largest advance warning I'd ever received for a course wanting to implement new quizzes. I took this as an opportunity to design quizzes "properly" and have been attempting to avoid the above issues. 

My solution was to create a new maxima file, `linearalgebra.mac` that I could include in my new questions by running `stack_include_contrib('linearalgebra.mac');` at the beginning of each question which would contain various helper functions and could be easily updated to service an entire question bank at once. 

This file is now mostly complete (ignoring the possibly large number of edits and additions that I cannot foresee), and the course question bank is being written. This case study serves mostly as a reflection on whether this has been a suitable solution so far, as well as some documentation on my workflow and considerations when writing the file. The intention is to publish the file to STACK at the end of 2024 once the course of focus has completed, and then any user can use it with `stack_include_contrib`.

### Course Background

The engineering linear algebra course, EMTH211, is a second-year compulsory course for our electronic and mechatronic students. It has a greater focus on numerical linear algebra than the other 200-level course on offer, MATH203, and has a large Python-coding component in lectures and assessment. Expected prior knowledge includes basic matrix arithmetic, Gaussian elimination, determinants, and eigenproblems. 

Students enrolled in this course have been using STACK for at least 3 semesters prior and are familiar with the way that we use quizzes and STACK. The course currently focuses on tutorials that encourage hand-working and Python coding, and are marked for engagement rather than correctness. The first major piece of assessment is not returned until week 7, so students who do not self-assess well may not have had any feedback on their ability to correctly solve problems until the course is over halfway through. The hope is that the introduction of medium-length (8 to 10 questions), fortnightly quizzes will keep students engaged and help them to identify misconceptions and practice basic computations.

### Why is this context a good candidate for this sort of project?

A number of things make this course a good candidate to try out this idea of a central library of useful functions.
- Linear algebra topics in previous courses are the biggest culprits for copying code between questions. In particular, checking whether lines or planes in vector form are correct, and checking eigenvector problems appear time and time again and require a non-insignificant amount of work to extract useful feedback.
- The existing linear algebra tools are mostly concerned with either manipulating matrices in various ways or dealing with _numerical_ linear algebra. The former is useful, but not really for assessing student answers, and the latter is mostly outside the scope of STACK assessment.
- STACK isn't really built to accept expressions that consist of linear combinations or sets of vectors. When we ask students to give matrices or vectors, the logical solution is to either use a matrix input type (not ideal for vector equations of lines for example), or to simply use lists or tuples (not ideal in any situation where we would like to distinguish between column and row vectors).
- Assuming that STACK is largely targeting larger courses where written work is difficult to handle, EMTH211 is likely slightly more advanced than the average course. This suggests that the demand for this content is lower, and therefore better added as an optional inclusion for advanced users rather than included as part of base STACK. 
- Linear algebra is a highly interconnected topic, and I have found that many functions I made for one purpose are instrumental in allowing me to write more advanced functions later.

### What are my hopes for this file?

There were a handful of core ideas and principles that guided the creation of this file.

As our students get more confident with both basic linear algebra concepts and STACK question types, it gets more desirable to let our students interact with vectors as they would any other mathematical object. We frequently deal with expressions or equations involving vectors, and having to manually use `matrix` to input a vector is tiresome. One goal I had with this project was thus to streamline vector notation. I took inspiration from the Matrix section of the STACK documentation and created the `c` and `r` functions for column and row vectors respectively. These are inert functions with an arbitrary number of inputs that are known to be non-scalar by STACK (using the `declare` function) and will display as matrices due to a `texput` call. This enables students to input matrix expressions like `c(1,2,3) + t*c(2,3,4)` easily. 

STACK is built to test properties of algebraic expressions and objects, and I found the variety of matrix-based predicate functions in base Maxima to be lacking. There are plenty of predicates to determine data types, but not many to test actual mathematical properties of these objects. A sensible use of predicate functions also makes writing more complicated functions much easier. For example, many annoying error messages can be avoided easily by calling my new `squarep` predicate function (which checks whether a given object is a matrix and that it has the same number of columns as rows) before running any further code that assumes that property. This package is therefore built to offer many new predicate and comparison functions that return a Boolean answer. 

Another thing that I found frustrating when working on linear algebra questions across multiple courses is that there are simply too many reasonable ways to represent common objects like vector spaces or bases. Therefore, I wanted all of my functions to assume that the input was either a list of lists or a matrix (focusing on its columns) to ease readability. This led to a pair of helper functions that could convert most anything into a list of lists, and then a list of lists to a matrix. This way a student could be asked to input nigh-on anything, such as a set of ntuples, and have a single function do all of the cleaning before running appropriate tests. Neat! 

Lastly, I want the functions I create to be applicable to a range of different questions. If this isn't true, then it should just live in the one question that it is useful for, not in a library of functions. 

With these principles I set out to create this file. 

### What is my workflow?
1. Actually writing the file
2. Test cases and documentation
3. Wrangling GitHub
4. Writing questions with this file
5. Iterative

### Next steps/Limitations
- Randomisation functions 
- File size/load times 
