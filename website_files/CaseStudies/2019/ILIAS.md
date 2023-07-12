---
template: casestudy.html

title: Technical Integration of STACK Into ILIAS

shortdescription: STACK was integrated into the ILIAS learning management system to support projects for learning content.
cardimage: ILIAS_thumbnail.png
cardimagealt: A typical STACK question in ILIAS.
---

# Technical Integration of STACK into ILIAS 
<img class="figure-img img-fluid float-right img-logo" src="../Images/ILI_logo.png" alt="Institut für Lern-Innovation logo">

#### Innovation in Learning Institute

Interview with Fred Neumann and Jesus Copado

### Abstract

STACK was integrated into the ILIAS learning management system to support projects for learning content. This was done by creating an integrated question type directly in ILIAS. The biggest challenges were decoupling the dependencies on Moodle, and an increasing number of user queries following a quickly growing community.

### Motivation

[ILIAS](http://www.ilias.de) is one of the most popular Learning Management Systems (LMS) used in German universities. It has been available under an open-source license since 2000, and since then has grown in popularity in a number of countries, especially Germany and Switzerland. In the last decade, the ILIAS community started a special-interest group related to mathematical assessment. The main driver for this was the "optes" project, a federally funded project to create open learning content for mathematics and natural science. It was key for this project to have a sophisticated question system that uses CAS to evaluate students' input. In 2013, the group compared different systems for CAS based questions and finally decided to use STACK. 

STACK was initially built for the learning management system Moodle, and it would not be trivial to implement STACK into ILIAS. A crowd funding initiative was started to port the STACK plugin from Moodle to ILIAS, and the Innovation in Learning Institute at the Friedrich-Alexander-University Erlangen-Nuremberg (FAU)  was asked to implement and maintain it. This would also be an advantage to FAU, as it could then establish STACK as an innovative element of e-learning and e-assessment at the University.

### Execution

It was important to create an integrated question type that works like all the others in ILIAS, instead of trying to dynamically connect a separate STACK platform to ILIAS. Initially, a 2-day meeting with lead STACK developer Chris Sangwin was held at Loughborough University in December 2013, where the basic architecture and principles of the question type were laid out. In the following months, the [ILIAS question type](https://github.com/ilifau/assStackQuestion) was created.

 The developers set up a Moodle installation with STACK, examined the code and analysed how it works. Then the ‘library-like’ Moodle core was extracted and integrated into the template of an ILIAS question plugin. The techniques used followed the open source nature of STACK and were supported by the fact that STACK uses the same technology (PHP/mySQL) as ILIAS.

Initially, the only way to add questions was to create them in Moodle, then import the moodleXML file into ILIAS. However, authoring provisions and an authoring interface were later created in ILIAS, using the GUI classes.

### Results

From the beginning, the ILIAS community has shown a great interest in using the integration of STACK. To date, nine separate institutions have participated in the crowd funding of the plugin. Over time, several workshops have been organized by the community. A German user manual and workshops to teach the creation of STACK questions was created at FAU and ported to an online module by the University of Göttingen. In 2018, [the first international STACK conference](https://www.stack-konferenz.de) was held at the Innovation in Learning Institute, bringing together around 65 participants from the Moodle and ILIAS communities.

As hoped, STACK is now being used extensively at FAU for innovative e-assessment. The ILIAS installation at FAU contains around 3000 questions from over 100 different authors. Additionally, a local ‘STACK user group’ was founded with 40 members from various disciplines, including mathematics, natural sciences, engineering, and economics.

Based on external and internal funding, it is possible to permanently provide new major versions of the plugin for each major ILIAS release every year, as well as several minor bug fix versions in between. The core of STACK used by the plugin is also updated every year. The ILIAS questions are fully compatible with the Moodle version and can be exchanged between the two Learning Management Systems through the moodleXML format.

<div class="float-right img-tall">
<figure class="figure">
<img class="figure-img img-fluid" src="../Images/ILI_question.png" alt="A typical ILIAS question about simplification.">
  <figcaption class="figure-caption">Figure: A typical ILIAS question about simplification..
</figcaption>
</figure></div>

### Challenges

The biggest challenge for the initial integration of STACK into ILIAS was the decoupling of all dependencies from Moodle in the STACK core. Currently, around 50 patches are maintained for that. Furthermore, there were major differences in ILIAS and Moodle regarding the definition and display of feedback and various test player options. The completely different GUIs of Moodle and ILIAS meant the whole authoring interface  of STACK had to be redesigned.

When the community of STACK users in ILIAS grew, the number of bug reports related to exotic edge cases of STACK usage also grew. This could, for example, be issues relating to questions with a huge number of inputs. Furthermore, an increasing community of users brought in very different opinions about the styles of a question, its validation and feedback. Dealing with these issues was a significant challenge.

A barrier that had to be evaluated is time. The initial work in integrating STACK into ILIAS took significant effort, and the project has to be continually maintained as bug fixes and project features are applied. It is estimated that, on average, 70% of a full-time employee's time is required to maintain the STACK developments for ILIAS. This is currently partially funded by the ILIAS community and the Innovation in Learning Institute.

Server performance was an issue when it came to using STACK in large institutions. Maxima was designed as a desktop application, and so lacks a set of “good practice” recommendations for hardware and configuration options depending on the expected load. To solve this, there are some initiatives such as the GoMaxima project from HAW Hamburg and an initiative at the University of Göttingen for a docker swarm of Maxima pools.

### Enablers

The meeting with the lead STACK developer was a major help in getting the project off on the right track. The comprehensive STACK documentation was also invaluable for understanding the question type.

Additionally, the support from the ILIAS special interest group was invaluable. This group helped sketch the authoring interface in ILIAS, write documentation and organise the first workshops. It also helped moderate the discussion of feature requests from the ILIAS community and organise crowd funding for the maintenance of the plugin. Furthermore, since the Innovation in Learning Institution is not a mathematics institution, it was invaluable to get help from mathematicians to write good demonstration questions.

Finally, the port was supported by the common technology of ILIAS and STACK and the fact Moodle and ILIAS have very similar quiz structures, and both treat STACK as a question plugin type. Implementation differences aside, the main principles are the same.

### What's Next?

The ILIAS question type will continue to be updated as STACK, Moodle and ILIAS get updated. In particular, the way question types in ILIAS are implemented will change in a future ILIAS patch, which means the question type will have to be adapted accordingly. There are also plans to make STACK less dependent on the Moodle library. If this is successful, the ILIAS plugin will have to be largely rewritten (since it depends on the Moodle library), however the developers are optimistic. From writing the question type the first time around, they have gained invaluable experience. Furthermore, the authoring interface will not have to be rewritten.

There are many wishes from the ILIAS community for new features to be implemented. Some of these are step-wise feedback, as well as more control of the feedback style, for example the colour of feedback boxes. These may be added to the STACK question type in the future.

Finally, the maintenance relies heavily on crowdfunding managed between institutions (typically the Innovation in Learning Institution and another University). This means contracts have to be written between the heads of each institution, which can be difficult to manage. There are therefore considerations to transfer the maintenance of the question type to an ILIAS service provider, as it would then be easier to get crowdfunding contracts from Universities.
