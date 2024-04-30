# 6th STACK Professionals Network meeting report, March 2024
The 6th STACK Professionals Network meeting took place on Tuesday 12th March 2024 in person during the International STACK Conference. There was some remote participation but unfortunately due to technical issues not all online participants were able to fully join.  

Acknowledgements: Thanks to OTH Amberg-Weiden for allowing the network to join during the conference. Thanks to all the participants who attended who are not official members of the network and for their contributions. Thanks to Sam Fearne for taking notes. 

The nature of the meeting was different than usual and it was an open discussion on new development, priorities and challenges that STACK users are facing. The meeting was co-facilitated by Santiago Borio and Chris Sangwin. Below is a list of the key items that were discussed. 


## Items discussed

* Chris outlined why the network is useful in order to demonstrate the continued value of the project. 

* Santiago introduced the network and how it works, what it aims to achieve both for the project and for its members.

* Corné pointed out the STACK Professionals Network is useful for forming consortia to apply to European grants, which usually require an internation consortium, and help people fund their existing positions.

* A question from the audience was posed about a drag-drop editor for STACK questions. Chris created dragmath some time ago, but the project died. If this is of value, perhaps some other audience member could take up this project. Chris also mentioned that MathPix might be a better future for natural input, and Sam mentioned having used STACK-JS in similar contexts. 

* Stephen requested more regular workshops (git basics, other special interests). Santiago mentioned that the conference included an introductory STACK workshop that was offered in multiple languages, and there would be scope for further events for targeted groups.

* A member of the audience suggester struggling with custom settings and useful scripts due to Moodle permissions. There was agreement that it would be good to have a list of Moodle capabilities required, listed on the main webpage, to lend authenticity and help convince institutions to grant these capabilities to STACK authors. Santiago offered an IDEMS server as a playground for new users to use to learn more about STACK and Moodle admin.

* An audience member learned from video tutorials online, specifically learned about question tests. Videos exist in the quick start guide. The docs website also gives specific advice by topic. Particular examples are good.

* What open and semi-open question banks exist? Some were mentioned.

* A question from audience was raised about being able to edit questions direct in text format. There was an existing project for writing questions in a YAML format. Chris noted that using such a format introduces the possibility of typos, etc. This project stalled a while ago and never added support for rich media, though YAML is capable of this. Sam added that being able to import PRTs would be useful. The audience thought that the YAML format was a good item to be high priority.

* Georg suggested trying to keep track of the various projects people were working on, such as projects analysing databases of questions. Chris noted that such projects were in a better place to succeed now that the gitsync plugin exists. Santiago noted that focus on multilingual development is necessary for open databases to thrive. ChatGPT and other tools can help do auto-translating, though it is possible for context to be lost between the different strings; It would be useful to be able to filter by language in a database, and see screenshots of the questions for users to decide whether the question is worth translating further.

* Question tests are currently basic and test score, penalty and final tree destination. There were requests for more advanced question testing: external libraries, timeouts for large sets of PRTs. Chris asked the audience whether they would rather have hard limits set in STACK, or soft limits created by timeouts. Audience unanimous they would rather not have hard limits. Chris introduced the s_assert function which can enable testing in feedback variables in Maxima.

* Edmund asked for thoughts about whether a change to monospace font would be a problem for people. Asked for contributions via Zulip.