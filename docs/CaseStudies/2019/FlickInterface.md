# A Flick Interface for Maths Input

#### Graduate School of Informatics, Nagoya University, Japan

Yasuyuki Nakamura

Sangensha LLC., Japan

Takahiro Nakahara

### Abstract

Typing mathematical expressions into mobile devices can be time-consuming. To solve this problem, developers at Nagoya University are developing a "flick interface" for STACK, similar to the popular Japanese keyboard mode. Students can pick a common integer or variable and flick in a direction to quickly turn, for example, \(x\) into \(\sqrt(x)\). A survey of usability suggests students prefer this input type to their traditional keyboard.

### Motivation

As smartphones become increasingly used in schools and universities, it is important to find a reliable way to input mathematical expressions. Inputting mathematics on a computer is not a problem, but on smartphones and other mobile devices it can be much more time-consuming. For example, to type an answer to the question "Expand (x+2)\(x+3)", students have to enter the expression `x^2+5*x+6` into the answer space. On a mobile device, this requires several switches between the alphabetical and numerical views of the keyboard, resulting in 19 key touches for this simple answer. 

Recently, a flick keyboard for Japanese characters has become very popular in Japan, especially amongst young students. Japanese has three character systems. Hiragana is mostly used for simple and native Japanese words, katakana mostly for foreign words and kanji for all other words. The keyboard shows only a limited number of hiragana[^hiragana] characters, but students can hold and "flick" on a key to choose a similar character. Characters are grouped together by sound, for example grouping together na, ni, nu, ne and no. The keyboard will then suggest related kanji and/or katakana characters that share similar sounds. It was the popularity of this keyboard that motivated the developers to create a similar interface for inputting mathematics, as a STACK input type.

### Execution
<div class="float-right img-tall">
<figure class="figure">
<img class="figure-img img-fluid" src="../Images/Flick_interface_compressed.png" alt="A STACK question is answered using a mobile keyboard. '2' is held down, displaying options for '2 to the power of', '2y', 'something to the power of 2' and '2x'.">
  <figcaption class="figure-caption">Figure: The flick interface in action.
</figcaption>
</figure></div>
The flick interface was developed by Yasuyuki Nakamura and Takahiro Nakahara, funded by a grant from the Japan Society for the Promotion of Science. Like the Japanese character keyboard, students are faced with a small set of common inputs. Students can switch between numerical values and common variables by pressing "123" and "xy", respectively, or see a full keyboard view by clicking the keyboard logo. Pressing on a number reveals some common manipulations, and students can then flick in one direction to turn, for example, "2" into "2x". The input is compatible with normal keyboards, and will automatically be selected for the  type of device being used. 



The interface is programmed in JavaScript to minimise the dependency on mobile device operating systems. The interface uses [MathDox](http://mathdox.org/) to describe expressions, and the input is then converted to the Maxima format by a conversion filter previously created by the developers. Developing an interface suitable for all different screen sizes was one of the biggest challenges of the project, but now the interface is suitable for most devices of sizes around 5-6 inches.

### Results

The flick interface is estimated to significantly reduce the number of keypresses required to type an expression. The following table shows an estimated comparison for a few common expressions [1].

| Mathematical expression       | Direct input taps | Flick input taps |
| ----------------------------- | ----------------- | ---------------- |
| \(x^2+5x+6\)                    | 19                | 8                |
| \(3x^2-\frac{2x}{(x^2+1)^2}\) | 36                | 13               |
| \(2x \cos(x^2)\)                | 23                | 7                |

<figcaption class="figure-caption text-center">Table: A comparison of the number of taps needed to type an expression.
</figcaption>


To analyse the usability of the interface, the developers conducted a usability test at Nagoya University, Japan. 29 students where asked to enter five common maths expressions by using both a traditional keyboard and the new flick input keyboard. After they entered these math expressions, they were given a survey on usability and satisfaction levels. The survey questions were based on the following five parameters, originally from Jakob Nielsen’s five goals of usability [2]: learnability, efficiency, difficulty or ease in making corrections, rememberability, and the intent to reuse. For each parameter, students were asked to give each input type a score from 0.0 to 5.0. The following table shows the results [1], including both the averages, as well as the standard deviations in parentheses. The survey suggests that the usability and satisfaction levels are higher when the flick input method is used to enter mathematical expressions, rather than the direct input method.

| Question                                              | Direct input score | Flick input score |
| ----------------------------------------------------- | ------------------ | ----------------- |
| It is easy to learn how to input math.                | 3.0 (1.2)          | 3.5 (1.0)         |
| I can input math quickly and easily.                  | 2.6 (1.1)          | 3.2 (1.3)         |
| It is not confusing and easy to correct.              | 3.0 (1.2)          | 3.1 (1.1)         |
| I remember the method that I learnt at the rehearsal. | 3.0 (1.1)          | 3.1 (1.1)         |
| I will use this method to input math the next time    | 2.9 (1.3)          | 3.2 (1.4)         |

<figcaption class="figure-caption text-center">Table: Responses from the interface survey. Standard deviations are given in parentheses.
</figcaption>

### What's Next?

The next step for the developers is to merge the flick interface into STACK as a new input type. This will include refactoring the flick interface code and working with STACK developers to best implement it into the question type.

### References

[1] Y. Nakamura and T. Nakahara. *A new mathematics input interface with flick operation for mobile devices.* 15(2), 2017.

[2] J. Nielsen. *Usability Engineering.* Morgan Kaufmann Publishers Inc., San Francisco, CA, USA, 1993.

<nav aria-label="...">
  <ul class="pagination pagination-lg justify-content-center" style="margin-top:2em">
    <li class="page-item"><a href="../Adaptive" class="page-link"><i class="fa fa-arrow-left"></i>&nbsp;Adaptive Self-learning Exercises</a></li>
    <li class="page-item"><a href="../Maseno" class="page-link" >Innovating Education in Maseno, Kenya&nbsp;<i class="fa fa-arrow-right"></i></a></li>
  </ul>
</nav>
