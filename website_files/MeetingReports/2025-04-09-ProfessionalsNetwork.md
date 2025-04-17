# STACK Professionals' Network: Meeting on 09 April 2024

The meeting took place on Wednesday 09 of April 2025, in person, during the International STACK Conference at Durham University. There was some remote participation from members who couldn't travel to Durham.  

Acknowledgements: Thanks to Durham University and the conference organisers for allowing the network to join during the conference. Thanks to all the participants who attended who are not official members of the network and for their contributions. 

Below is a list of the key items that were discussed.

## Items discussed

### STACK training - resources

* There was a question from the audience of how to get other people to learn STACK without scaring them off. Jonas and Tim mentioned they both run in-person workshops for collueges at their institutions. People don't often realise how comlicated it is and there is a steep learning curve. People need to also know LaTeX, Maxima and the basic Moodle learning environment. Sam said that in the UK it is quite common for university staff to get a kind of teaching accreditation when they first get a teaching post. This is usually a Fellowship from the Advance HE (Higher Education) and in Durham University people need to atend some training workshops. So they run a STACK training as part of these workshops.

* STACK training sessions most times start with an exampe]le that requires people to also pay attention on the mathematics while first encountering the software. Marcus and Jonas said that they start the workshops with a very simple examp (e.g 1+1) to allow the audience to focus on the functionality of the tool before they deal with the maths. Hayden also mentioned that the differentionation example was too advance for a broader audience, so this is something to consider when running workshops . 

* George said that when he runs STACK training sessions he starts with the quadratic equation and he splits up the problem into 7 problems. He starts with something very, very basic like solving a quadratic equation, without randomization, and then deliberately making design mistakes and improving at each step while showing each time how powerful STACK is and what it can do.

* Sam mentioned the concept of a non-technical STACK workshop: people to write a binary decision tree for marking an assessment of their choice. This will not involve code at all, but just try to think of the tests that you would need if you were going to mark an essay and what feedback are you going to give depending on how those tests turn out. For example, does it have good paragraph structure or is it grammatically correct? 

* [STACK 101](https://stack-demo.maths.ed.ac.uk/demo/course/view.php?id=62) course. This is an online STACK training course that covers everything, including HTML, Maxima, Latex, Moodle, as well as basic STACK examples. This is the first attempt to create such a course and it is still under constraction. We would appreciate input of how to improve the course and what else to include.

* Description of "Answer Test": write a couple of sentenses explaining what each answer test does/means. There is explanation in Appendix E of Tim's STACK Guide. Maybe update this file and point towards them. 

* How people can ask for a workshop? There are people outside of Higher Education now that are starting using STACK and they would benefit from a STACK training because they would be able to ask questions. But it isn't obvius of how to organise this, how to advertise or how people can ask for it. Have a kind of form that people can ask for a workshop  - where to put it so that people can easily find it? Possibly one way people find STACK is the Moodle plugins data base entry: <https://moodle.org/plugins/qtype_stack>

* There was a sugestion from Marcus to concentrate on subjects outside maths, who use maths, like economics, business, psychology, sociology because they will hugely benefit from STACK.

* There was a discussion of how to advertise and promote STACK. There was a suggestion to contact new partners, who are commercial organisations. George mentioned that a good advertisment for STACK is to make it obvious of how much money institutions save by using STACK (marking time, tutors hours).



### Development percpective: 

* Variable input fields: there is a github issue on that: <https://github.com/maths/moodle-qtype_stack/issues/1254>. People can post here for further development. 

* Copy/paste PRTs. Still on the TO-DO list. Jesus said this functionality exists on ILIAS. 

* Save a broken questions. Still on the TO-DO list. 

* Editors, especially for JSXGraphs and SVGs. (Marklar editor. It has HTML and Markdown preview and pasting images from the clipboard)

* JavaScript maths keyboards into stack questions, for the student input: FlickMath as a possible input type for students to use – lives in one of the branches, not recently tested or updated.

* When should people do a single stack update for the year? Edinburgh updates in June, the latest build should be mostly stable at the end of June. And always run the bulk test on questions after updating the STACK version. 


### Other

* Units: there was a qustion from George regarding STACK questions for Physics that assess units. In a simple question the validation provides feedback if the units are missing. Martin said that the main problem with units is that you can do a lot of errors and if you want to catch them all, you have exploding feedback trees that are not very easy to copy. He sugested using feedback functions, which do all the feedback in a single node. He pointed to a question from the Meclib worshop which contains the standard Meclib feedback functions for algebraic expressions and numerical values with or without units. https://stack-demo.maths.ed.ac.uk/demo/mod/quiz/view.php?id=1890




