# About the STACK Project
<!-- ALL-CONTRIBUTORS-BADGE:START - Do not remove or modify this section -->
[![All Contributors](https://img.shields.io/badge/all_contributors-1-orange.svg?style=flat-square)](#contributors-)
<!-- ALL-CONTRIBUTORS-BADGE:END -->

STACK is an assessment system for mathematics, science and related disciplines, designed to enable students to answer questions with a mathematical expression, such as a polynomial. Students are not limited to multiple choice.

Primarily, STACK provides a question type for the [Moodle](https://github.com/maths/moodle-qtype_stack) and [ILIAS](https://github.com/ilifau/assStackQuestion/) learning environments. STACK can be integrated into other systems using [LTI](../Installation/LTI.md).

To see STACK in action, please visit our demonstration site.
<br>
<br>
<button type="button" href="https://stack.maths.ed.ac.uk/demo" class="btn btn-primary">Go to demo site</button>


## Main Features
<div style="width:min(500px,100%);float: right;padding: 15px">
<figure class="figure">
<IMG class="figure-img img-fluid" src="../img/about_prt.png" align="right" style="width:100%" alt="A STACK question on finding roots of a quadratic. The validation box shows how the answer is interpreted. The feedback gives partial marks for getting only one root correct, and refers to the student's answer."/>
  <figcaption class="figure-caption">A typical STACK question. The two roots are randomly generated when the question is viewed. Note the student can see how their answer is interpreted, the feedback is specific to the student's error and partial marks are given.</figcaption>
</figure></div>

<h3> Intelligent randomisation</h3>

Randomising questions is invaluable in ensuring students can practice and reducing sharing of answers. The trick is to reverse-engineer the randomised question from a randomised answer. Computer algebra is invaluable to support this process.


### Validation of answers

Online assessment should assess mathematics skills, not how well students know the specific syntax. For example, penalising a student for answering `sinx` instead of `sin(x)` is not fair. 

<p class="lead ml-5"> Separating validity from assessment is a key design feature pioneered by STACK.</p>

To ensure that students are marked for *mathematical skills* instead of *computer skills*, STACK separates "validity" and "correctness". When a student types an answer, it is interpreted by the CAS and a "validation box" is shown displaying how the student's answer is interpreted. This gives the student a chance to fix any syntax errors before their answer is marked.
### Intelligent marking

STACK uses a Computer Algebra System to mark responses based on mathematical properties, rather than a single "correct" answer. This is invaluable in mathematics, where many expressions, such as \((x-1)(x+1)\) and \(x^2-1\), may be considered equivalent.
<p class="lead ml-5"> Responses are marked based on mathematical properties, rather than a single "correct" answer.</p>

In STACK, answers are marked using a potential response tree with multiple nodes. At each node, the teacher can check various mathematical properties of the student's answer, and can can choose to show feedback or change a student's grade. This opens up a whole array of options:

* Automatic feedback that is specific to the individual student.
* Partial credit.
* Multipart questions with follow-through marking, for example where a mistake in part (a) is carried forward into part (b).
* Give-examples style questions, where there are many correct answers.

### Support for real STEM questions

STACK has a large number of inputs and answer tests to support the diverse needs of users across mathematics and science. This includes support for questions about numerical accuracy, significant figures and scientific units. You can also assess student's ability to reason line-by-line through equivalence reasoning.

To learn more about all of STACKs features, please see our documentation.

## Who uses STACK?

The following applet shows some of the known institutions that use STACK.
<table class="auto" style="max-width:min(200px,100%)">
<tbody>
<tr>
<td><i class="material-icons" style="color:#a52714">stars</i></td>
<td><b>Case studies</b></td>
</tr>
<tr>
<td><i class="material-icons" style="color:#0288d1">place</i></td>
<td><b>General users</b></td>
</tr>
</tbody>
</table>
<iframe src="https://www.google.com/maps/d/u/5/embed?mid=1auYEFzIF752n121gCZKTRW54mSSo6AZ6" width="100%" height="500px"></iframe>

## Development

STACK is currently maintained by:

<div class="container">
<div class="row">
  <div class="col-sm" style="text-align:left">
  <img src="../img/chris.jfif" height="200" alt="Chris Sangwin">
      <h5>Chris Sangwin</h5>
  The University of Edinburgh, UK
  </div>
  <div class="col-sm" style="text-align:left">
  <img src="../img/tim.jpg" height="200" alt="Tim Hunt">
  <h5>Tim Hunt</h5>
  The Open University, UK
  </div>
  <div class="col-sm" style="text-align:left">
  <img src="../img/matti.jpg" height="200" alt="Matti Harjula">
  <h5>Matti Harjula</h5>
  Aalto University, Finland
  </div>
</div>
</div>
<br>

### Translations

STACK is released in many languages, using Moodle's ATOS language system.

  * EN: English (British), by Chris Sangwin (and others)
  * FI: Finnish, by Matti Pauna
  * SV: Swedish, by Mikael Kurula
  * DA: Danish, by Malthe Sporring
  * ES: Spanish, by Victor Hugo Huerta 
  * JA: Japanese, by Yasuyuki Nakamura and Takahiro Nakahara  

German documentation was added in Jan 2019 by Eva Mix and Mario Josupeit of University of Cologne, Germany.
<br>
### ILIAS
STACK has been ported to the plugin [assStackQuestion](github.com/ilifau/assStackQuestion) for the Learning Management System [ILIAS](https://www.ilias.de/)  by:

* Jesus Copado
* Fred Neumann

### GitHub contributors

STACK is open-source and welcomes additions and improvements from its users. Please see the community page on our documentation for more information on contributing to STACK. Contributions can include adding features, submitting translations, sharing publications or reporting bugs.

<table class="table-responsive-xl">
<thead>
<tr>
<th align="center"><a href="https://github.com/sangwinc"><img alt="sangwinc" src="https://avatars3.githubusercontent.com/u/781615?v=4&s=117" width="117"></a></th>
<th align="center"><a href="https://github.com/timhunt"><img alt="timhunt" src="https://avatars0.githubusercontent.com/u/138653?v=4&s=117" width="117"></a></th>
<th align="center"><a href="https://github.com/aharjula"><img alt="aharjula" src="https://avatars1.githubusercontent.com/u/980957?v=4&s=117" width="117"></a></th>
<th align="center"><a href="https://github.com/germanvaleroelizondo"><img alt="germanvaleroelizondo" src="https://avatars2.githubusercontent.com/u/2671923?v=4&s=117" width="117"></a></th>
<th align="center"><a href="https://github.com/malthesporring"><img alt="malthesporring" src="https://avatars0.githubusercontent.com/u/52042426?v=4&s=117" width="117"></a></th>
<th align="center"><a href="https://github.com/alcarola"><img alt="alcarola" src="https://avatars1.githubusercontent.com/u/1645276?v=4&s=117" width="117"></a></th>
</tr>
</thead>
<tbody><tr>
<td align="center"><a href="https://github.com/sangwinc">sangwinc</a></td>
<td align="center"><a href="https://github.com/timhunt">timhunt</a></td>
<td align="center"><a href="https://github.com/aharjula">aharjula</a></td>
<td align="center"><a href="https://github.com/germanvaleroelizondo">germanvaleroelizondo</a></td>
<td align="center"><a href="https://github.com/malthesporring">malthesporring</a></td>
<td align="center"><a href="https://github.com/alcarola">alcarola</a></td>
</tr>
</tbody></table>
<table>
<thead>
<tr>
<th align="center"><a href="https://github.com/iandavidwild"><img alt="iandavidwild" src="https://avatars2.githubusercontent.com/u/2386283?v=4&s=117" width="117"></a></th>
<th align="center"><a href="https://github.com/MaximKraev"><img alt="MaximKraev" src="https://avatars3.githubusercontent.com/u/575940?v=4&s=117" width="117"></a></th>
<th align="center"><a href="https://github.com/vesal"><img alt="vesal" src="https://avatars3.githubusercontent.com/u/826392?v=4&s=117" width="117"></a></th>
<th align="center"><a href="https://github.com/mloginov"><img alt="mloginov" src="https://avatars3.githubusercontent.com/u/2392299?v=4&s=117" width="117"></a></th>
<th align="center"><a href="https://github.com/georgekinnear"><img alt="georgekinnear" src="https://avatars1.githubusercontent.com/u/30723394?v=4&s=117" width="117"></a></th>
<th align="center"><a href="https://github.com/christianp"><img alt="christianp" src="https://avatars0.githubusercontent.com/u/19513?v=4&s=117" width="117"></a></th>
</tr>
</thead>
<tbody><tr>
<td align="center"><a href="https://github.com/iandavidwild">iandavidwild</a></td>
<td align="center"><a href="https://github.com/MaximKraev">MaximKraev</a></td>
<td align="center"><a href="https://github.com/vesal">vesal</a></td>
<td align="center"><a href="https://github.com/mloginov">mloginov</a></td>
<td align="center"><a href="https://github.com/georgekinnear">georgekinnear</a></td>
<td align="center"><a href="https://github.com/christianp">christianp</a></td>
</tr>
</tbody></table>
<table>
<thead>
<tr>
<th align="center"><a href="https://github.com/birdanja"><img alt="birdanja" src="https://avatars2.githubusercontent.com/u/45361170?v=4&s=117" width="117"></a></th>
<th align="center"><a href="https://github.com/gustavdelius"><img alt="gustavdelius" src="https://avatars3.githubusercontent.com/u/1340713?v=4&s=117" width="117"></a></th>
<th align="center"><a href="https://github.com/gitnovisat5"><img alt="gitnovisat5" src="https://avatars3.githubusercontent.com/u/21970576?v=4&s=117" width="117"></a></th>
<th align="center"><a href="https://github.com/whanrott"><img alt="whanrott" src="https://avatars0.githubusercontent.com/u/10232136?v=4&s=117" width="117"></a></th>
<th align="center"><a href="https://github.com/JonathanWatkins"><img alt="JonathanWatkins" src="https://avatars3.githubusercontent.com/u/1997938?v=4&s=117" width="117"></a></th>
<th align="center"><a href="https://github.com/inthewaves"><img alt="inthewaves" src="https://avatars2.githubusercontent.com/u/26474149?v=4&s=117" width="117"></a></th>
</tr>
</thead>
<tbody><tr>
<td align="center"><a href="https://github.com/birdanja">birdanja</a></td>
<td align="center"><a href="https://github.com/gustavdelius">gustavdelius</a></td>
<td align="center"><a href="https://github.com/gitnovisat5">gitnovisat5</a></td>
<td align="center"><a href="https://github.com/whanrott">whanrott</a></td>
<td align="center"><a href="https://github.com/JonathanWatkins">JonathanWatkins</a></td>
<td align="center"><a href="https://github.com/inthewaves">inthewaves</a></td>
</tr>
</tbody></table>
<table>
<thead>
<tr>
<th align="center"><a href="https://github.com/Smibu"><img alt="Smibu" src="https://avatars0.githubusercontent.com/u/7945133?v=4&s=117" width="117"></a></th>
<th align="center"><a href="https://github.com/potslinux"><img alt="potslinux" src="https://avatars1.githubusercontent.com/u/42441713?v=4&s=117" width="117"></a></th>
<th align="center"><a href="https://github.com/aspark21"><img alt="aspark21" src="https://avatars1.githubusercontent.com/u/4015496?v=4&s=117" width="117"></a></th>
<th align="center"><a href="https://github.com/dthies"><img alt="dthies" src="https://avatars1.githubusercontent.com/u/5671730?v=4&s=117" width="117"></a></th>
<th align="center"><a href="https://github.com/destitutus"><img alt="destitutus" src="https://avatars3.githubusercontent.com/u/1736475?v=4&s=117" width="117"></a></th>
<th align="center"><a href="https://github.com/HuongNV13"><img alt="HuongNV13" src="https://avatars1.githubusercontent.com/u/11548406?v=4&s=117" width="117"></a></th>
</tr>
</thead>
<tbody><tr>
<td align="center"><a href="https://github.com/Smibu">Smibu</a></td>
<td align="center"><a href="https://github.com/potslinux">potslinux</a></td>
<td align="center"><a href="https://github.com/aspark21">aspark21</a></td>
<td align="center"><a href="https://github.com/dthies">dthies</a></td>
<td align="center"><a href="https://github.com/destitutus">destitutus</a></td>
<td align="center"><a href="https://github.com/HuongNV13">HuongNV13</a></td>
</tr>
</tbody></table>
<table>
<thead>
<tr>
<th align="center"><a href="https://github.com/jason-platts"><img alt="jason-platts" src="https://avatars0.githubusercontent.com/u/793158?v=4&s=117" width="117"></a></th>
<th align="center"><a href="https://github.com/lucaboesch"><img alt="lucaboesch" src="https://avatars0.githubusercontent.com/u/377279?v=4&s=117" width="117"></a></th>
<th align="center"><a href="https://github.com/mpetrowi"><img alt="mpetrowi" src="https://avatars0.githubusercontent.com/u/1470849?v=4&s=117" width="117"></a></th>
<th align="center"><a href="https://github.com/m-r-k"><img alt="m-r-k" src="https://avatars1.githubusercontent.com/u/2588881?v=4&s=117" width="117"></a></th>
<th align="center"><a href="https://github.com/kabalin"><img alt="kabalin" src="https://avatars2.githubusercontent.com/u/329780?v=4&s=117" width="117"></a></th>
<th align="center"><a href="https://github.com/sgparry"><img alt="sgparry" src="https://avatars0.githubusercontent.com/u/4488509?v=4&s=117" width="117"></a></th>
</tr>
</thead>
<tbody><tr>
<td align="center"><a href="https://github.com/jason-platts">jason-platts</a></td>
<td align="center"><a href="https://github.com/lucaboesch">lucaboesch</a></td>
<td align="center"><a href="https://github.com/mpetrowi">mpetrowi</a></td>
<td align="center"><a href="https://github.com/m-r-k">m-r-k</a></td>
<td align="center"><a href="https://github.com/kabalin">kabalin</a></td>
<td align="center"><a href="https://github.com/sgparry">sgparry</a></td>
</tr>
</tbody></table>
<table>
<thead>
<tr>
<th align="center"><a href="https://github.com/t-schroeder"><img alt="t-schroeder" src="https://avatars0.githubusercontent.com/u/24255259?v=4&s=117" width="117"></a></th>
<th align="center"><a href="https://github.com/dhilsen"><img alt="dhilsen" src="https://avatars0.githubusercontent.com/u/22775691?v=4&s=117" width="117"></a></th>
<th align="center"><a href="https://github.com/mjosupei"><img alt="mjosupei" src="https://avatars3.githubusercontent.com/u/45790381?v=4&s=117" width="117"></a></th>
</tr>
</thead>
<tbody><tr>
<td align="center"><a href="https://github.com/t-schroeder">t-schroeder</a></td>
<td align="center"><a href="https://github.com/dhilsen">dhilsen</a></td>
<td align="center"><a href="https://github.com/mjosupei">mjosupei</a></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody></table>





## Contributors ✨

Thanks goes to these wonderful people ([emoji key](https://allcontributors.org/docs/en/emoji-key)):

<!-- ALL-CONTRIBUTORS-LIST:START - Do not remove or modify this section -->
<!-- prettier-ignore-start -->
<!-- markdownlint-disable -->
<table>
  <tr>
    <td align="center"><a href="https://github.com/malthesporring"><img src="https://avatars0.githubusercontent.com/u/52042426?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Malthe Sporring</b></sub></a><br /><a href="#a11y-malthesporring" title="Accessibility">️️️️♿️</a> <a href="https://github.com/malthefogsporring/malthesrepo/commits?author=malthesporring" title="Documentation">📖</a> <a href="#eventOrganizing-malthesporring" title="Event Organizing">📋</a> <a href="#translation-malthesporring" title="Translation">🌍</a> <a href="#tutorial-malthesporring" title="Tutorials">✅</a> <a href="#video-malthesporring" title="Videos">📹</a></td>
  </tr>
</table>

<!-- markdownlint-enable -->
<!-- prettier-ignore-end -->
<!-- ALL-CONTRIBUTORS-LIST:END -->

This project follows the [all-contributors](https://github.com/all-contributors/all-contributors) specification. Contributions of any kind welcome!