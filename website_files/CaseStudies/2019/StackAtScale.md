---
template: casestudy.html

title: "STACK at Scale: The Open University"
authors: Tim Lowe, School of Mathematics and Statistics, Tim Hunt, Information Technology.

shortdescription: The Open University uses STACK for large-scale online courses.
cardimage: OU_thumbnail.png
cardimagealt: A STACK question on finding the magnitude of friction force on a box resting on an incline.
---

# STACK at Scale: The Open University
<img class="figure-img img-fluid float-right img-logo" src="../Images/OU_logo.png" alt="Open University logo">

### The Open University.
Tim Lowe, School of Mathematics and Statistics,
Tim Hunt, Information Technology.

### Introduction
<div class="float-right img-tall">
<figure class="figure">
<img class="figure-img img-fluid" src="../Images/OU_1.jpg" alt="The Open University.">
  <figcaption class="figure-caption">Figure: The Open University.
</figcaption>
</figure></div>
The Open University is the UK’s largest academic institution. In 2017/18 there were approximately 175,000 students studying with the University, mainly part time, making approximately 65,000 full-time equivalent students. Students combine their study with work, family, caring and other responsibilities. Students study from home, at a distance, guided by the University’s Moodle-based VLE and using a combination of online and printed materials. Students are supported by a tutor who provides individual support to a group of typically 20 students and usually offers a combination of face-to-face and online tutorial support. 

The School of Mathematics and Statistics offers a number of undergraduate qualifications in mathematics (with a total intake of approximately 1300 each year) and a taught MSc, which is the largest such course in the UK. In addition, students throughout the University can take one or more mathematics modules in support of their main subject of study. There are approximately 13,000 student-module combinations within mathematics and statistics each year.

STACK is an ideal tool to support the distance-learning of mathematics, as it enables students to practice key techniques from home whilst receiving immediate feedback on their answers. Students can attempt different randomised variants of questions to support their learning and development. 


### Execution
<div class="float-right img-tall">
<figure class="figure">
<img class="figure-img img-fluid" src="../Images/OU_4_large.png" alt="A STACK question on finding the magnitude of friction force on a box resting on an incline.">
  <figcaption class="figure-caption">Figure: A typical OU STACK question.
</figcaption>
</figure></div>

STACK was first used in the curriculum in 2014 with the launch of a new introductory calculus module: MST124 "Essential Mathematics I", which is currently studied by approximately 2,800 students per year. Since then, STACK has been taken up by many modules at all levels. The main use is for formative “practice quizzes” allowing students to practice the important techniques taught. At lower levels, it is also used for summative assignments, which both encourage students to use the formative quizzes to prepare for the assignment and practice their mathematics, and help students keep on pace with their study by providing deadlines. At the postgraduate level, a series of linked-STACK questions has been developed to guide students through more complex mathematical arguments in the calculus of variations [1].

The School of Mathematics and Statistics have been supporting colleagues in the School of Engineering and Innovation who use STACK to support their teaching of mathematically-based topics. The School is also using STACK to support students between formal module study, and in preparation for study as a key component of online “Revise and Refresh” support materials. 

STACK is currently used in at least 10 modules providing at total of 330 CATS credits and reaching over 6,500 students annually. Over one million STACK questions are answered by students each year, which is approximately 18% of all quiz questions answered by OU students.

### Server

STACK is supported by the University Information Technology department as part of the Moodle installation. This consists of 11 load-shared Apache Web Servers supported by 2 MaximaPool servers to service the use of Maxima by STACK. Despite the high level of use, STACK has been robust in performance with no unplanned service outages during the period of use. All question authors are strongly encouraged to include *Question tests* as part of each STACK question, which helps ensure that the integrity of the questions is maintained over time. Before each STACK upgrade, IT checks the question tests of all STACK questions to ensure none are affected by the upgrade. If any tests fail, the questions are corrected by the appropriate module staff before the upgrade is applied to the live system.

### Feedback

Students’ engagement with the quizzes is often demonstrated by comments posted in online forums, for example questioning details of the worked solution provided. Students are often not content with just being able to answer every question in a quiz, but continue to try to correctly answer the quiz in the minimum time.

Student feedback on the use of STACK quizzes has been positive, with many choosing to praise them in the unprompted open comments of the university module feedback survey. Conversely, negative comments are received where a module does not have STACK quizzes. Typical student comments include the following:

- I do value the practice quizzes because you do get practice, the feedback explanations are very good and detailed.
- [I] have done two runs of the practice quiz which has made a big difference for me and will become something I will be doing much more as [it] helps so much.
- I have been doing the practice quiz every morning now for 2 weeks ... I managed 100% on one of the quizzes and over 90% now on all of them so my confidence level is going up!
- The practice quizzes were excellent and I think absolutely essential for consolidating your understanding of the subject.

### What's Next

The School currently plans to introduce STACK quizzes into additional modules as they are updated. Future plans include extending the use of STACK to further, higher level modules and to expand the use of STACK to support students in checking their preparedness for the study of various modules.

### References

[1] T. W. Lowe and B. M. Mestel. *Using STACK to support student learning at masters level: a case study.* Teaching Mathematics and its Applications: An International Journal of the IMA, 2019.
