---
template: casestudy.html

title: Integrating STACK questions into the PreText textbook authoring system
authors: Georg Osang
shortdescription: We outline early progress of integrating STACK into the PreText authoring system.
cardimage: pretext-preview-cropped.png
cardimagealt: Preview of a PreText textbook featuring a STACK question
--- 

# Integrating STACK questions into the PreText textbook authoring system

Georg Osang

## Abstract

[PreText](https://pretextbook.org/) is a system for authoring textbooks. The main selling point of PreText is that once authored, the textbook can be deployed in many different formats, such as an interactive online textbook (HTML), PDF, EPUB or even Braille. The HTML version can contain various types of interactive content, and various settings allow for easy customization of each of the deployment formats.

We outline our initial and ongoing work to integrate STACK into PreText so that interactive STACK questions can be used inside of PreText textbook, and showcase two particular use cases in Kenya and Ethiopia.

<div class="float-none img-middle">
    <figure class="figure">
        <img class="figure-img img-fluid" src="../Images/pretext-preview.png" alt="Preview of a PreText textbook featuring a STACK question">
        <figcaption class="figure-caption">Preview of a PreText textbook featuring a STACK question</figcaption>
    </figure>
</div>

## Motivation

Until recently, STACK questions had to be served to students within a learning management system (LMS), such as Moodle. Then the development of the STACK API opened up opportunities for using STACK outside such a system, and with the STACK community creating an ever growing collection of learning materials, the possibility of a PreText integration to embed these questions into textbooks was first discussed at the [AIM workshop in Kenya](../2024/AIM_meeting.md) in 2024.

An immediate concrete use case arises from Kenya, where a new competency-based curriculum (CBC) is being introduced in high school and new textbooks have to be written anyway. A STACK-PreText integration would allow us to write interactive text books featuring STACK questions while at the same time offering to automatically typeset these as PDF and thus for print.

Another particular use case arises in Ethiopia, which uses a harmonized undergraduate curriculum, in particular featuring a Basic Maths course that every undergraduate student, regardless of subject, has to take. As digital materials can scale really well in such a setting, we explored the potential of using STACK materials as part of a [STACK workshop](../2023/Bahir_Dar_University_Workshop.md) in 2023 at Bahir Dar University in Ethiopia. STACK practice materials relevant to the Basic Maths course were compiled for lecturers to use with their students, but adoption was low as having to create accounts on the Moodle learning management system presented a significant entrance barrier. 

Deploying these resources as an interactive textbook provides an opportunity to lower this entrance barrier. While this doesn't allow us to record user-specific data, and therefore cannot be used for assessment purposes (unless supplemented by a Moodle course or similar), the initial aim is to give students the opportunity to practice, self-assess and get feedback while going through the course, which interactive textbooks are suitable for and which otherwise is difficult to do.

## Background

Prior to this work, Sam Fearn managed to integrate STACK questions into [dynamic HTML course notes](Dynamic_course_notes.md) using the STACK API. In this setting, the course notes are directly written in HTML (using MathJax for LaTeX rendering) and STACK questions are added via HTML elements. Existing course notes can be converted from LaTeX to HTML using pandoc.

In PreText, content is authored in XML using semantic tags to structure the document such as `<chapter>`, `<section>`, `<example>`, `<exercise>` that are then numbered automatically and converted into the desired output formats according to a configuration. PreText natively supports creating simple [exercises](https://pretextbook.org/doc/guide/html/overview-exercises.html) whose interactive version (HTML) shows a question prompt with input fields to the student and assesses the student's answer when they submit, while in the static version (e.g. PDF) these questions would be rendered like in a classic textbook, with answers e.g. at the end of a chapter or the end of the book. PreText also supports embedding interactive elements like GeoGebra, JSXGraph, Sage, and specific question types like [WebWork](https://openwebwork.org/) and [MyOpenMath](https://www.myopenmath.com/). Various examples can be browsed [here](https://pretextbook.org/examples.html).

We add a new `<stack>` tag that lets us include STACK exercises exported from Moodle in Moodle XML format.

## Development

The PreText commandline interface is written in Python, however, a lot of the conversion logic for different formats is done using XSLT templating. While we wrote most of the STACK-specific logic itself, a lot of the more generic integration to piece that together with the existing codebase was supported by PreText developer Rob Beezer, especially the XSLT logic.

This is an early prototype implementation and some design decisions, including the semantics of the `<stack>` tag, may still change.
STACK questions are currently included as exercises like this:

```
<exercise>
	<title>Optional question title</title>
	<stack label="stack-integration">
		<xi:include href="path/to/moodle-xml-file.xml"/>
	</stack>
</exercise>
```

Below you can see different renditions of the above question, including the section containing the question.
Depending on the context where a STACK exercise is used, and the styling configuration, question could also appear differently. For example, in the static version, one can configure whether to display answers and solutions right after the exercise or at the end of the book.

<div style="display: flex; justify-content: space-between;">
    <figure class="figure" style="width: 48%;">
        <img class="figure-img img-fluid" src="../Images/pretext-example-html.png" alt="Interactive HTML version of the above question">
        <figcaption class="figure-caption">Interactive HTML version of the above question</figcaption>
    </figure>
    <figure class="figure" style="width: 48%;">
        <img class="figure-img img-fluid" src="../Images/pretext-example-static.png" alt="Static PDF version of the above question">
        <figcaption class="figure-caption">Static PDF version of the above question. Note that here the horizontal bar represents a blank for the student to put their answer.</figcaption>
    </figure>
</div>

### Implementation details

For the interactive HTML version, currently most of the Javascript logic is taken from Sam Fearn's `stackapicalls.js` from his [dynamic HTML course notes](Dynamic_course_notes.md), which for most part mirrors the [code from the STACK API sample page](https://github.com/maths/moodle-qtype_stack/blob/master/api/public/stackshared.php). We adapted the logic so that the STACK API can be deployed separately from the course notes, and its URL specified in the configuration. 
While for the interactive version, we can send the Moodle XML file of the question to the API as is and the javascript logic does the rendering, we also need to generate a static version of each STACK question that can be used in print, e.g. for the PDF output. For this purpose we send the question to the API to get a specific random instance of it, and then reformat the response using PreText's semantic XML tags for exercises, such as `<statement>`, `<answer>` and `<solution>` as well as formatting conversions for e.g. LaTeX. It should be noted that not all STACK questions are suitable for non-interactive versions.

### Next steps

While the current implementation is functional, a lot of aspects still need to be improved.

- Currently, feedback is not color-coded according to correctness. We should use CSS to style feedback appropriately. The look and feel of various elements of the questions, such as buttons, could also be adapted to align more closely with other PreText elements.
- The buttons and their labels mirror what is currently on the STACK API sample page. We may want to align this more closely with interactions with other question types.
- Static question generation is currently very basic. While not all questions work as static questions (e.g. question with interactive JSXGraph inputs), we can add better support for multiple choice questions and apply some heuristics to replace commonly used HTML tags within STACK questions to make them compatible with PreText
- The interactive STACK questions currently use a different version of MathJax than the rest of PreText textbooks. While this doesn't seem to cause visible issues in most cases, it produces some errors under the hood and needs to be fixed.

### Challenges

A question looking fine in Moodle is not a guarantee that it also looks fine in PreText.

For example, the following question's layout is too wide to fit into the display box:

<div class="float-none img-middle">
    <figure class="figure">
        <img class="figure-img img-fluid" src="../Images/pretext-challenges.png" alt="PreText STACK question with content extending beyond the right boundary">
        <figcaption class="figure-caption">PreText STACK question with content extending beyond the right boundary</figcaption>
    </figure>
</div>

We have also encountered an issue where a JSXGraph question would cause the page to lag because its coordinate system extended from 0 to 5000 and a grid was enabled to be shown. Disabling the grid option made the question render fine. In Moodle, the question rendered fine either way. This shows that additional review of STACK question PreText is necessary.
 
## Early usage

### Kenya

The first envisioned use case for STACK questions in PreText was in Kenya. After the [AIM workshop in Kenya](../2024/AIM_meeting.md) in 2024, Michael Obiero managed to acquire funding to support 10 local interns to work on PreText text books for the new competency based high school curriculum in Kenya, initially focusing on grades 7 to 10. The materials were developed from scratch, and STACK questions were already created and collected in anticipation of a future STACK/PreText integration.

Once a first draft of the integration was available, we included STACK questions in a few sections for a demo showcase of the grade 7 textbook and manually deployed it.

Development of the textbooks is still ongoing. The goal is to develop revision textbooks for grades 7-12.

### Ethiopia

After the experience from 2023 and discussions prior to the [3rd African STACK conference](African_STACK_conference_2025.md) we determined that it would be valuable to have the Basic Maths course as an interactive textbook, given that at each university in Ethiopia, thousands of students have to take this course every year. There are two version of the course, Basic Maths for Natural Sciences and Social Sciences, which overlap in about half of their content. The Ministry of Science and Higher Education has a text book that is openly available and was created by university lecturers.
One day before the The 3rd African STACK Conference for Undergraduate Mathematics (link will go here) we received the .docx source files, and started a conversion to HTML/MathJax using pandoc. Due to different formats of the maths typesetting in the book (new Word formulas, old work formulas, images), and the conversion being agnostic of the book structure, a lot of polish was needed. We wrote a script to split the output files into sections, and the intern team from Kenya spent the week cleaning up the book. Another script would include the STACK questions that were compiled in 2023 into the relevant sections. We deployed the STACK API online (thanks Ian) and hosted the book online, initially using github pages. The course will be delivered starting late September 2025. A similar course, Basic Maths for Social sciences, will start in January 2026, and more work will be needed to convert it into a book as 50% of the content differs from Basic Maths for Natural Sciences.

In order to support review by local lecturers, we also included an auto-generated link with each question to a feedback form. The link would pre-fill the form with an ID allowing our team to identify the question within Moodle and easily edit the question to address the feedback. The questions are synced between the Moodle server and PreText repository using gitsync.

<div class="float-none img-middle">
    <figure class="figure">
        <img class="figure-img img-fluid" src="../Images/pretext-review.png" alt="PreText STACK question with a review link">
        <figcaption class="figure-caption">PreText STACK question with a review link</figcaption>
    </figure>
</div>

We are currently exploring how we can add native support in PreText for review processes in a similar vein, rather than using a custom script to insert review links.

## Enablers

This work would not be possible without the STACK API, which was originally developed at RWTH Aachen University by Sven Kirschbaum for the Dynexite examination system, and integrated into the main STACK codebase and developed further by Edmund Farrow. Also thanks to Sam Fearn for getting me started on using the API, and my IDEMS colleague Ian Stride for hosting our own version of the API and helping me sort our CORS issues.

The PreText developer group has also been very supportive of this work. In particular, Rob Beezer integrated my contributions into the PreText codebase, but also thanks to Oscar Levin for supporting our team in Kenya.

## Future directions

In its current state, the STACK questions within PreText books can only serve for practice and self-assessment as no answer data is being collected. Given the philosophy of PreText, we could imagine creating a new output format that is a Moodle course, that would automatically be generated from the PreText XML source. This would mirror the content 1-to-1, and the exercises in the course could be used for assessment while the students can use the textbook for practice.

In the future, we may also consider hosting the STACK questions on an LMS (e.g. Moodle) server and passing answer data to the server using e.g. Learning Tools Interoperability (LTI) standards. Students would then authenticate on the textbook webpage using their LMS credentials, and information from interactions within the textbook would be passed on to the LMS server for storage. This way, students can do quizzes in the textbook while the LMS would provide a gradebook and tools for teachers to analyse students' results.