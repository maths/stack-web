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

EMTH211 is a good candidate for this type of project because of its status as a 200-level linear algebra course. There are lots of regularly used routines in linear algebra, so code-sharing is commonplace. The existing linear algebra support in Maxima is mostly concerned with manipulating matrices, with some other packages doing very specific things (such as `diag` for computing Jordan normal forms, or `lapack` for running numerical routines). This leaves plenty of room for functions that are widely applicable, simple, and useful. The Algebraic input type doesn't have good support for matrices or vectors, and the Matrix input types are not suitable for expressions _containing_ matrices or vectors, so tools to smooth this over will be naturally useful. Students at 200-level are likely to be confident enough to engage with these slightly more abstract input types as well. 

### What does this file contain?

1. Functions about form

The first thing that appears is the `c` and `r` functions. These are inert functions that students and teachers can use to represent column and row vectors respectively, and the validation box will correctly display them. This allows students to write expressions containing vectors without needing to use Maxima's matrix notation. 

The LaTeX formatting is done using `texput` to extract the arguments, format them individually using `tex1`, and then put them all together within appropriate LaTeX matrix wrapping. The two functions are also declared nonscalar, so that expressions like `c(1,2) + matrix([3],[4])` will simplify to `matrix([4],[6])` rather than `matrix([3 + c(1,2)],[4 + c(1,2)])`. 

`texput` interacts with validation unexpectedly, in that the validation LaTeX display is only "aware" of any lines in the Question Variables that are exactly `texput(...)`. This means that you cannot put the `texput` inside a larger block of code (notably, including if statements) or refer to other existing variables, functions or flags within the `texput` code itself. Ideally, teachers would be able to choose whether to include this part of the file with a flag variable (in case they are wanting to use the variable `c` for a constant of integration, or `r` to refer to the vector `[x,y,z]` etc.), but this is not possible. Even nicer would be the ability to choose what type of matrix bracket is used (questions that ask for lists of vectors are a bit confusing to read at present), or to match the question-wide matrix bracket choice. Perhaps future versions will give more control over `texput` and validation, but for now these suffice. 

There are also a number of functions that convert statements between various "standard forms". It is much easier to write this library of routines knowing that everything is either a list of lists or a matrix. Convenience functions are provided that will convert groups (i.e. lists, sets, ntuples, spans, and others) of vectors (matrices, `c`, `r`, lists, ntuples) into a list of lists, and then to convert a list of lists into a matrix. 

2. Predicates

Predicates are exceptionally useful little tools to use in PRTs or inside larger routines to avoid unwanted error messages. There are not many Maxima-native predicates to do with linear algebra outside of `matrixp`, `zeromatrixp` and `blockmatrixp`, and there are many properties of matrices we may want to check. There are many predicates here that teachers can use to quickly check properties of student answers, or that they can use to filter out answers of unexpected form. 

There are also a handful of comparison functions that test some sort of equivalence between a teacher's answer and a student't answer. These are mostly to do with equivalence of subspaces and linear independence, as algebraic equivalence is too restrictive to test these properties. 

3. Useful functions for manipulating matrices, collections of vectors, or algebraic expressions containing vectors. 

This is self-explanatory and takes up the bulk of the file. There is a lot of variety here and interested parties should look at the file itself to browse options. 

4. Matrix Factorisations 

This one is a little self-indulgent, as it usually makes little sense to find exact representations of a matrix QR factorisation, SVD, or diagonalisation unless the matrix has been set up explicitly to produce nice answers in this case. In EMTH211, we use Python to find solutions to these generic cases, and I can't think of any cases where these functions are likely to be _that_ useful, but it felt wrong to write a linear algebra package and not include these common factorisations. 

### What was my writing process? 

My writing process is not particularly good practice and wouldn't scale well, but it has worked for me and is entirely in-browser. This suits me, as I use a remote desktop connection at work and don't have much control over my own installs and settings. 

1. GitHub

If you're new to GitHub (I certainly am) here is a rundown on my process. 
- From the STACK home on GitHub (github.com/maths/moodle-qtype_stack), click the Fork button to create your own copy of STACK.
- Go to the fork you've created and create a new branch, either by clicking the "master" dropdown menu and typing your new branch name in, or by clicking on branches and then selecting "New branch". I called mine `linear-algebra-beta`. 
- From this branch, navigate to stack/maxima/contrib, and click Add file. In my case, I simply created a new file called `linearalgebra.mac`. 
- Now, once you've created the file and committed the changes, you can click the "Raw" button when viewing the code, and copy this URL into a STACK question to get access to this code. In my case, I have been using `stack_include("https://raw.githubusercontent.com/MY_ACCOUNT_HERE/moodle-qtype_stack/linear-algebra-beta/stack/maxima/contrib/linearalgebra.mac");` at the beginning of my questions, and will eventually transition it to `stack_include_contrib("linearalgebra.mac")` when this file is published to STACK properly. 

Nowadays I am doing most of my work directly in GitHub, but when writing functions initially it's nicer to get some more immediate feedback.

