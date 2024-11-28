---
template: casestudy.html
title: Integrating STACK at the University of Trieste, Italy.
authors: Daniel Doz, Zevick Otieno Juma, Motognon Wastalas D. Dogbalou, Danilo Lewański.
shortdescription: A reflection on the analysis of STACK usage in continous assessment, exam results and student attitudes on the first STACK Implementation in the Italian Higher Education.
cardimage: UniTS-cover-page.jpg
cardimagealt: 
---

# Integrating STACK at the University of Trieste, Italy.
Daniel Doz, Zevick Otieno Juma, Motognon Wastalas D. Dogbalou, Danilo Lewański

### Background
The University of Trieste (UniTS) is a prominent player in Italy’s academic landscape, recognised for its efforts to align with contemporary educational trends in education. This is despite the largely traditional nature of Italy’s education system ( for more details [click here](https://www.research.unipd.it/handle/11577/3508021)).
In Italy, university assessments are traditionally summative, relying heavily on high-stakes, end-of-semester exams to measure student understanding. This model places emphasis on theoretical knowledge assessed at the end of the semester, often lacking interim feedback that could aid in bridging knowledge gaps as they arise. Although effective in certain respects, this system has significant limitations, particularly in its lack of continuous feedback mechanisms that could help students identify and address learning gaps throughout the semester. By regulation, lecturers are not obligated to administer continuous assessments during the semester. 
In response to this, UniTS launched a pilot project to integrate STACK, an open-source assessment tool designed for STEM subjects, starting with the Department of Mathematics, Informatics, and Geological Sciences (MIGe). Developed through a partnership with [IDEMS International](https://www.idems.international/), UK-based social enterprise focused on supporting education and sustainable development projects worldwide. 
This was done during the 2022/23 academic year, starting with a Probability and Statistics course and later scaling it up to Linear Algebra in the subsequent academic year. STACK was selected due to its automated, real-time feedback, allowing students to learn from their mistakes and progress through iterative practice. 

<div class="float-none img-middle">
    <figure class="figure">
        <img class="figure-img img-fluid" src="../Images/UniTS-cover-page.jpg" alt="University of Trieste, Piazzale Europa, 1, 34127 Trieste TS, Italy ">
        <figcaption class="figure-caption">University of Trieste, Piazzale Europa, 1, 34127 Trieste TS, Italy</figcaption>
    </figure>
</div>

The Italian Government, through its National Recovery and Resilience Plan [PNRR - Piano Nazionale di Ripresa e Resilienza](https://www.italiadomani.gov.it/content/sogei-ng/it/it/home.html), which calls for innovation and digitalisation in education, provided financial support accross various learning institutions in Italy, which allowed UniTS to sponsor two PhD research positions focused on STACK integration and expand collaborative opportunities with institutions abroad, mostly located in Africa.

This case study outlines the progress and insights gained from implementing STACK at UniTS to guide similar educational advancements in Italy and beyond. The project’s primary goal is to modernise assessment methods in STEM, providing students with more frequent, individualised feedback and aligning assessment practices with UniTS’s commitment to sustainable educational improvement.


### Overview of Assessment Practices in Italian Universities
In the Italian higher education system, continuous assessment practices are generally absent in STEM subjects. Instead, courses rely on multiple written exam sessions, with each course offering 6 or 7 sessions per year. Students have considerable flexibility: they can attend as many sessions as they choose, reject passing grades, and retake exams in subsequent years without any time constraints.

The  assessments typically includes the following key phases:
1. Written Exam – Students begin with a written exam, which requires them to apply their knowledge to solve practical problems. Only those who achieve a sufficient score in this initial phase are eligible to proceed to the final assessment stage.  
2. Oral Exam – In this phase, students participate in an oral examination, where they articulate and defend their understanding of the subject through discussion with lecturers. This stage assesses not only the students' depth of knowledge but also their ability to communicate complex ideas effectively.

The grading system in Italy ranges from 18/30, the minimum passing score, to 30/30, with “30 e lode” (cum laude, occasionally noted as 31/30) for exceptional performance. Continuous assessment, while increasingly valued, remains optional and is typically up to individual instructors.

In the 2023/2024 academic year, STACK was integrated into three courses at the University of Trieste. The first subject, Probability and Statistics, was taught in a course that had used STACK in the previous year. The second subject, Linear Algebra, was divided into Course A and Course B, which followed identical curricula but were taught by different lecturers. STACK was used to support with continous assessment, give feedback to students, and even running exams in the Probability and Statistics course.
Only *mastery quizzes* were implemented—these are specialised quizzes designed to help students achieve a deep understanding of key concepts, with only the highest grade among all attempts taken into account. The quizzes remained open throughout the semester until the first exam, allowing students ample time to practice and master the material at their own pace.

### Implementation Phases

1. Content development. The initial introduction of STACK at UniTS was supported by IDEMS International, which focused on providing STACK content to instructors.
   
2. Customising Questions. The next step was to tailor the questions to fit the specific learning objectives of each course. Instructors, with IDEMS support, reviewed resources from the IDEMS open question bank and created new questions where necessary. IDEMS also provided access to open-source resources like the African STACK Open Question Bank to enrich the question pool.

3. Engaging Students. To help students get comfortable with STACK, instructors provided informal onboarding sessions within each course. These sessions included tutorials on navigating quizzes, using feedback effectively, and retaking quizzes to reinforce learning. Initially, students were uncertain about the option for multiple quiz attempts, but they quickly adapted and came to value the immediate, constructive feedback provided.


##### Challenges and Solutions during Integration:

The integration of STACK at UniTS came with a few key challenges:

1. Technical Issues. There were initial technical difficulties with STACK’s server integration, but UniTS supported by IDEMS resolved these issues. Additionally, the lead instructor addressed technical issues as they arose throughout the course, ensuring smooth ongoing functionality.

2. Question Development. Crafting effective questions that met STACK’s technical requirements was initially time-consuming. However, by using pre-existing materials from the African Question Bank and the HELM Project, instructors were able to expedite the question development process, tailoring questions to fit course objectives more efficiently.


### Outcome
To evaluate STACK’s impact on student performance, we analysed engagement data from three courses at UniTS: two Linear Algebra courses (Course A and Course B) and one Probability and Statistics course. This analysis aimed to understand how varying levels of STACK engagement influenced student outcomes.
In Course A of Linear Algebra, students had access to all STACK quizzes and completed each one throughout the semester, showing consistent engagement. In contrast, Course B students attempted only 6 out of the 10 available quizzes, despite following an identical curriculum and sitting for the same final exams as Course A. This variance in engagement levels between the two otherwise identical courses provided a unique opportunity to explore how consistent quiz participation might affect exam performance and mastery of course content.
<div style="display: flex; justify-content: space-between;">
    <!-- Left Plot -->
    <figure class="figure" style="width: 48%;">
        <img class="figure-img img-fluid" src="../Images/Lin-Alg-courseA.JPG" alt="Student Engagement with STACK, Course A">
        <figcaption class="figure-caption">Student Engagement with STACK, Course A</figcaption>
    </figure>

    <!-- Right Plot -->
    <figure class="figure" style="width: 48%;">
        <img class="figure-img img-fluid" src="../Images/Lin-Alg-courseB.JPG" alt="Student Engagement with STACK, Course B">
        <figcaption class="figure-caption">Student Engagement with STACK, Course B </figcaption>
    </figure>
</div>
In the Probability and Statistics course, STACK had been used previously, and this time the new student cohort also engaged with all available quizzes, completing at least one attempt per quiz. Therefore, we did not analyse pre- and post-STACK implementation for this course as we did for the two Linear Algebra courses. Since this was the second cohort to use STACK, there was no baseline data without STACK for comparison. Instead, our focus here was on evaluating overall performance trends with STACK already in place.
<br>
<p></p>
In comparing student performance in the two Linear Algebra courses (A and B), there were notable differences post-STACK integration. For Course A, the analysis showed a significant improvement in student performance after integrating STACK. The Mann-Whitney U test indicated a significant difference in grade distributions between the pre- and post-STACK groups, suggesting that STACK’s continuous assessment and feedback likely contributed to improved outcomes. For Course B, however, the results did not show a statistically significant change in performance post-STACK integration, as the Mann-Whitney U test returned a non-significant result. 
<br>
<br>
<br>

<div style="display: flex; justify-content: space-between; align-items: center;">
    <!-- Left Plot -->
    <figure class="figure" style="width: 48%; margin: 0;">
        <img class="figure-img img-fluid" style="width: 100%; height: auto;" src="../Images/Pre-Post-STACK-courseA.PNG" alt="Student Engagement with STACK, Course A">
        <figcaption class="figure-caption" style="text-align: center;"> Pre-Post STACK Analysis, Course A</figcaption>
    </figure>

    <!-- Right Plot -->
    <figure class="figure" style="width: 46%; margin: 0;">
        <img class="figure-img img-fluid" style="width: 100%; height: auto;" src="../Images/Pre-Post-STACK-courseB.PNG" alt="Student Engagement with STACK, Course B">
        <figcaption class="figure-caption" style="text-align: center;">Pre-Post STACK Analysis, Course B </figcaption>
    </figure>
</div>
<br>
While the results suggest a positive impact of STACK, we recognise that correlation does not equal causation. The improvement in performance could partly stem from factors like individual motivation or external influences. We discuss these considerations and potential limitations in detail in a separate research paper. That paper also presents insights from a K-means classification analysis. This analysis showed that students with steady engagement tend to achieve moderate performance and are more often female. In contrast, students with irregular study habits span all performance levels and are more commonly male.


### What Students Say About STACK

To gather insights into student experiences with STACK, we conducted a qualitative feedback analysis based on a survey administered to students in the Probability and Statistics course. Since this was the second time STACK was used in this course, students were able to provide well-informed feedback on its advantages and challenges. Due to time constraints, similar qualitative feedback was not collected from the two Linear Algebra courses. For more in-depth findings, please refer to our published paper [click here](https://journal.foundae.com/index.php/jasme/article/view/357).

Here are some key themes that emerged from the feedback:

**Instant Feedback and Clarity**  
Many students highlighted the benefit of immediate feedback and clear instructions provided by STACK, which allowed them to quickly assess their understanding.  
> “...Comodo e si ha subito il risultato… mi sono trovato molto bene, soprattutto per studiare. L'esame era chiaro e non necessitava di dover dimostrare i vari passaggi...”  
> _Translation: "...Convenient and you get the result quickly... I found it very good, especially for studying. The exam was clear and didn’t require demonstrating each step."_

**Concerns about Evaluating the Thought Process**  
Some students expressed concerns that STACK emphasised final answers rather than the problem-solving process. They felt this approach might limit their ability to demonstrate comprehensive understanding during exams.  
> “Rimango dell’opinione che gli esami online siano molto più scomodi rispetto a quelli cartacei. Credo che con carta e penna sia più facile valutare il processo risolutivo, mentre su Stack viene preso in considerazione solo il risultato finale.”  
> _Translation: "I remain of the opinion that online exams are less convenient than paper-based ones. With pen and paper, it's easier to assess the solution process, whereas STACK only considers the final answer."_

**Reduction of Exam Anxiety**  
For some students, practicing with STACK before exams helped reduce anxiety, making them more comfortable with digital assessments.  
> “Fare l'esame su STACK non crea ansia e pressione. Avendo fatto molta pratica sulla piattaforma, mi sembra normale fare gli esercizi attraverso lo schermo.”  
> _Translation: "Doing exams on STACK doesn’t create anxiety or pressure. Having practiced a lot on the platform, it feels normal to do exercises on the screen."_

**Concerns over Technical Issues**  
Despite improvements, some students continued to report technical difficulties, including issues with devices and internet access, which occasionally disrupted their assessment experience.

<br>
These insights provide meaningful perspectives on students' experiences with STACK in the Probability and Statistics course, and we believe they likely reflect broader patterns that could apply to students in the two Linear Algebra courses (A & B) as well. 


## Conclusion and Next Steps
The integration of STACK in our Linear Algebra and Statistics courses has yielded promising outcomes, particularly when students fully engage with the quizzes. Moving forward, our efforts will concentrate on refining and expanding our STACK content. We have already developed new STACK questions, including Parsons problems, which will be implemented in the 2024/2025 Linear Algebra course. This will enable us to further assess how we can leverage STACK teaching and learning approaches.


1. **Refinement and Expansion**: We will continue to refine existing STACK questions, particularly those used in Linear Algebra. The newly authored STACK questions will be rolled out in the 2024/2025 semester, allowing us to monitor their impact on student learning outcomes.
   
2. **Collaboration and Research:** We are constantly looking out to establish collaborations through STACK development and research ideas, since we are still new at this, both within Italy and beyond. This will play a vital role in expanding our understanding and ability to carryout research experiments that explore the broader application of STACK in mathematics education. 
   
3. **Integration into More Courses:** We plan to extend STACK to more first-year courses, particularly in disciplines like Physics, where it can significantly aid in students’ comprehension of complex concepts. Expanding STACK's application will not only provide students with a more interactive learning experience but also generate additional data to evaluate its overall effectiveness across different fields.
