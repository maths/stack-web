---
template: casestudy.html

title: Translating STACK questions with AI
authors: Georg Osang
shortdescription: We describe how we have used a neural machine translation service to automatically translate STACK questions.
cardimage: working-with-data-course.png
cardimagealt: A translated section of the "Introduction to working with data" course
--- 

# Translating STACK questions with AI

Georg Osang

### Abstract

This case study describes how within IDEMS we have used the translation API from DeepL, a Language AI company, in 2025 to automatically translate STACK questions from English to French and Italian, and from German to English, allowing us to scale open educational materials across language barriers.

### Motivation

The STACK community is large and growing, and one of its strengths is the wide international collaboration.  We have significant projects creating materials which are useful for students in languages other than the original.  Past projects, e.g. [IDIAM](../../../Projects/IDIAM/) sought to provide materials in multiple languages, however for the IDIAM project translation was a manual process.

Given the rapid improvement of the quality of machine translation, it is now timely to use this to translate STACK questions between languages.  This case study reports our progress with machine translation in the spring of 2025.

The initial motivating application came about from IDEMS' _Introduction to working with data_ Moodle course. This course features modules with exposition as well as STACK and multiple choice questions. Our team was planning to give a training in West Africa featuring a large portion of this course. However, the training was scheduled to be in French, while the course content was in English. Ideally, we would have the course available in both English and French using multi-language tags, in particular STACK's `[[lang]]` tags within STACK questions and Moodle's `{{mlang}}` tags elsewhere.

While plain-text, and simple HTML, can be sensibly translated by sending it directly to a translation engine, STACK has more complex syntax using blocks with different semantics, including LaTeX, mathematics as Maxima and HTML. Sending the text-based representation of a whole question (e.g. the "Moodle XML file"), or even just the raw question text itself, directly to a translation engine is likely to break syntax and translate some content that does not need to be translated. Furthermore, if we wanted to use multi-language tags, we'd have to break down the question into smaller units (strings) to be translated.

In the past, we manually tagged strings using a language block, and then automatically extracted the content of these blocks and sent them for translation. In practice, that meant that the bulk of the work was manually tagging strings to be translated, as the rest could be automated. Thus, the major challenge now was extracting sensible units of text to be translated.

### Technical Execution

On a high level, our process consists of extracting strings, sending these to a translation engine for translation, and then re-inserting either the translated strings or multi-language blocks with the translations.

As we were working on an entire course, we would use the Moodle export of that course, which is a compressed folder structure of XML files. Thus, we first iterate through these files and parse their XML, and within the XML tree classify the content of its elements semantically. Many fields are metadata that can be ignore, but text data may be plain text/HTML, CASText (for STACK questions) or maxima code, all of which need to be treated differently.

For each of these content types, our string extraction algorithm is slightly different, and similarly, the method for re-insertion may be different. The STACK-specific content types, i.e. CASText and maxima code, require a lot more complexity to process, and for now we have omitted extracting strings from within maxima code (e.g. the question variables). Below gives examples of typical strings that are extracted from a CASText block.

```
<p><b>Bold</b> and <i>italic</i> text remains part of a sentence.</p>
[[jsxgraph]]Code doesn't need to be translated.[[/jsxgraph]]
The answer is: [[input:ans1]] [[validation:ans1]] [[feedback:prt1]]

[[ if test='oddp(var)']]
Please don't mess up my \(\LaTeX\).<br>
And don't even bother translating the maths below.
\[ \sum_{k=1}^\infty \frac{1}{n^2} \mbox{is really mathsy stuff.} \]
[[ else ]]
<p>We can use \({@a@}+{@b@}\) or {@c@} in the middle of a sentence.</p>
[[/ if]]
```

Extracted strings:

- `<b>Bold</b> and <i>italic</i> text remains part of a sentence.`
- `The answer is:`
- `Please don't mess up my <x>\(\LaTeX\)</x>.`
- `And don't even bother translating the maths below.`
- `We can use <x>\({@a@}+{@b@}\)</x> or <x>{@c@}</x> in the middle of a sentence.`

Note how we keep text formatting HTML tags, like italic and bold, inline, while other tags, like paragraphs, indicate a separation of units of text. The DeepL API that we are using is able to cope with HTML tags within text sensibly. Moreover, we wrap any kind of LaTeX or maxima into `<x>` tags (while being careful not to nest them), which indicates to DeepL not to translate the content inside. Without these, LaTeX syntax would occasionally get broken in the process. In our example the `\mbox{is really mathsy stuff.}` content inside the displayed equation `\[ ... \]` remains untranslated in this first trial.   

After translation, the translated text or multi-language text is then re-inserted using bespoke search and replace.

