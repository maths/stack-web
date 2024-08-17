---
template: casestudy.html

title: American Institute of Mathematics meeting on Open source mathematics curriculum and assessment tools
authors: Franca Hoffmann, David Stern and Juma Zevick
shortdescription: A report of an AIM-sponsored meeting on Open source mathematics curriculum and assessment tools
cardimage: AIM-card.jpg
cardimagealt: AIM-card.jpg
---

# American Institute of Mathematics meeting: Open source mathematics curriculum and assessment tools

Franca Hoffmann, David Stern and Juma Zevick 

### Introduction

The [American Institute of Mathematics](https://aimath.org/) (AIM) hosted an engaging workshop on [Open Source Mathematics Curriculum and Assessment Tools](https://aimath.org/pastworkshops/oerassessment.html) at Maseno University in Kisumu, Kenya, from August 5 to 9, 2024. This event brought together a vibrant mix of educators, researchers, and software developers. The workshop was organised by Joe Champion from Boise State University, Franca Hoffmann from CalTech, Michael Obiero from Maseno University, and Mary Ochieng from Strathmore University, with support from the National Science Foundation (USA). It aimed to improve the use and impact of open educational technologies, including STACK, in mathematics. The event also set the stage for the [International STACK Conference at the Technical University of Kenya](https://stack-assessment.org/Events/2024-08-12-AfricanSTACKConference/), starting on August 12, 2024.

<div class="float-none img-middle">
    <figure class="figure">
        <img class="figure-img img-fluid" src="../Images/AIM-group.JPG" alt="AIM attendance photo">
        <figcaption class="figure-caption">AIM attendance photo</figcaption>
    </figure>
</div>


### Workshop Overview

This event adopted the AIM workshop format, encouraging participants to propose open problems and questions before it began. These suggestions ranged from specific issues to broader challenges that could shape the future of the field. The workshop included lectures to equip participants with the necessary background on these problems, followed by parallel working sessions for collaborative problem-solving. It was designed to foster collaboration between mathematicians, researchers in mathematics education and developers of open-source tools, including Webwork and STACK.

#### Key Objectives:

The main topics for the workshop were

1. Enhancing Integration: Discussing strategies for better integration of open-source tools with existing educational frameworks.
2. Research Collaboration: Facilitating partnerships between developers and researchers to drive innovation and practical application.
3. Data Sharing and Analysis: Exploring new avenues for sharing and analyzing educational data to improve learning outcomes.
4. Interoperability: Addressing the technical challenges of ensuring that different educational technologies, e.g. STACK and Webwork, can work together.
5. Implementation Challenges: Identifying common obstacles in the adoption and effective use of these tools, and proposing solutions.

### Sessions and Discussions

In addition to featured talks, participants engaged in focused group discussions. Key topics are summarised below.

###### Sharing of Educational Material 

For open-source educational software to be competitive with commercial options, collaboration on development and content is key. WeBWorK (https://webwork.maa.org/moodle/) is widely used in the US and part of its attractiveness is a well-organised question bank. Questions are tagged by topic and through a user-friendly interface can easily be integrated into worksheets and courses. However, ownership of questions and derivatives is not clearly traced. 
For STACK, several question banks have already been developed by different groups (some open, some closed), and additional question banks are rapidly being developed. There is a pressing need for a structured approach for sharing and collaborating on the development of questions in STACK. A concrete plan for a general library of STACK questions, tagged by topics, emerged. However, this is not enough. 
The discussions produced a clear vision: A system for a structured repository of curated material, allowing for multi-layered ownership. Here, by "curated" we mean material that is (i) tagged by topic, (ii) quality-controlled, and (iii) exists within a broader context. For instance, a question may exist within a sequence of questions intended for a specific pedagogical/educational purpose, which exists within a worksheet, topic, chapter, course etc, and may be adopted to the requirements of a given educational level or curriculum.
Ideally, such a repository of materials should be usable across different platforms and educational tools so that the user is not constrained by the choice of tool. The participants discussed how to overcome technological barriers for this goal, and PreTeXt (https://pretextbook.org/)  presented itself as a vehicle in this direction. 
Accessibility could serve as a minimum requirement for writing formats (e.g. a screen reader being able to interpret the content). In order for groups maintaining question banks for their own context (at the level of a continent / region / country / institution / department / individual) to take ownership of this process, a structured approach is needed. The group discussed the architecture for this vision, both from a technological and managerial perspective, and concluded that working towards this vision represents an opportunity for novel ideas to emerge for instance for the development of new technology to allow for version control of content and its derivatives across multiple ownership levels. Some of the technological challenges were then taken up by the interoperability discussion group.

###### Interoperability of Learning Platforms

The vision of having question repositories which cut across multiple tools requires technical interoperability beyond current capabilities. For this the workshop participants discussed: (1) Translation — e.g. converting STACK questions to WeBWorK questions, and vice versa for content sharing between different lecturers, institutions and question banks; (2) Agnostic authoring — allowing people to write content (textbooks, quizzes, questions etc) without having to decide on a deployment method a priori, avoiding having to learn domain-specific markup. 
For agnostic authoring, the potential of markup languages that capture the structure of learning materials, while being both highly human-editable and computer readable, was discussed. The initial efforts in this direction by PreTeXt were discussed at the meeting. PreTeXt documents can be published in multiple formats, as they separate the task of authoring from publishing. PreTeXt could potentially play the role of a question-engine agnostic authoring tool; it currently integrates WebWorK, and the potential of integrating the new STACK Application Programming Interfaces (API) in the future was discussed. While PreTeXt may be able to render questions in a variety of tools, it will come at the price of losing rich tool specific features. It was discussed that there is already a user base for which interoperability and access to a wider bank of material is a priority. Over time, the agnostic authoring capabilities could be extended, potentially enabling open tools to reflect on and extend their own capabilities in the process.
For author interoperability, a common authoring style is key, and whilst this may mean making choices on the development side for specifying a meta-framework, targeting 80% of automatic correct cross-platform translation seems like a good tradeoff between needed sophistication and quality of desired functionality. 
Interoperability requires standardised protocols and APIs; an API for STACK is now available as of recently. For translation of material/markup languages as well as translating content to other human languages, AI may be a useful tool, as long as appropriate training sets can be identified. For interoperability between two platforms, the goal is to design two one-way systems instead of one closed-loop, therefore retaining options of more advanced features in both systems. Further, one needs to explicitly think about managing ontology: first drawing out explicitly the different schemas of the various systems, and then asking how to map subsystems to each other. The overall goal is that users can set up their own system without having to commit to one tool (as is usually the case with commercial software), but rather can access a variety of tools, drawing on the power of collaboration in open-source software. To move forward successfully, it is vital that the community develops a common vision for cross-platform interoperability. 
The workshop aimed to identify technical barriers and promote the development of cohesive learning platforms. This approach is vital for enabling educators to integrate various technologies, like STACK, WeBWorK and PreTeXt, and for this to be possible within a given context and with local ownership lead to the concepts of multi-layered ownership and evolvable (meta-)ontology.
The aim emerged to have an ecosystem based on content rather than the choice of tool. This could be based on open principles, with a distributed model for appropriate multi-layered ownership and version control, allowing for both public and private repositories. Making these ideas a reality asks for new approaches and new technological tools to be developed - exciting future directions.


###### Challenges and Innovative Uses

Both technological and human-related barriers may prevent the adoption of maths education technologies. From the discussions emerged a structured list of barriers to adoption in the African context, focusing on secondary and tertiary education. Further discussions focused on innovative uses of open online curriculum and assessment tools to address these barriers in terms of digital and human–driven innovations in training, education, and instruction. Participants discussed how to use these tools to tap into existing student intuition and skills, and how to build on the historical nature of exercising maths, which tends to be pen-and-paper based. Innovative uses in instruction include using technology as a tool to improve interaction between instructor and students by focusing on thought-revealing activities, on overcoming social impediments in teacher-student relationships and the learning process, on task improvements (eg via scaffolding as in faded worked examples), and on real-world problem based learning. Innovative uses may allow students to concentrate on the problem rather than the maths, and on student-to-student interaction (e.g. through team-based grading, dialogic interaction, de-emphasizing competition, collaboration and more able peer-to-peer learning). If done well, this enables students to participate in the development of tech not as testers, but as conceptualizers. In this, the educational context is shaping the innovation, e.g. access to different types of devices. 

A key focus of the workshop was inclusivity. Considerations for students with special needs in the development and implementation of educational technologies are still lacking behind. Participants discussed access barriers and how tools can be adapted to overcome them, needs assessment of existing technologies, identification of appropriate assistive technologies for various categories of special needs, and engagement with mathematics experts with special needs for identification of appropriate technologies and necessary adaptations. Concrete ideas for an exploratory study on assistive technology and learning of mathematics in Kenya emerged. Next steps include bringing together experts to start exploratory research, with a focus on identifying needs and potential technological solutions. 

Overall, the following questions took centre stage in the discussions on innovative uses: How can innovation introduce more empathy in the learning process? Can it create space for non-intuitive maths students, e.g. via a tool for capturing how non-intuitive maths learners have breakthroughs in learning? How can we use technology as specialised, personalised tools for students to learn in the way(s) they learn best? Can the tools reflect the cognitive empathy of a great teacher (e.g., anticipating student responses, responding to student reasoning)? How can we innovate maths communication, leveraging different ways that people arrive at understanding the same maths concepts? Participants recommended including research in the process of continuously improving STACK and other educational tools to answer these questions.


###### Educators' training and Curriculum Development

Participants discussed the adoption of the Competency Based Curriculum (CBC) and shortcomings/benefits thereof. The CBC has been introduced recently in Kenyan secondary schools, and it is expected that lecturers adapt their curriculum and delivery modes once these students arrive in Kenyan universities. These discussions are relevant more broadly as several countries across Africa are considering CBC implementation. Further, the group built a shared understanding on generic challenges in mathematics teacher education and challenges associated with the use of STACK and other tools for pre-service mathematics teachers. Moving forward, participants proposed collaborations on multinational curriculum design teacher training, including via synchronous curriculum discussions/meetings and joint funding proposals.

There is a pressing need for training on emerging technologies to enhance the teaching of mathematics at all levels, including specifically for basic education and higher education facilitators in response to the CBC curriculum. Technological advancements in mathematics education have highlighted the gap in awareness and optimal usage among mathematics teachers. Participants worked on concrete next steps: (i) Developing and launching a postgraduate program in Master of Science in Mathematical Innovation; (ii) An EdD (Mathematics Education Professional Doctorate Program) designed for mathematics educators, leaders, and professionals who want to advance their knowledge and expertise in education; (iii) building partnerships and collaboration networks for Mathematics Educators and Researchers, with Kenya Mathematical Society taking a lead in the process.

The Master of Science in Mathematical Innovation was identified as a key priority for the Kenyan context. The Open University of Kenya was proposed as an initial implementing partner, given the potential of a large-scale eLearning programme. International and Kenyan partners agreed to support the development and initial implementation, as it was recognised that no individual institution has the capability to develop this ambitious ground-breaking programme alone.

###### Mathematics Education Research

The general discussion focused on opportunities within the community to develop research projects related to existing instructional contexts in Africa, noting that developing publishable results can be observational and would be excellent contributions to the literature. After specific research questions are identified, next steps could include applying quantitative and qualitative methods to more refined versions of these studies. 

Seeing challenges as opportunities can drive positive change; for instance, the large classes in many African universities provide the opportunity to rapidly innovate on teaching practices, for the use of technology and comprehensive data collection for impactful research. Participants discussed implications of large classes in terms of assessment, instructional methods, instructor training, and student learning experiences, and it was recognised as a driving force behind many of the issues discussed at this workshop. 

By the end of the workshop, participants produced plans for 7 concrete collaborative studies, including a study on "STACK Online Assessment in Large University Mathematics Courses" to be launched this month involving universities in several African countries and a growing list of international collaborators, focusing on the following questions: (1) What are the patterns in students’ STACK performance? (2) To what extent is STACK performance associated with course achievement? (3) To what extent is STACK performance associated with instructors’ characteristics (attitude, competency, skills etc)? (4) What factors (e.g attitude, entrance behaviour etc) are associated with differences in students’ STACK performance?

###### Financial Sustainability

The workshop participants emphasised the hidden costs of open-source tools: whilst the software itself may be free, implementation may still rely on investment of appropriate resources for training / authoring / integration. Whilst the long term goal includes sustainable partnerships, it is more advantageous to prioritise successful implementation in the short-term. The key question is how to transition from unsustainable to sustainable solutions for the use of EduTech tools in maths. The priorities may look different for different types of users (instructors, administrators and students). A model that has proven successful is for an enthusiastic faculty member to become the main local manager. Several business models for open-source software already exist in the literature. STACK seems to be mostly operating under Business Model 4 of FOSS (Free & Open Source Software) business strategies [From Fitzgerald (2006)] as it helps sell research and implementation. An alternative revenue opportunity that may be leveraged by the STACK team is course-specific material creation within STACK.

In general, what is needed for broader adoption is the right combination of (1) a turnkey solution with excellent user experience, (2) reliable pricing and services, and (3) research-based evidence of outcomes. The community formed at this workshop can serve as a resource for developers and users trying to work out sustainable business models.

###### Responsible AI

Lecturers expressed concern how to adapt to the increasing use of generative AI by students. This sparked various conversations leading to a consensus that this shift presents an opportunity to reframe our assignments and exams, encouraging the development of higher-order assessment items for students. To support educators in this transition, resources like the Responsible AI for Lecturers' course developed by IDEMS were made available for use, offering guidance on effectively integrating these tools in their teaching.
This was identified as a highly topical issue which warranted deeper consideration. While some participants intend to collaborate on trialling initiatives in their context, it was felt that this topic could benefit from taking a more central role in a future event. 


### Outcomes and Future Directions

The workshop concluded with several key recommendations and plans for future actions. Concrete next steps already on the way include:

Collaborating towards launching a new masters program “Master of Science in Mathematical Innovation”  at the Open University Kenya, in time to support the training of secondary school teachers for the upcoming switch to a Competency Based Curriculum, with the first student potentially to enrol in January 2025.
Seven concrete collaborative research studies on the timescale of 5+ years with a growing list of partners and with the first study to be launched in September 2024.
Conceptualising pathways for content sharing with multi-level ownership including first concrete ideas how to structure ownership levels and re-envision version control, bringing together developers, key partners from the Topos Institute and teams managing question banks.

In addition to the above concrete outcomes, plans for research visits and joined grant proposals have been launched at the workshop, as well as concrete ideas for future AIM workshops to be held in Africa on related topics. More generally, participants agreed to establish a network of educators, researchers, and developers to address the challenges identified during the workshop. This network aims to drive the adoption of open-source tools like STACK and ensure they are effectively integrated into educational practices and a wider ecosystem of tools. Emphasis was put on the importance of community support, professional development, and iterative feedback loops to improve the integration of STACK and similar tools.

### Conclusion

The meeting ended with a sense of real momentum, and the participants have committed themselves to leading the way in enhancing mathematics education through innovative technologies. The workshop has not only laid the groundwork for future collaborations but also set a clear path for the continued development and improvement of tools like STACK, ultimately benefiting students and educators across diverse learning environments. 
