# Translating the HELM workbooks to STACK

#### University of Edinburgh

Konstantina Zerva, Ilyas Nicholson, Adrián Doña Mateo

<img class="figure-img img-fluid img-logo" src="../../2019/Images/Edinburgh_logo_stacked.png" alt="University of Edinburgh logo">

## Context

HELM (Helping Engineers Learn Mathematics) is a collection of 50 workbooks developed by five English universities – Loughborough, Hull, Reading, Sunderland and Manchester – that covers the curriculum of first- and second-year mathematics courses for engineering undergraduates. They were designed as flexible learning resources and have been used by an estimate of 12,000 students in 55 UK higher and further education sites [1].

During the ongoing pandemic, as more and more teaching moves to online spaces, the universities of Edinburgh and Loughborough, with the help of several other institutions, have undertaken an effort of translating the HELM materials into Moodle quizzes. These quizzes very much follow the spirit of the original workbooks but provide the added value of interactivity through STACK questions. The result will be released as an Open Educational Resource (OER) on the University of Edinburgh website.

## Execution

So far, about half of the workbooks have been made into Moodle quizzes. Most of the quizzes corresponding to workbooks 1–19 and 35–39  were created during the summer of 2020. These include all the exposition and worked examples as description boxes, and STACK versions of most of the tasks and exercises in each workbook. The materials covered by these quizzes include:

* Basic algebra and elementary functions
* Linear algebra
* Complex numbers
* Calculus and differential equations
* Probability

Feedback from students and lecturers was gathered and acted upon during an extensive revision of the material during the summer of 2021, prior to their public release. This also ensured consistency of style and resulted in the creation of new quizzes and addition of interactive graphs to some questions using JSXGraph.

Currently, there are over 90 quizzes with an average of 6–8 STACK questions each. Most questions have algebraic or numerical inputs, but some are implemented as multiple choice questions, which better suit the nature of the original HELM exercise. Except where it was not possible, question statements were randomised so that students can practice with different versions of the same exercise. Special care was taken to set up relevant tests, to ensure each question is working as expected and to flag issues in future edits.

The following screenshots provide some highlights from the HELM quizzes.

<div class="float-none img-middle">
<figure class="figure">
<img class="figure-img img-fluid" src="../Images/HELM_1.png" alt="An interactive plot in a STACK question about Riemann sums.">
<figcaption class="figure-caption">
<i>Interactive plot with JSXGraph.</i> Students can change the number of rectangles in the left Riemann sum to help them understand the definition of an integral an answer the question.
</figcaption>
</figure>
</div>

<div class="float-none img-middle">
<figure class="figure">
<img class="figure-img img-fluid" src="../Images/HELM_2.png" alt="An interactive plot in a STACK question about the Newton–Raphson method.">
<figcaption class="figure-caption">
<i>Interactive plot with JSXGraph.</i> Students can pan and zoom to explore how the Newton–Raphson method works.
</figcaption>
</figure>
</div>

<div class="float-none img-middle">
<figure class="figure">
<img class="figure-img img-fluid" src="../Images/HELM_3.png" alt="A question that walks the student through the derivation of the vector equation of a plane in 3-dimensional space.">
<figcaption class="figure-caption">
<i>HELM task as a STACK question.</i> Part (b) is assessed with the SysEquiv answer test to allow for different equivalent forms of the correct equation.
</figcaption>
</figure>
</div>

## Putting the quizzes to work

The HELM quizzes have been used in the Engineering Mathematics 1A and 1B (360 students) and Mathematics for Natural Sciences 1A and 1B (130 students) courses at the University of Edinburgh during the 2020/21 academic year. The courses also had online lectures and tutorials, and the HELM quizzes were mostly used for self-study. Each week, 3 or 4 quizzes were made available to students, which would serve as an introduction to the topics to be covered. These were intended as formative feedback and thus did not impact the student’s final grade, but they could be used as practice for the assessed quiz due at the beginning of the following week.

## Student reception

The students’ engagement with the HELM materials was encouraging. In the Engineering Mathematics courses, each quiz typically received between 250 and 300 complete attempts on the week it was released. Feedback was overwhelmingly positive – some students found the HELM quizzes to be the most valuable part of the course. They particularly appreciated being able to work at their own pace and how the quizzes assumed little or no previous knowledge, a trait inherited from the original workbooks. Students also pointed to some areas that needed improvement, such as worked solutions, which were addressed during the 2021 summer revision.

## Conclusion

Bringing new life to the HELM workbooks in the form of STACK quizzes has proved to be a very fruitful activity. The upfront effort to develop STACK questions has added great value to the online learning experience, through question randomisation and immediate feedback. The quizzes created so far cover most of the contents of first year engineering mathematics, applicable also to other subjects, and demonstrate how STACK can be used to teach a wide variety of topics.

The work is nevertheless far from over. Around half of the HELM workbooks are yet to be translated into Moodle. Several other universities are interested in using the existing materials in their courses, and further progress will be made prioritising the workbooks that would be of most use to course organisers. In addition to this, it would be interesting to explore the use of interactive graphs as question inputs, which would enable certain types of ‘sketch’ questions in the original workbooks to be transferred to STACK.

Lastly, the quizzes will soon be released as an OER, which will allow students all over the world to use them for self-study.

## References

[1] <https://www.lboro.ac.uk/departments/mlsc/student-resources/helm-workbooks/past-present-future/>
