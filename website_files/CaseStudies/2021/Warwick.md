# Using STACK in Real Analysis

#### University of Warwick

Siri Chongchitnan

Context
--------

The onset of the Covid-19 pandemic in 2020 urgently forced us to rethink how we assess mathematics at university level. In the summer of 2020, we turned to STACK with the goal of creating self-assessed online quizzes in real analysis that would supplement traditional problem sheets. We wanted to see how far STACK could be used in a heavily proof-based pure mathematics undergraduate course. 

Time line
---------

* Coding phase: June - August 2020
* Testing phase: September - December 2020
* Launch: January to March 2021
* Feedback and data analysis: April 2021 

We worked on the module Analysis II - a core first-year module for maths undergraduates at Warwick. The intake was about 400. This is second course in real analysis follows from the foundation in numbers, sequences and series in Analysis I. Teaching materials, including online quizzes, were to be created on the Moodle virtual learning environment. Here is the weekly scope of the course given over 10 weeks. 

1. \(\epsilon-\delta\) definition of continuity
2. Sequential definition of continuity
3. Continuity on an interval, Intermediate Value Theorem 
4. Limits
5. Inverse Function Theorem
6. Differentiation, Carathéodory’s theorem
7. Mean Value Theorem, L’Hôpital’s Rule
8. Taylor’s Theorem, Lagrange form of the remainder
9. Radius of convergence 
10. Differentiation of power series 

Our goal was to create one set of STACK assessment for each week’s material. Each set should take around 30-40 minutes to complete. 

Execution
---------

In the previous year, students had to submit problem sheets weekly, However, Covid-related uncertainties meant that we had to cut this number down to only 4 problem sheets, which counted for 10% of the final grade. 

To supplement the above, we created 11 sets of STACK quizzes, two of which were not counted (one on syntax training, and one on Analysis I revision). They were practice quizzes, in the sense that students could do them an unlimited number of times before the deadline, each attempt building on the last. Each quiz had a pass mark of around 85% (not uniform across the quizzes). Passing 6 out of 9 quizzes gave the student a flat 5% for the module. 

We used STACK to create over 40 multi-part questions over 4 weeks. We are grateful for George Kinnear’s talk on JSXGraph at previous STACK conferences, and to Chris Sangwin and Robbie Bickerton, both of whom gave us inspirations to apply their scaffolding and proof-comprehension techniques to Analysis II. 

We used STACK in conjunction with Moodle-type questions (STACK integrated seamlessly with our Moodle virtual learning environment). We particularly found JSXGraph helpful in creating interactive graphics that visualise and explain tricky analysis concepts better than static media could. Highlights include the questions shown in these figures.

<div class="float-none img-middle">
<figure class="figure">
<img class="figure-img img-fluid" src="../Images/War-Fig1.png" alt="">
  <figcaption class="figure-caption">
  ε-δ definition of continuity visualised with JSXgraph and slider.
  </figcaption>
</figure></div>

<div class="float-none img-middle">
<figure class="figure">
<img class="figure-img img-fluid" src="../Images/War-Fig2.png" alt="">
  <figcaption class="figure-caption">
  Counterexamples in analysis can be visualised with JSXgraph’s zoom function (e.g. to explore local behaviour of a function).
  </figcaption>
</figure></div>

<div class="float-none img-middle">
<figure class="figure">
<img class="figure-img img-fluid" src="../Images/War-Fig3a.png" alt="">
<img class="figure-img img-fluid" src="../Images/War-Fig3b.png" alt="">
  <figcaption class="figure-caption">
  A proof of the Chain Rule is implemented using Moodle’s ‘drag and drop’ question type together with STACK-coded scaffolded proof.
  </figcaption>
</figure></div>


Results
-------

We set the pass mark for each assignment quite high (>80%) but most students achieved >90%. On average students submitted between 2 and 3 attempts per quiz, with over 90% of students passing all quizzes. These engagement statistics are all encouraging.


Student feedback
----------------

When asked: “Apart from the lecture notes and videos, what other resources are useful for the understanding of Analysis II?”, we found that almost 90% of respondents rated the quizzes as useful. As many students rated the problem sheets as useful. This is evidence that when implemented properly, the learning gains from STACK quizzes are comparable to those of traditional pen-and-paper assignments. 

When asked to “Name one thing about the module which has had the most impact on your learning in this course”, a number of students thought the STACK quizzes were the most impactful element of the course. Some comments include: 

“The quizzes were helpful and the infinite attempts ensured that I did not feel pressured while doing them, allowing me to focus on understanding the content." 

“The quizzes have been a very useful interactive learning tool." 

“The alternating assessment format between quizzes and written assignments is nice and helped reduce stress." 

Summary
-------

STACK can be successfully applied to a wide range of mathematics content, including pure mathematics at university level as our work has demonstrated. We have shown that it is possible to turn proofs in existing lecture notes and problem sheets into interactive online quizzes, even in pure proof-heavy courses like ours. The interactivity in the STACK quizzes also meant that students understood the proofs much more clearly than when the proofs were recited during lectures.

Although STACK was the primary tool for question creation, we also found it useful to mix STACK with other native Moodle-type questions for a varied diet. Creating questions on STACK is an ideal co-creation project which can be done as a summer internship. There are long-term benefits for everyone involved.

All in all, we found STACK to be highly flexible and adaptable to help us achieve our teaching-and-learning goals. At Warwick we are continuing to expand the use of STACK to other maths modules. 

<nav aria-label="...">
  <ul class="pagination pagination-lg justify-content-center" style="margin-top:2em">
    <li class="page-item"><a href="../HELM" class="page-link" >Translating the HELM workbooks to STACK&nbsp;<i class="fa fa-arrow-right"></i></a></li>
  </ul>
</nav>