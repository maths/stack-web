---
template: casestudy.html

title: Meclib: supporting mechanical systems
authors: Martin Kraska
shortdescription: Meclib is a set of tools to simplify authoring of STACK questions with a focus on mechanical systems
cardimage: ?
cardimagealt: ?
---

# Meclib: supporting mechanical systems

Martin Kraska

### Introduction

Meclib is a set of tools to simplify authoring of STACK questions with a focus on 
- JSXGraph based static and interactive illustrations controlled by Maxima lists (defined in the question variables)
- Maxima functions for rich formative feedback on interactive graphic input and on numeric or symbolic expressions.

The set of objects is created with sketches of mechanical systems in mind (support and load symbols, bars, ropes, disks, annotations). The most advanced application is the interactive creation of free body diagrams with rich formative feedback.

![image](https://github.com/user-attachments/assets/3cff9ae6-a800-43ee-90fe-23f46d97c906)


The primary website of the project is on Github. A good entry point is the [Wiki](https://github.com/mkraska/meclib/wiki).

There is a demo Moodle site, where Meclib examples can be tested. It is hosted at Brandenburg University of Applied Sciences (Technische Hochschule Brandenburg, THB).

[External Moodle Course](https://extmoodle.th-brandenburg.de/course/view.php?id=138)

- You can create an account on the server or use the guest login
- You need an account to actually access the demo questions, the other contents (slides, papers) can be accessed with guest login.
- No course password required.



### Getting started

The author of Meclib has developed two introductory workshop formats. They are documented in the Meclib wiki. With basic experience in authoring STACK questions, these workshops can be worked through without assistance. Guided workshops can be booked (kraska@th-brandenburg.de). 
- [My first Meclib question](https://github.com/mkraska/meclib/wiki/My-first-Meclib-question) Tutorial for a simple question with interactive input (center of gravity of a triangle). This workshop takes approximately 1.5 hrs if the basics of STACK questions are known.
  ![image](https://github.com/user-attachments/assets/09ab2652-3df3-4a32-bb38-ef7c5c1f42b8)

- [FBD Example Question](https://github.com/mkraska/meclib/wiki/FBD-Example-Question) Tutorial for a STACK question with interactive free body diagram editor, input of equillibrium conditions and support reactions. This workshop takes 6 hrs in total. For guided workshops, a distribution over two days is recommended in order to provide intermediate space for individual tryout by the participants.
  ![image](https://github.com/user-attachments/assets/7052ae1c-d76a-49c6-bf71-14d2361cb74a)
  ![image](https://github.com/user-attachments/assets/1a0cd47a-ba06-4ba4-96dc-6033acefffa0)

### Maxima driven JSXGraph graphics

The basic idea behind meclib is that question authors can embed high quality, visually consistent sketches with or without interactive elements into their STACK questions without writing a single line of Javascript. All contents of the graphics is driven by a Maxima list of object description lists inside the question variables. This list is injected into a generic part of the question text, which contains a `[[JSXGraph ]]` block. In early stages of Meclib development, this generic block contained the full JavaScript code (more than 2000 lines). Currently, the embedding using `[[include ]]` is recommended.

The available objects are documented in the [Meclib wiki](https://github.com/mkraska/meclib/wiki/List-of-Objects).

This is how the generic Meclib block for a static (non-interactive) image in the question text looks like (usually it is copy-pasted from the Meclib wiki)

```
[[lang code="de"]] [[/lang]][[lang code="other"]] [[/lang]]
<div style="float:right">
[[jsxgraph width='250px' height='250px' ]] 
var mode  = "STACK";  // as opposed to "jsfiddle" which is used in the test environment
var stateRef;         // is empty in the non-interactive case
const initstring = {#init#}; // injection of the list of objects
var decsep = {#stackfltsep#};  // injection of the decimal separator setting
const centeredLabelStyle = {size:0, showInfobox:false, label:{offset:[-6,0], 
  anchorX:'left', anchorY:'middle'}};
// End of STACK header
[[include src="https://raw.githubusercontent.com/mkraska/meclib/main/meclib.js" /]]
[[/jsxgraph]]</div>
```

Setting up such graphics is quite easy, getting started takes just a couple of hours and can be mastered by student assistants, including randomization.

For interactive graphical input, the `[[jsxgraph ]]` block is bound to two hidden input fields. `objects` is a string input filed, which stores a JSON version of the graphics specification. If the user modifies a graphic, these changes are reflected in this input field. Beyond the modification of existing objects, this includes dynamically generated or deleted objects, as required for interactive edit of free body diagrams.

For such questions, the basic effort is not in setting up the graphics side but in consistent and comprehensive feedback. 

### Feedback functions

### Localization

Meclib is fit for multilingual feedback and configurable decimal separator. Multilingual feedback uses the STACK language block `[[lang ]]`. 


## Reference

Kraska, Martin, & Schulz, Dennis. (2021). Automatic assessment of free body diagrams using STACK. Presented at the International Meeting of the STACK Community 2021, Zenodo. http://doi.org/10.5281/zenodo.4916138

Kraska, Martin. (2022). Meclib: Dynamic and interactive figures in STACK questions made easy. Presented at the International Meeting of the STACK Community 2022, Leoben, Austria. [https://github.com/mkraska/meclib/blob/main/References/STACK%202022%20Kraska%20V2.pdf](References/STACK%202022%20Kraska%20V2.pdf)
