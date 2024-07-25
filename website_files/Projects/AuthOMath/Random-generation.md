# Randomly generating mathematical questions

### Konstantina Zerva, The University of Edinburgh, UK

STACK offers the possibility to randomly generate questions and give feedback, which is relevant to each specific random variable. The task presented in the video is a very simple one, and it was deliberately chosen to be simple, because the main focus here is the randomisation and the things that question authors need to consider when creating random variables in a question. 

<center>
<iframe class="embed-responsive-item" width="560" height="315" src="https://www.youtube.com/embed/HKeEqr7ep8g" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</center>

The task asks students to drag the point \(A\) so that the slope of the line is the same as the given value; in this case \(-7/2\). The values of the slope are randomised. 

When the student load the question they all see the same graph. The initial slope of the line is set to \(1\) in the GeoGebra app and the point \(A\) is placed at \((2,2)\). The students can move the point \(A\) along the line and drag it around so that the line changes slopes.

In this example the slop needs to be \(-7/2\). The slope is defined as \[\frac{\text{Change in Y}}{\text{Change in X}}\] so the students can drag the point \(A\) and place it at \(Y=-7\) and \(X=2\)  (point \((2,-7)\) ). Then click the check button and see if their answer is correct or not. Another possible solution here \(Y=7\) and \(X=-2\). 

<div class="float-none img-middle">
<figure class="figure">
<img class="figure-img img-fluid" src="../Images/Correct_slope.png" alt="Correct slope">
<figcaption class="figure-caption">Figure: Defining the correct slope.</figcaption>
</figure></div>

A common mistake that students do is believe that the slope is defined as \[\frac{\text{Change in X}}{\text{Change in Y}}\] so if they put \(A\) at the point \((-7,2)\) they'll receive specific feedback about this mistake. 

<div class="float-none img-middle">
<figure class="figure">
<img class="figure-img img-fluid" src="../Images/Wrong_slope.png" alt="Wrong slope">
<figcaption class="figure-caption">Figure: A common misconception.</figcaption>
</figure></div>

Let's look at the background of the question and how to deal with the randomisation. All the slopes need to be ratios of two integers (e.g. \(3/2\)) and also they shouldn't simplify to an integer (avoid cases like \(4/2=2\)). 

<div class="float-none img-middle">
<figure class="figure">
<img class="figure-img img-fluid" src="../Images/Code.png" alt="An example of Maxima code">
<figcaption class="figure-caption">Figure: An example of Maxima code for creating the variables for this question.</figcaption>
</figure></div>

The variable \(rd\) defines the denominator of the slope. We pick the denominator to be an even number, in this case a power of \(2\). We could also predefine a list of even numbers and randomly pick from the list. 
The variable \(rn\) defines the numerator of the slope. For the numerator we pick the values from a predefined list and these values are all odd numbers. 
We define the slope as \(\dfrac{rn}{rd}\) and in our case all the slopes will be fractions. 

<!--EU funding message and image-->
<div class="disclaimer">
<div class="disclaimer-left"><img src="../Images/AuthOMath_EU.png" alt="AuthOMath Logo, EU flag, Co-founded by the European Union" width="85%" /></div>
<div class="disclaimer-right">The creation of these resources has been (partially) funded by the ERASMUS+ grant program of the European Union under grant No. 2021-1-DE01-KA220-HED-000032031. Neither the European Commission nor the project's national funding agency DAAD are responsible for the content or liable for any losses or damage resulting of the use of these resources.</div>
</div>
</div>