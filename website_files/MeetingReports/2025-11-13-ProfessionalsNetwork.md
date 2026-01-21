# STACK Professionals' Network: Meeting on 13 November 2025 

## Participants
* Maciej Matuszewski
* Jesus Copado
* Tim Lowe
* Marc Peterfi
* George Ionita
* Jonas Lache
* Michele Pancera
* Matti Harjula
* Marcus Green
* Edmund Farrow
* Konstantina Zerva


## Developers Updates

STACK-Moodle update from Edmund: In STACK 4.11.0 there is a fair number of bug fixes. Download questions, are also working again now. We've added in chemical data. There's a sticky footer on the edit form, so you don't have to scroll all the way to the bottom to save. MathJack's version has been updated, to 3.2.2. We've got increased consistency on the dashboard pages. Work has been done on the response analysis page. You can now download JSON data from that and also, you should get all the attempts on the questions. In terms of the API, the API will now take in YAML question fragments, and you can also get, YAML versions of questions out, as well, which are more readable.   
Instead of having text-based PRTs, we are gonna do a full edit page of STACK questions, so you'll be able to see the XML make changes to it, and then import that XML as a new version.  


## Items Discused

### AI Authoring Assistant
This AI assistant was created to remove some of the barriers that new STACK users face when they start writing questions. This "Proof of concept" is working with ChatGPT (version 4.0 at the moment) on its interface. 
In the eample presented, Michele copied an image of an integral and asked the AI-assistant to randomise that integral. The AI assistant gave some pedagodical ideas about what the student is ask to do and then proceded to give the Question variables, the question text and the general feedback. If the question is simple enough you can copy and past all of these in the STACK question. The main idea is not to copy-paste, but is to have a conversation with the assistant so that your ideas are the ones that are being developed, and the assistant just makes you faster. What we don't have at the moment is the PRT; they are working on having the assistant also be able to help with the PRT. 

The AI-assistant can make the question multilingual with [[lang]]. The assistant can also help the user not just for writing questions but also to learn how write stuff in STACK, e.g. how to referce variables in a question.  
The next step that they are developing at the moment is an application where they can call some other LLM, through API, have a conversation with the assistantand after the conversation the question variables, the question text and the general feedback are automatically parsed and put into an actual stack question, so that it can be modified directly. 

At the moment the AI -assistant is not giving back the XML file of the STACK question.

### Funding application in ICMS Mathematics for Humanities Worldwide. 
We submited a funding application for the Mathematics for Humanities Worldwide scheme, which can fund up to 30,000£ for a satelatite event around the STACK conference. We will know around the end of January if this will get funded. 

### Parser for STACK
Matti presented the new parser. In STACK we now have these "stackbasen()" objects available where you can define a base and number. And if your input has been configured correctly, the student can input base and numbers in various ways. In general, we support bases from 2 to 36 , bu most digital electronics courses probably will work with CS Index. And we have plenty of tools inside, new functions that generate and convert bases. You can validate that the input is in correct base, the digits match the base, and whatnot, generate tables, ...  This is now in the dev branch, so probably it will releases next year sometime, maybe in January or in March.

We now have a rust parser that you can use if you need to build tools to process STACK questions in bulk on command line, or we have a JavaScript parser that you can load into your browser and parse Maxima content. And translate it between to some other formats.

## Date for next meeting:
The next meeting will take place hybridly during the STACK, STEM & AI Event in Seville, either 29 or 30 January - time to be fixed.

Note: this meeting was recorded and the video was shared with the members of the Network. 