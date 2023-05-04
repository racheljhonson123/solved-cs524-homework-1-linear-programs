Download Link: https://assignmentchef.com/product/solved-cs524-homework-1-linear-programs
<br>



<table width="0">

 <tbody>

  <tr>

   <td width="95">maximize 6<em>x</em><sub>1 </sub><em>x </em>1 <em>;x </em>2 <em>;x </em>3</td>

   <td width="109">2<em>x</em><sub>2 </sub>+ 3<em>x</em><sub>3</sub></td>

   <td width="197">(1)</td>

  </tr>

  <tr>

   <td width="95">subject to:       2<em>x</em><sub>1</sub></td>

   <td width="109">     <em>x</em><sub>2           </sub><em>x</em><sub>3 </sub>+ 2</td>

   <td width="197">(2)</td>

  </tr>

 </tbody>

</table>

0      <em>x <sub>j             </sub></em>3<em>; j </em>2 f1<em>; </em>2<em>; </em>3g                                                            (3)

<ol>

 <li>Given the choice of the solvers Cl p, ECOS, and SCS, which one would you choose? Why?</li>

 <li>Solve the problem using your selected solver. Print the termination status to check whether you have indeed obtained the optimal solution.</li>

 <li>What is the optimal objective value? What is the optimal solution for the variables <em>x</em><sub>1 </sub>and <em>x</em><sub>2</sub>?</li>

 <li>Can you change <em>one </em>of the problem parameters to make the problem infeasible? Solve the new problem in JuMP and print the termination status to demonstrate that the problem is infeasible.</li>

 <li><strong>[2 points] Stigler’s diet. </strong>True story! In 1945, American economist (and future Nobel laureate) George Stigler published a paper investigating the composition of an <em>optimal </em>diet; minimizing total cost while meeting the recommended daily allowance (RDA) of several nutrients. To answer this question, Stigler tabulated a list of 77 foods and their nutrient content for 9 nutrients: calories, protein, calcium, iron, vitamin A, thiamine, riboavin, niacin, and ascorbic acid. Here is what the rst few rows and columns of his table looked like:</li>

</ol>

<table width="0">

 <tbody>

  <tr>

   <td width="163"></td>

   <td width="104">Calories (1000)</td>

   <td width="81">Protein (g)</td>

   <td width="86">Calcium (g)</td>

   <td width="73">Iron (mg)</td>

   <td width="34">. . .</td>

  </tr>

  <tr>

   <td width="163">Wheat Flour (Enriched)</td>

   <td width="104">44.7</td>

   <td width="81">1411</td>

   <td width="86">2</td>

   <td width="73">365</td>

   <td width="34">. . .</td>

  </tr>

  <tr>

   <td width="163">Macaroni</td>

   <td width="104">11.6</td>

   <td width="81">418</td>

   <td width="86">0.7</td>

   <td width="73">54</td>

   <td width="34">. . .</td>

  </tr>

  <tr>

   <td width="163">Wheat Cereal (Enriched)</td>

   <td width="104">11.8</td>

   <td width="81">377</td>

   <td width="86">14.4</td>

   <td width="73">175</td>

   <td width="34">. . .</td>

  </tr>

  <tr>

   <td width="163">…</td>

   <td width="104">…</td>

   <td width="81">…</td>

   <td width="86">…</td>

   <td width="73">…</td>

   <td width="34">…</td>

  </tr>

 </tbody>

</table>

To make calculations easier, Stigler normalized his data so each row shows the nutrients contained in $1’s worth of the given food item. Back then, $1 could buy you quite a lot!

When Stigler posed his diet problem, the simplex method had not yet been invented. In his paper, he wrote: …the procedure is experimental because there does not appear to be any direct method of nding the minimum of a linear function subject to linear conditions.” Nevertheless, through a combination of what he called trial and error, mathematical insight, and agility”, he eventually arrived at a solution: a diet costing only $39.93 per year. Though he confessed: There is no reason to believe that the cheapest combination was found, for only a handful of the [many] possible combinations of commodities were examined.”

In this exercise, you will help Stigler formulate and solve the diet problem as a linear program (LP).

<ol>

 <li>Formulate the optimization problem:</li>

</ol>

What are the decision variables in this problem?

What is the objective of this optimization problem?

What are the constraints of the optimization problem?

Answer both with an explanation in words and with the mathematical model.

1 of 2

CS/ECE/ISyE 524 Introduction to Optimization L. Roald, Spring 2020 <strong>b) </strong>Implement the optimization problem in Julia. To get you started, Stigler’s original data is provided in st i gl er . csv, and the IJulia notebook st i gl er . i pynb imports the data and puts it into a convenient matrix format.

<ol>

 <li>Analyze your result. Did you nd the optimal solution? How does your cheapest diet compare in annual cost to Stigler’s? What foods make up your optimal diet?</li>

 <li>Suppose we wanted to nd the cheapest diet that was also vegetarian. Implement the new problem in Julia and nd the optimal solution. Is this solution cheaper or more expensive than the nonvegetarian solution? Is this as expected?</li>

</ol>

<ol start="3">

 <li><strong>[2 points] Polyhedron modeling. </strong>We saw that the set of <em>x </em>such that <em>Ax b </em>where <em>A </em>2 R <em><sup>m n </sup></em>and <em>b </em>2 R <em><sup>m </sup></em>describes a polyhedron. For each polyhedron below, nd a matrix <em>A </em>and vector <em>b </em>such that <em>Ax b </em>describes the polyhedron. <strong>H int: </strong>since each inequality describes a dierent face, <em>m </em>should be equal to the number of faces. Make sure the inequalities go the right way!</li>

</ol>

(a) Regular cube centered at the origin (b) Regular octahedron centered at the origin with vertices at ( 1<em>; </em>1<em>; </em>1). with vertices at ( 1<em>; </em>0<em>; </em>0), (0<em>; </em>1<em>; </em>0), (0<em>; </em>0<em>; </em>1).

<ol start="4">

 <li><strong>[2 points] Standard form with equality constraints. </strong>Rather than using the standard LP form we saw in class, some prefer using a form where all variables are nonnegative, all constraints are equality constraints, and the cost function is a minimization. So a general LP would look like:</li>

</ol>

minimize         <em>c</em><sup>T </sup><em>x</em>

subject to:           <em>Ax </em>= <em>b                                                                        </em>(4)

<em>x       </em>0

Consider the following LP:

maximize 3<em>z</em><sub>1                </sub><em>z</em><sub>2 </sub><em>z</em>1 <em>;z</em>2 <em>;z</em>3 <em>;z</em>4

subject to:         <em>z</em><sub>1        </sub>+     6<em>z</em><sub>2                    </sub><em>z</em><sub>3        </sub>+      <em>z</em><sub>4                         </sub>3

7<em>z</em><sub>2 </sub>+ <em>z</em><sub>4 </sub>= 5 <em>z</em><sub>3 </sub>+ <em>z</em><sub>4 </sub>2

1      <em>z</em><sub>2          </sub>5<em>;         </em>1      <em>z</em><sub>3          </sub>5<em>;         </em>2      <em>z</em><sub>4          </sub>2

<ol>

 <li>Transform the above LP into the equality-constrained standard form of (4). What are <em>A </em>, <em>b</em>, <em>c</em>, and <em>x</em>? Be sure to explain how the decision variables of your transformed LP relate to those of the original LP.</li>

 <li>Solve both versions of the LP using JuMP and show that you can recover the optimal <em>z </em>and objective value by solving your transformed version of the LP.</li>

</ol>