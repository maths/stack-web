---
template: casestudy.html

title: Dynamic course notes using the STACK API

shortdescription: The STACK API was used to create dynamic course notes which embed interactive STACK questions alongside other examples directly within accessible html notes.
cardimage: SS2.png
cardimagealt: An image of some html course notes with a STACK question appearing alongside a typed example.
---

# Dynamic course notes using the STACK API #

<img class="figure-img img-fluid float-right img-logo" src="../Images/DULogo.png" alt="University of Durham logo">

[Sam Fearn](https://www.maths.dur.ac.uk/users/s.m.fearn/)

Durham University

### Abstract ###

[The STACK API](https://github.com/maths/moodle-qtype_stack/tree/master/api) allows STACK questions to be viewed and marked (and tested) outside of a Moodle environment. One valuable use-case for this is the embedding of STACK questions as examples directly within course notes (in html format). This should enable students to better practice questions relative to the specific part of the course notes that they are currently studying.


### Motivation

Moodle provides many features that can be useful for formal assessment purposes, such as managing the opening and closing dates of an assessment, and storing the results data associated with each students' attempts. However, assessment in Higher Mathematics is often primarily designed to give students an opportunity to test their understanding, before further developing this through the feedback they then receive on their work. Assessment for this purpose is often called *Formative Assessment* (though this term can be ambiguous). STACK excels at this type of assessment. The nature of randomised questions means that detailed feedback can be given, with the student still able to "close the feedback loop" by testing whether their understanding has improved now they've been given this additional feedback. For such purposes, Moodle may be a barrier to student engagement, as students need to find the questions they would like to practice separately to the course notes explaining the material.

In order to minimise potential barriers to students engaging with practice course questions, [the STACK API](https://github.com/maths/moodle-qtype_stack/tree/master/api) was used to embed STACK questions directly within html format lecture notes.

# Execution #

The STACK API was first set up as a Docker container, as per the deployment instructions. The API then provides five routes, three of which we make use of in our notes. In particular, we use the API by sending and receiving JSON data to the `/render`, `/validate`, and `/grade` routes. The requests consist of the STACK question xml, as well as some configuration options specific to each route (such as the relevant seed to use when rendering or grading). Each request results in a JSON response which includes appropriately rendered text, such as the question text in the `/render` response, and the appropriate specific feedback in the `grade` response (see the [API usage instructions](https://github.com/maths/moodle-qtype_stack/tree/master/api#usage-instructions) for full details).

To use the API within a set of notes, the notes first need to be produced in html format. There are a number of tools which can assist with converting notes from other formats (including \(\LaTeX{}\) and markdown) to html. For this project [pandoc](https://pandoc.org) with the [tex2html](https://github.com/samfearn/tex2html) extensions were used to convert existing \(\LaTeX{}\) notes to html. The required questions should also be exported from a Moodle server in Moodle XML format. Question blocks can then be inserted into the notes by placing empty divs in the notes of the following form,
```
<div class="que stack" data-qid="XXXX"></div>
```
where `XXXX` is the Question Name of the required question contained in the exported Moodle XML.

A javascript module `stackapicalls.js` was created (based on a simple API frontend provided with the API), which includes all the required code for notes in the above form to communicate with the API. This module is included in the header of the html notes, and a simple initialisation function is called when the html body is loaded. The html notes, question XML file, javascript module and optionally any required style files or images can then be uploaded and served from a webserver.

<div class="float-none img-middle">
<figure class="figure">
<img class="figure-img img-fluid" src="../Images/StackAPI.png" alt="An image of some html course notes with a STACK question appearing alongside a typed example.">
  <figcaption class="figure-caption">Figure: A STACK question being displayed alongside a static worked example in a set of calculus course notes.
</figcaption>
</figure></div>

### Results ###

The (empty) divs of class `que stack` from before are numbered and populated, initially containing a button to generate a question. This button gets the XML of the question from a preconfigured list of XML files, and passes this to the `/render` route, before rendering the response. A random seed is used for the render, so the seed is attached to the answer submit button, ensuring that feedback for the correct question variant is given when a student checks their answer. Event listeners are attached to the inputs to call the `/validate` route when the input changes. The answer submit button calls the `/grade` route, passing the xml as before, with the matching seed to the `/render` call. The response from this is then rendered to the page.

<div class="float-none img-middle">
<figure class="figure">
<img class="figure-img img-fluid" src="../Images/StackAPIgif.gif" alt="A short gif, showing a question being rendered, the input validated, and the response graded. ">
  <figcaption class="figure-caption">Figure: A short gif, showing a simple example question being rendered, the input validated, and the response graded.
</figcaption>
</figure></div>

After checking their answer, a student can change their answer and resubmit, load a new example question, or simply move on.

### Challenges

Producing lecture notes in html format with embedded STACK questions can introduce new challenges for educators who wish to do so. The practice of writing mathematical notes in \(\LaTeX{}\) is well-established, automatic conversions of \(\LaTeX{}\) to html will often generate errors (or otherwise simply fail, particularly with more esoteric tex), and many staff will lack the time and/or inclination to rewrite course documents entirely from scratch. This challenge can hopefully be addressed through staff development, and the continued development of tools to help with conversion.

Another challenge with the current implementation of the API is that at the time of writing, the routes expect the question xml to be sent as part of the request. This means a knowledgeable user can obtain the full question xml, which may not be acceptable to an institution if the same questions appear in formal assessments. Some institutions may also not want to freely share their questions in this way.

A final technical challenge is that the current implementation of the `stackapicalls.js` javascript module which communicates with the API, makes these API calls directly from the browser (using [XMLHttpRequest](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest)). This is a simple way to communicate with the STACK API, without placing additional requirements on the backend, though it means that such API calls are subject to so-called Cross-Origin Resource Sharing ([CORS](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/CORS) rules. Whilst the API can easily be configured to allow cross-origin requests (see [this guide on CORS for the SLIM framework](https://www.slimframework.com/docs/v4/cookbook/enable-cors.html)), this is still currently causing some issues with more advanced questions that use [STACK-JS](https://docs.stack-assessment.org/en/Developer/STACK-JS/).

### Enablers

Embedding questions into lecture notes is only possible through the use of the STACK API, which was first developed as part of the [Dynexite examination system](https://help.itc.rwth-aachen.de/en/service/8d9eb2f36eea4fcaa9abd0e1ca008b22/article/41d91a35d6414293b4346dc656ac3e80/), and later integrated into the main STACK project. Many thanks go to [Edmund Farrow](https://edwebprofiles.ed.ac.uk/profile/edmund-farrow) for his work on making this available and easy to use. The example frontend he provided was the basis for the javascript module used to load questions into the html notes.

I'd also like to thank the [Durham Centre for Academic Development (DCAD)](https://www.durham.ac.uk/departments/centres/academic-development/) for awarding me an [Education Laboratory Fellowship](https://www.durham.ac.uk/departments/centres/academic-development/collaborative-grants/), which helped provide me with some time to work on this project.

### What's Next?

So far this project has been one of technical implementation, and so I am currently unable to provide evidence as to whether including questions directly within lecture notes increases student engagement with practice questions (by removing an access barrier). I therefore intend to conduct a small study to see whether (and if so, how) the provision of notes in this form changes student engagement with practice questions.