2. Send to CAS

This is twisting the intended use case of this function a bit, but it has worked excellently for me. I often use the "Send general feedback to the CAS" link for quick-and-dirty testing in a real STACK environment. You can access this link from the STACK question dashboard (I have an empty question bookmarked for this). You can edit the question variables and general feedback fields of a question temporarily, and even use `stack_include`. 

My main workflow was to include this header:

	simp: false;
	tests: [];
	s_test_case(sa,ta):= tests: append(tests,[[is(sa=ta),sa,ta]])

followed by either `stack_include` or simply a copy-paste of the code I'm wanting to check, and then I would put the following into the General Feedback field:

	[[foreach test="tests"]]
	{@first(test)@}&nbsp;&nbsp;{#second(test)#}&nbsp;&nbsp;{#third(test)#}<br><br>
	[[/foreach]]
  
As I added more to the code, I would use `s_test_case(sa,ta)` with `sa` being the function application and `ta` being the expected output. This was a really useful way to build test cases into the development process.

3. Test cases and documentation

Test cases are important to ensure that small edits to this open source software don't have unintended effects. These are important for the main codebase of STACK, but in the event that a new version of STACK would break existing questions, users can anticipate this before the upgrade. The `stack_include` feature is version-independent, so any changes made will _immediately_ impact all users, and so test cases are even more important (It's worth noting that "immediately" refers to newly compiled questions, so questions sitting unedited in quizzes will be fine, but caution is still required). 

At present, test cases are kept separately from the main function. For example, I am currently maintaining both `linearalgebra.mac` and `linearalgebra_test.mac`, the latter of which hosts the test cases. The test cases should all be of the form `s_test_case(test case, expected output)`. For example, one of my functions has the following set of test cases: 

	s_test_case(diagmatrix_like([1,1,1],3,3),ident(3));
	s_test_case(diagmatrix_like([1,2,3],3,4),matrix([1,0,0,0],[0,2,0,0],[0,0,3,0]));
	s_test_case(diagmatrix_like([1,2,3],4,3),matrix([1,0,0],[0,2,0],[0,0,3],[0,0,0]));
	s_test_case(diagmatrix_like([1,2,3],4,4),matrix([1,0,0,0],[0,2,0,0],[0,0,3,0],[0,0,0,0]));
	s_test_case(diagmatrix_like([1,2,3],2,3),matrix([1,0,0],[0,2,0]));
	s_test_case(diagmatrix_like([1,2,3],3,2),matrix([1,0],[0,2],[0,0]));
	
I chose those test cases to cover all of the possible cases I could think of: a square matrix with a full diagonal, tall and squat matrices with full diagonals, a too-short list of given diagonal entries, and over-full lists of diagonal entries with rectangular matrices. 

Documentation should be in the main file. This is an ongoing project, so the format is not finalised. At present, I have been following the format of

	/**
	 * Description of function
	 * 
	 * @param[data type] parameter_1_name Description of parameter
	 * @param[data type] parameter_2_name Description of parameter
	 * @return[data type] Description of returned value
	 */
	 
One specific example is shown below for a function that takes a matrix and vector and returns the general solution:

	/** 
	 * Solve the matrix equation Ax = b given matrix A and column vector (or list) b.
	 * Optionally will find a least squares solution
	 * Always returns a general solution if one exists, even in the least squares case
	 * If a single solution is required, use pseudoinverse(A) . b instead.
	 * 
	 * @param[matrix] A An mxn matrix
	 * @param[matrix] b A mx1 matrix (or a list with m entries)
	 * @param[boolean] lstsq Optional: if given true then a least squares solution will be obtained. If false or omitted, only exact solutions obtained.
	 * @return[matrix] The general solution to Ax = b. If no solution exists and lstsq is not true, then matrix([]) is returned.
	 */
	mat_solve(A,b,[lstsq]):= block([m,n,vars,eqns,sol],
		... function here ...
	);
	
4. The Surprises and Pitfalls

The inclusion should work for `simp:false` and `simp:true` and return appropriate results in either case. This caused me a few headaches, as I forgot to work with `simp:false` for a large chunk of the original writing process. I only noticed when I went back through to add test cases the first time and realised that everything broke. Some things to watch out for: 

- `makelist` doesn't work in expected ways with `simp:false`. Rather than `expr: makelist(func(i),i,1,n)` you might prefer `expr: map(lambda([ex], func(ex)), ev(makelist(i,i,1,n),simp))`
- For loops don't automatically evaluate the indexing variable, so you might encounter errors when, for example, `i = 1+1` instead of the expected `i=2`. To avoid this, you can simply include `i: ev(i, simp)` at the beginning of the loop.
- Some functions, particularly predicate functions, require their inputs to be simplified before they work. For example, I found that `zeromatrixp(apply(matrix,[[0,0,0]]))` was returning `false` even though `apply(matrix,[[0,0,0]])` will correctly return a matrix of zeros. I fixed this with `zeromatrixp(ev(apply(matrix,[[0,0,0]]),simp))`. 
