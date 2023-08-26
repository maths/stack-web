---
template: casestudy.html

title: "Employ.Ed STACK Internship Programme"
authors: Gavin McWhinnie, Maria Christodoulidou
shortdescription: This case study details the work and insights gained from a STACK-based internship during the summer of 2023 at the University of Edinburgh.
cardimage: Probability_Question.png
cardimagealt: Figure showing a STACK question on Probability.
---

# The Employ.Ed STACK Internship Programme: Impact and Reflections

#### University of Edinburgh

Konstantina Zerva, Gavin McWhinnie, Maria Christodoulidou

<img class="figure-img img-fluid img-logo" src="../../2019/Images/Edinburgh_logo_stacked.png" alt="University of Edinburgh logo">


## Introduction:

This case study details the work and insights gained from a STACK-based internship during the summer of 2023 at the University of Edinburgh and reflects upon the unique experience of being a dedicated STACK intern. The internship was facilitated by the Employ.Ed on-campus internship program and ran for 12 weeks from June through August. The main aim of the internship was to contribute to the ongoing work in the School of Mathematics of creating and maintaining STACK materials for various undergraduate courses and to further contribute to the ongoing project of translating the HELM workbooks to STACK.

## Training

At the start of this internship, training began with an introductory presentation by Konstantina Zerva, followed by self-study using the materials available online (namely the [Quick Start Guide](https://docs.stack-assessment.org/en/AbInitio/) and the [Documentation](https://docs.stack-assessment.org/en/)). After being introduced to STACK, the significant range and depth of features available can mean that the training needed to become a proficient question author can pose quite a challenge. Especially during this 12-week internship, it was important to quickly get a strong grasp of the basics. Training continued through the first week with small introductory tasks, such as reviewing and implementing minor modifications to existing STACK question banks.

From our experience, the most effective approach to mastering STACK is learning directly from experienced STACK users themselves. Throughout the course of the internship, we were lucky enough to receive guidance and input from multiple STACK professionals working at the university. As an alternative, however, anyone is welcome to join the STACK community on STACK’s [free online chat platform](https://stack-assessment.zulipchat.com/).

## Work and Impact:

#### Undergraduate Courses:

Throughout the internship, close collaboration was established with course organisers to develop and refine STACK-based materials for various undergraduate courses within the School of Mathematics. Quality checks, question tidying up and revisions were carried out on the materials designed for the different courses, including:

- Several Variable Calculus and Differential Equations (MATH08063)
- Probability (MATH08066)
- Functional Analysis (MATH11135)
- Mathematical Biology (MATH10013)
- Statistics (Year 2) (MATH08051)

In particular, new material was created for the 2nd year Probability course, with an example question shown below.

<div class="float-none img-middle">
<figure class="figure">
<img class="figure-img img-fluid" src="../Images/Probability_Question.png" alt="Figure showing a STACK question on Probability.">
<figcaption class="figure-caption">
<center><i>Probability STACK Question.</i> Marking is correct for any choice of symbols used for the sample space, \(\Omega\).</center>
</figcaption>
</figure>
</div>

#### HELM

Furthermore, an active contribution was made to the ongoing project of translating the HELM workbooks into STACK format (see this [case study](../2021/HELM.md)). This included the incorporation of interactive randomised STACK questions and the addition of comprehensive worked solutions for practice exercises. HELM workbooks 19, 20, 23 and 25 were converted and are to soon be tested and put into use by first and second year engineering mathematics courses at the university.

<div class="float-none img-middle">
<figure class="figure">
<img class="figure-img img-fluid" src="../Images/HELM_Question.png" alt="Figure showing a STACK question based of a HELM workbook.">
<figcaption class="figure-caption">
<center><i>HELM task as a STACK question.</i> Converted from HELM Workbook 20.1 - Casual Functions.</center>
</figcaption>
</figure>
</div>

#### Uploading to Moodle and latex conversion

For the 4th year course Functional Analysis (MATH11135), there was a need to convert LaTeX course notes to html and then upload this to Moodle so that it could be used in conjugation with STACK to create interactive online notes. (For a previous example of this, see the use of STACK in [Honours Complex Variables](../2022/HonoursComplexVariables.md).) This process lends itself to being fully automated, which can be done with a fairly small Python program. Specific problems (with LaTeX to html conversion using Pandoc) encountered whilst developing this program led to the creation of [pandoc-math](https://gavinmcwhinnie.github.io/pandoc-math/), a Pandoc filter for converting mathematics course notes to html ([GitHub repository](https://github.com/GavinMcWhinnie/pandoc-math)). By using this tool, the resulting html can then uploaded to Moodle either manually or via a Python script to parse the html and convert it into [Moodle XML](https://docs.moodle.org/402/en/Moodle_XML_format).

#### AuthOMath LTTA:
One of the highlights of the internship was our participation in a 4-day Erasmus+ Meeting at Johannes Kepler University in Linz, Austria. The meeting had a primary focus on the integration of STACK and GeoGebra, leveraging their combined strengths while also emphasising effective didactics in mathematics education.

During the meeting, mathematics and teaching students from various European universities came together to combine their skills and collaborate on the creation of digital tasks. These tasks incorporated interactive STACK questions along with GeoGebra applets, enhancing the learning experience. At the conclusion of the conference, each team had the opportunity to present their collaborative work to professors and project leaders, showcasing their innovative ideas and solutions.

A report of the conference is published [here](https://www.authomath.org/?page_id=433).


## Reflection

The role of a dedicated STACK intern is undeniably an interesting and enjoyable experience. It's been fulfilling to belong to a global community of users and developers and a privilege to create new high-quality materials for future mathematics students. This section highlights some of the positives, interesting aspects and difficulties of this experience:

- STACK interns can greatly help in creating online content for undergraduate courses and are certainly a worthwhile investment! Provided with good training, interns can give attention to creating engaging, high-quality, and robust STACK questions, a task that academics and course organisers might not have the time or capacity to undertake. Often STACK interns are students themselves who have first-hand experience as STACK users, meaning they have their own insight into what is useful and what might be less engaging or even potentially frustrating for students.

- One of the most noticeable difficulties in writing STACK questions for undergraduate STEM courses as a STACK intern or similar, is that there is difficult balance between having the technical knowledge of what is possible in STACK and the pedagogical knowledge and teaching experience needed to create good questions. Often this means there are two people involved in every STACK question: an academic or teaching staff member who writes questions they believe will be possible to implement in STACK, and a teaching assistant or intern who actually creates the question. This can lead to the STACK author on the technical side receiving an (almost) impossible task or creating questions which are technically correct but are flawed from a teaching standpoint.

- STACK question authors tend to have their own approach to writing questions, with their own styles and quirks. This is likely due to the wide range and depth of features STACK has, allowing users to use what features suit them best. However, this can make collaboration difficult and reviewing other author's questions occasionally tricky. A potential solution for this issue is given under [authoring collaboratively](https://docs.stack-assessment.org/en/Authoring/Workflow/#authoring-collaboratively), on the page describing "authoring workflow" in the documentation.
