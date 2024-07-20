# STACK v4.6.0 matching feature demo and feedback session

A feature allowing authors to write drag-and-drop matching problems was developed for release in STACK v4.6.0.
A preview and feedback session was held on Monday, 13th May 2024 with members of the STACK Professionals Network 
to establish any desired changes or additions to the current state of development prior to release.

Present at the meeting: Sal Mercuri, Matti Harjula, Luke Longworth, Sam Fearn, Andreas Steiger, Stephen Nulty, 
Juma Zevick, Wigand Rathmann, Edmund Farrow, Danilo Lewanski.

## Background
A drag-and-drop proof assessment feature based on Parson's problems was released in STACK v4.5.0 in Dec. 2023 
through a `parsons` block.
In these questions, students are presented with two lists: an available list populated with pre-written strings
corresponding to steps in the proof; an empty answer list they must drag proof steps to in the correct order.
The priority for STACK v4.6.0 is to extend this drag-and-drop functionality beyond proof into more general 
"grouping" (dragging items into the correct category) and "matching" (dragging multiple corresponding items 
to the same row) questions.

## Demo summary
- Introduction and background.
- Grouping question demo.
    - A question where a student is asked to drag functions into the groups "Continuous" and "Discontinuous" as appropriate.
    - Student interface was presented.
    - Author workflow was presented focusing on defining variables and setting up the question text. Assessment through the use of the to-be-released `matchlib.mac` STACK library was also covered.
- Matching question demo.
    - A question where a student is asked to drag functions and their first- and second-order derivatives into rows as appropriate.
    - Student interface was presented.
    - Author workflow was presented as in the grouping question demo.
- Feedback on items so far.
- (Time permitting) Adding index columns to matching questions and using images.

## Feedback and other items discussed
- A question on style was raised, particularly in the scenario where a large number of groups/columns are being used. Action item: test larger volumes of columns/rows and make documentation recommendations where necessary.
- A suggestion of helper functions which could map Maxima variables into TeX within displayed items, to avoid the burden of having to `\\(...\\)` numerous times. It was raised that this would require further development on how CASText is handled by STACK.
- Question raised about whether interactive images could be used, for example JSXGraph. A longer-term possibility for more general item styles which may also include inputs within items.
- A question on PRTs and whether more bespoke forms of evaluation are possible, for example, can we check whether a student has used a specific item somewhere in their grid?
- Discussion around when is it more appropriate to use drag-and-drop style questions vs. drop-down vs. other styles of questions. It could be a useful research study to understand the impact of using drag-and-drop style questions vs. drop-down, and make guidelines and recommendations based on these. A link to [A Collaboratively-Derived Research Agenda for E-assessment in Undergraduate Mathematics](https://link.springer.com/article/10.1007/s40753-022-00189-6) was shared in relation to this.
- Request to see the original Parson's proof question style for comparison and it was clarified how proof vs. grouping vs. matching styles are defined.