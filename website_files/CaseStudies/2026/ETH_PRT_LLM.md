---
template: casestudy.html

title: A workflow for generating PRTs for summative assessment using an LLM
authors: Jeremy Feusi, Andreas Steiger, ETH Zürich
shortdescription: This case study describes a possible workflow for creating the PRTs using an LLM and the considerations that went into the process
cardimage: ETH-LLM-long-prt.png
cardimagealt: An LLM-generated potential response tree.
---

# A workflow for generating PRTs for summative assessment using an LLM

*Jeremy Feusi, Andreas Steiger, ETH Zürich*

---

## Introduction: Grading with STACK

STACK was originally designed to support formative assessment. Over the past few years, there has been an increased interest in using STACK in summative assessment. Examiners like the scalability, the quick availability of results and the deterministic outcomes when using STACK in examination situations.

One of the major design features of STACK is its PRT (Potential Response Tree) system, which allows instructors to carefully program a fine-grained decision tree for the evaluation of a student answer to a task. A PRT converts a student answer into a feedback message and a numerical score.

For examinations, a guiding principle for designing the PRTs for a task is to imitate the classical, manual evaluation process. In that setting, examiners write a detailed grading scheme, carefully explaining the score any given answer should receive. A PRT is then a programmatic way of describing the grading scheme. The conversion is rather natural, yet it is a programming task which can be cumbersome.

However, solving tasks, writing answers and evaluating them are all human tasks. All of them naturally have to deal with ambiguity. Graders constantly have to decide if an answer matches a given criteria to receive the corresponding score. A serious attempt at algorithmic grading using STACK must consider these ambiguities and carefully examine if some valuable answers have been awarded an erroneously too low score.

In this case study, we describe a scenario in which an LLM programme the PRTs for STACK questions in a summative exam. The focus of this study is to accurately describe the workflow behind such a process and the considerations that went into it. This study does not contain at a detailed comparison or analysis of the actual grading results, however.

## A concrete scenario with manual grading

The authors of this case study are the main assistant and the responsible lecturer and examiner for two large courses: Analysis I (single variable calculus up to power series) and Analysis II (multivariate calculus, vector calculus, ODEs) for mechanical engineering and materials science students at ETH Zürich. For both courses, two exams each take place every year; one in the semester break right after the course, and one in the break one term later. Currently, the first exam for each course is usually taken by 700-800 students, whereas the second exam is taken by 70-120 students. Each of these exams contains 5 STACK tasks, often with multiple parts. They may contain randomness, yet with generally only up to 4 deployed variants for fairness reasons.

For the exam itself, only the basic PRTs comparing the student answer with the teacher answer are programmed. When designing the tasks we do have ideas what to give partial credit for, but it is only after the exam that we implement detailed PRTs. For that, we sift through the given answers by deployed variant using the "Analyze responses" page in the question dashboard. That process allows us to find more ways student answers are wrong than we could anticipate, and it also allows us to spot common typographical mistakes. PRTs are then programmed, the task regraded, and this process is iterated until the remaining special cases are easier to grade manually in Moodle. 

The described grading procedure takes about 4 hours per task on average for the larger exams and about 3 hours on average for smaller exams. Usually one task is graded over several sessions, as the concentration required to spot sensible wrong answers is high.

## Generating PRTs using an LLM

After the exam in January 2026, we tested how well an LLM can recreate the PRT of a STACK question given a detailed grading scheme and the actual student responses. An LLM was thus given a STACK question in the form of a MoodleXML file, containing the grading scheme as part of the general feedback section, a CSV file containing the student answers. It was prompted to return a MoodleXML file with the same question, but updated PRTs according to the grading scheme. In a copy of the original exam Moodle course, this MoodleXML file was then imported as a new version of the original question (using the `qbank_importasversion` plugin, which is a required dependency of STACK as of version 4.12.0 from April 2026), and the question was re-graded.

A comparison between the hand-written PRTs and the LLM-generated ones showed that they produced virtually the same scoring outcome. We noticed minor differences in handling certain edge cases ("is that a typo or a mistake?"), but these differences were on the level which we would also expect from two different humans implementing the same grading scheme. Especially for larger trees with more than 10 nodes, the LLM-generated PRTs were more detailed and contained better question note feedback. We suspect that human PRT authors become less careful as they keep spending time writing a PRT for the same problem.

<div class="float-none img-middle">
    <figure class="figure">
        <img class="figure-img img-fluid" src="../Images/ETH-LLM-answer-normalizing.png" alt="LLM-generated code to normalize students' answers" style="width:95%;">
        <figcaption class="figure-caption">Figure: code the LLM wrote to normalize student answers. Students sometimes write single-valued lists instead of variables and the other way around. We argue that we want to get close to human grading, so typing the "correct" answer in the wrong way should not be punished (severely).</figcaption>
    </figure>
</div>

## Changing to LLM-first grading

For the large exams in Summer 2026, we thus changed the grading workflow to LLM-first with an experienced human in the loop and a refined workflow.

Again, an LLM was given a MoodleXML file of a STACK problem containing a grading scheme and a list of anonymized student answers. It was prompted to classify common mistakes and to spot possible typographical errors. We reviewed these lists reported by the model and gave instructions how to handle them. In most cases we were in agreement with its decisions, as it recognized students had done a mistake anticipated in our grading scheme and suggested a corresponding decision. The LLM did also find mistakes we did not think of beforehand and assigned a score. As expected in these cases we had the highest amount of disagreement with the suggestions, but still at a low rate.

The second prompt then asked the LLM to implement the PRTs according to the grading scheme and the decisions taken. A special focus was put on the handling of follow-up errors, particularly when some answers were left blank. As in the first recreation experiment, the resulting MoodleXML file was then imported as a new question, followed by a regrading of the task. The examiner reviewed the outcome carefully using the responses analysis page, making sure all student answers got identified and scored correctly. Finally, answers causing syntax or runtime errors were manually graded.

## Outcome

In our experience, the described process is robust and efficient. The intermediate step of reviewing mistakes the LLM had found was helpful for quality assurance and for finding more scoring paths without having to analyze the actual answers ourselves. All PRTs written by the LLM worked as intended. As examiners, we could now spend our time discussing the scores of given answers instead of tediously writing code and making sure that the scoring was correct. The whole process was thus now much more educational rather than technical.

<div class="float-none img-middle">
    <figure class="figure">
        <img class="figure-img img-fluid" src="../Images/ETH-LLM-long-prt.png" alt="LLM-generated PRTs with 13 nodes" style="width:95%;">
        <figcaption class="figure-caption">Figure: one of the more complex LLM-generated PRTs with 13 nodes. Note that the LLM made use of some of the more subtle features like node names or silencing the default feedback of an answer test.</figcaption>
    </figure>
</div>

On average we estimate that it took us a little more than one hour to grade a single STACK problem using this process. About 35-45 minutes were spent by the person prompting the LLM and preparing the decision meeting, and the examiner spent about 25-35 minutes for the decision meeting and for reviewing the final grades. Compared to the original 3-4 hours using manual grading and programming, we saved about 65% of working hours and achieved a better quality grading as judged by ourselves.

## Remarks

For this case study, GPT-5.6 Sol with training disabled was used.