For this project, we made the design decision to only translate student-facing content. That means that the question title, note and description remain untranslated. The rationale is that this reduces maintenance load and makes it easier to trace back translated questions to their origin. However, in the future it would be easy to configure which fields, within the digital object, to translate as needed.
We don't aim to translate maxima variable names in the future, as that would make it much more difficult to sync code/logic changes between translated versions, especially as questions become more widely shared with the related [gitsync](https://github.com/maths/moodle-qbank_gitsync) project.

### Challenges

Using search and replace has obvious downsides: For example, if e.g. the English word "a" were to be extracted as a string for translation (imagine for example `<p>a [[input:ans1]] is a [[input:ans2]]</p>` where the two inputs are dropdown lists), any instance of the letter `a` would be replaced, yielding invalid CASText. As a temporary solution we set a lower limit on the length of extracted strings, but this could still pose issues if e.g. `feedback` gets extracted as a string. In the long run, we would adapt STACK's existing CASText parser (and similarly for maxima).

Due to the omission of maxima code processing, multiple choice questions authored in STACK needed manual post-processing.

Another issue is that the library we use for parsing HTML in the CASText, BeautifulSoup, removes line breaks and standardizes the representation of HTML tags. This means that either, our line breaks will get lost (if we re-insert into a parsed version of the text) or some re-insertions fail (because we extracted `<a download="" href="...">link</a>` when the original content was `<a href='...' download=''>link</a>`).

A different kind of challenge is mathematical terminology and abbreviations, especially if these terms and abbreviations also have meaning in other fields. With sufficient context, e.g. in longer phrases, the translation engine can often find out the correct meaning of the word, but for shorter strings additional context is needed. With DeepL, it is possible to populate a glossary (dictionary) of terms that will be taken into account when translating content. It is also possible to provide a few additional sentences as context. Either way, proof-reading will likely remain necessary even with these potential improvements.

### Results

In our initial use, we successfully translated the _Introduction to working with data_ course into French. File attachments from the course were partially translated manually, partially by using the DeepL document translator, but either way the download and re-upload of the files was a manual process.  This could be automated given a suitable cost-benefit evaluation on a larger corpus of questions.

We have since used this translation framework to translate questions from Italian to English, as were using some questions authored at the University of Trieste to an entrance test to an international master's program in Pakistan and Algeria. Conversely, we have also translated question authored at the ETH in Zurich in to English for use at CalTech.

For these applications, we extended the tool to also handle Moodle question bank exports in addition to course exports.

The code is available here: [https://github.com/IDEMSInternational/moodle-bulk-translator](https://github.com/IDEMSInternational/moodle-bulk-translator)

<div style="display: flex; justify-content: space-between;">
    <figure class="figure" style="width: 48%;">
        <img class="figure-img img-fluid" src="../Images/trieste-elephants-it.png" alt="Question (part) from University of Trieste, Italian">
        <figcaption class="figure-caption">Question (part) from University of Trieste, Italian</figcaption>
    </figure>
    <figure class="figure" style="width: 48%;">
        <img class="figure-img img-fluid" src="../Images/trieste-elephants-en.png" alt="Same question in English, used for entrance test">
        <figcaption class="figure-caption">Same question in English, used for entrance test</figcaption>
    </figure>
</div>


### Enablers

We thank DeepL for agreeing to give IDEMS access to their DeepL API Pro for use with open educational resources, and hope we can extend this agreement to continue working with multi-language STACK content.

### What's Next?

We would like to make our tool easier to configure, and also support input that already contains lang blocks. Furthermore, we would like to add support for translations of strings stored in maxima variables, so that multiple choice and Parson's STACK questions would be translated automatically. Proper parsers for maxima and CASText would be useful here, also to work around the issues caused by the use of search and replace.

Given significant interest and demand, we would give further thought how to leverage the glossary and context features of DeepL.  There is always a pragmatic middle ground between pre-processing data and using features internal to the target API (here DeepL).

While maintenance of single-language questions is already a challenge, maintenance and sync of questions in multiple languages is even more challenging. While multi-language tags help keep all translations in one place, they are unwieldy to work with as a user, and do not notify us when the translations get out of sync (e.g. because a content author updates only one of the languages). It appears that maintaining a phrase dictionary with tooling to generate versions of a question in another or multiple languages from a master version of a question may be a sensible option here, if we can ensure that the produced versions do not need any manual fixes.

Mathematics education is surprisingly international, and while there are important cultural differences between countries the core of pure mathematics remains common ground.  This makes developing high-quality learning materials and then translating them worthwhile.  This is more effective, more efficient, and ultimately more collaborative and than colleagues in each country interpreting educational research and writing materials afresh.    