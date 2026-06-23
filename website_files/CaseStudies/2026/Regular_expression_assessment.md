---
template: casestudy.html

title: Assessing student reasoning in STACK
authors: George Kinnear
shortdescription: A summary of the 2026 Meeting of the STACK Community at the University of Trieste, including programme highlights, major themes, and next steps.
cardimage: 
cardimagealt: 
---

# Assessing student reasoning in STACK

## George Kinnear, The University of Edinburgh

_Re-posted from [https://blogs.ed.ac.uk/georgekinnear/2026/06/23/assessing-student-reasoning-in-stack/](https://blogs.ed.ac.uk/georgekinnear/2026/06/23/assessing-student-reasoning-in-stack/)_

One way to assess small steps of reasoning is using a multiple-choice question (MCQ), where you provide a list of reasons for students to choose from.

In this example, I was asking for the reason why a given series does not converge. I provided various plausible-looking incorrect reasons, along with one correct answer ("s_n diverges").  Notice that I also included a "some other reason" option, where students could enter a reason of their own.

<div class="float-none img-middle">
<figure class="figure">
<img class="figure-img img-fluid" src="../Images/2026_reasoning_convergence_reason.png" alt="Does the series converge? Multiple-choice question with &quot;some other reason&quot; as an option.">
</figure>
</div>

## How to add an "other" option

I implemented this by appending an additional option in the definition of the MCQ in the question variables -- the list of given reasons are permuted, but the "other" option always comes last:
<pre>ta6: append(
  random_permutation([
    [castext("{@a*k+b &lt;= (a+b)*k^2@}, so the series converges by comparison with a \\(p\\)-series"), false],
    ["\\(s_n\\) converges to 0", false],
    ["\\(s_{n+1}\\geq s_1\\) for all \\(n\\in\\mathbb{N}\\) so the partial sums are bounded below", false],
    ["\\(s_n\\) is an increasing sequence", false],
    ["\\(s_n\\) diverges", true]
  ]),
  [["some other reason (please type it below)", false]]
);</pre>

Then in the question text, I used a reveal block to only show the text box (ans7) when the student selects the "other" option in the MCQ (it's the 6th item in the list of options, hence the check for `value="6"`):

<pre>Does the series converge?

[[input:ans5]][[validation:ans5]] because
[[input:ans6]][[validation:ans6]]
[[reveal input="ans6" value="6" ]] [[input:ans7]][[validation:ans7]] [[/reveal]]
[[feedback:prt5]]</pre>

## Grading the "other" answers

To give students a textarea to type in, I had made the text box (ans7) a "Notes" input. Unfortunately, I only realised <i>after</i> the students had completed the quiz, that you can't refer to any Notes inputs in the PRTs for grading! (This means there is no way to automatically grade the Notes input.)

From Stack 4.13.0 There is a "Free-text" input type. With that input type, students get a textarea to type in, <i>and</i> you can access its value as a string in the PRT.

To assess the "other" reasons given by my students, I've constructed some regular expressions - here is what I came up with (explained in more detail below!)

<pre>valid_reasons: [
  "Sn is not bounded.*",
  ".*(s_n|S_n|sn|Sn|partial sum).*(go to infinity|do not have bound|not bounded above|unbounded|unbouneded|grow without a bound|not bounded|no upper bound).*",
  ".*(s_n|S_n|sn|Sn|partial sum).*(\\&amp;rarr\\;|go(es)? to|tends? to|approach(es)?|diverge(s)?|going towards).*(infinity|inf)?.*",
  ".*(terms|Terms|sequence|Sequence).*(does not|do not|doesn.?t).*(approach|approaches|tends? to).*(0|zero).*"
];
valid_reason_given: maplist(lambda([pat], regex_match_exactp(pat, ans7)), valid_reasons);
</pre>

Then in the PRT, I check if the student has selected the "other" option, and if they have, I give them full points if <code>apply("or",valid_reason_given)</code> is true.

## How to come up with the regular expression?

For my quiz, students did not get immediate feedback, so I could see all of the students' answers when I developed the grading approach.

I went to the <a href="https://docs.stack-assessment.org/en/STACK_question_admin/Reporting/#individual-stack-item-analysis">"Analyze responses"</a> page on the STACK question's dashboard, where the "Inputs" tab gives a handy summary of all of the distinct responses for each of the inputs. For ans7, I had a big list with lines like the following:
<pre>1 (  0.29%); &amp;quot;Sn is not bounded, by the boundedness test for series, the series is therefore divergent. &amp;quot;
1 (  0.29%); &amp;quot;The partial sums go to infinity as n goes to infiinty&amp;quot;
1 (  0.29%); &amp;quot;Sn is an increasing sequence that is not bounded above&amp;quot;
1 (  0.29%); &amp;quot;The partial sums do not have bound.&amp;quot;</pre>
I used our in-house LLM service, ELM, to help with the tedious job of reformatting this. I pasted in the full list of lines like the above, and asked
<blockquote>please turn this into a list of maxima strings.

e.g. it should start:

["Sn is not bounded, by the boundedness test for series, the series is therefore divergent.", "The partial sums go to infinity as n goes to infiinty", .... ];</blockquote>
I then pasted that list into Maxima on my desktop, and read through it to separate the entries into two lists - one called <code>true_reasons</code> and one called <code>false_reasons</code> - based on whether I thought the student's reasoning was correct.

I iteratively developed the list of <code>valid_reasons</code> by running the following code, and adding entries to the <code>valid_reasons</code> to cover any cases that were appearing in the <code>not_matched</code> list:
<pre>valid_reasons: [
  "Sn is not bounded.*",
  ".*partial sums.*(go to infinity|do not have bound|not bounded above).*"
]$
not_matched :
  sublist(
    true_reasons,
    lambda([ans7],
      not apply(
        "or",
        maplist(lambda([pat], regex_match_exactp(pat, ans7)), valid_reasons)
      )
    )
  );</pre>

Note that this relies on STACK's <code>regex_match_exactp</code> function which you can find here: <a href="https://github.com/maths/moodle-qtype_stack/blob/f9c01cc70233137d6223233384a570062c124856/stack/maxima/stackstrings.mac#L341">https://github.com/maths/moodle-qtype_stack/blob/f9c01cc70233137d6223233384a570062c124856/stack/maxima/stackstrings.mac#L341</a>

It may also be helpful to give an LLM the list of <code>true_reasons</code> and <code>false_reasons</code>, and ask for a list of regular expressions that matches the true ones but not the false ones - at least as a starting point.

## Concluding thoughts

This was very much a proof of concept, and I only had a small sample of student responses (since out of ~350 students, 80% chose the correct MCQ option and only 27 students chose the "other" option). But I was encouraged by how readily I could make the regular expressions fit to what the students wrote, and I'm interested to see how well this approach would scale up (e.g., if the correct answer is "other"...). It may be useful in that case to borrow some ideas from the existing <a href="https://docs.moodle.org/502/en/Pattern-match_question_type">pattern-match question type</a>, which has already been quite successful (e.g., in physics education). 