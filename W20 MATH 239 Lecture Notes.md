---
geometry:
  - top=2.54cm
  - bottom=2.54cm
  - left=2.54cm
  - right=2.54cm
linestretch: 1
fontsize: 12pt

title: MATH 239 Introduction to Combinatorics Lecture Notes Winter 2020
author: Jinyu (Leo) Chen
header-includes:
  - \usepackage{amsmath}
  - \usepackage[makeroom]{cancel}
---


**Instructor:** Alexander Nelson

**Combinatorics** is the mathematics of discrete objects. The content of
this course is split evenly between two areas:

+ *algebraic Enumeration:* Bijections, Formal Power Series, Sums and Products,
Strings and Compositions, Recurrence Relations.
+ *Graph Theory*: Isomorphism, Trees, Bipartite Graphs, Connectedness,
Planarity, Matchings, Colouring.

**Marking Scheme:**

+ 10 assignments: **20%**
+ Mid-term: **20%**
+ Final: **60%**


\newpage

# Chapter 1 Introduction to Combinatorics
## 1.1 Composition of Integers //Jan 6^th^ Lecture 1

Definition 1.1.1.
  ~ A **composition** of an integer $n \geq 0$ is a sequence of integers ${m_1,
    \ldots,m_k},\ m_i > 0,\ k \leq n$ such that $$m_1+\cdots+m_k=n$$ where
    $m_i$ are called "parts" and $n$ is called "weight".


**Typical Questions:**

- How many compositions of a number $n$ are there?
- How many compositions of a number $n$ are there with exactly $k$ *parts*?
- How many compositions of a number $n$ are there where all *parts* are odd?  

Example 1.1.2.
  ~ A **binary string** of length $n$ is a sequence $a_1,\ldots,a_n,\ a_i\in\{0,1\}$.

**Question:** How many compositions of a binary string of length n are there?
**Answer:** There are $2^n$ compositions. *proof.* Clearly, each digit in the
string is of the set $\{0,1\}$ and there are $n$ dights. So we have
$$\underbrace{|\{0,1\} \times \cdots \times \{0,1\}|}_{\text{n times}} = {|\{0,1\}|}^n = 2^n$$

## 1.2 Cartesian Sums and Products
Let $A,B$ be sets

+ **Union**: $A \cup B = \{x \mid x \in A \text{ or } x \in B\}$
+ **Cardinality**: $\left| A \right| = \text{number of elements of the set }A$
+ **Cartesian Product**: the **Cartesian Product** of two sets
  $A \text{ and } B$, denoted $A \times B$, is the set of all *ordered pairs*
  $(a,b)$ where $a$ is in $A$ and $b$ is in $B$. That is, $$ A \times B = \{\,
  (a,b) \mid a \in A \text{ and }b \in B\,\}.$$
+ **Cartesian Power**:
    + The **Cartesian Square** of a set $X$ is the Cartesian product
    $X^2 = X \times X$.
    + Expands this idea, we can define the **n-ary Cartesian Power** of a set
      $X$ as $$X^n = \underbrace{X \times X \times \cdots \times X }_{n} = \{
       (x_1,\ldots,x_n) \mid x_i \in X,\  1 \leq i \leq n \}.$$

Example 1.2.1.
  ~ Let $A = \{1,2\},\ B = \{3,4,5\}$. We have $A \times B = \{(1,3),(1,4),(1,5)
    ,(2,3),(2,4),(2,5)\}$.
Example 1.2.2.
  ~ Let $A = \{1,2,3,4,5,6\}$, i.e. a dice with 6 sides. We throw it 3 times,
    then how many possible results can we get (order matters)?
**Answer:** $|A^3| = {|A|}^3 = 6^3 = 216$ possible results.

**Remarks:**

1. $|A \times B| = |A| \cdot |B|$\
2. $A^0 = \{()\} \ \text{where () is the empty list/tuple}$.
3. $|A^n| = \underbrace{|A| \times |A| \times \, \cdots \, \times |A|}_{n} = (|A|)^n = |A|^n$
4. By extension, $|A^0| = {|A|}^0 = 1$.
5. $\text{Let } S = A \cup B \text{. If } A \cap B = \emptyset \text{, then }
   |S| = |A| + |B|$.

## 1.3 Permutations and Combinations

Definition 1.3.1.
  ~ A **permutation** is the rearrangement of the elements of a set into a
    sequence or order. The number of **permutations** of a set of *n* objects
    is given by $$n \times (n - 1) \times \cdots \times 1 = n!.$$

Definition 1.3.2.
  ~ A **k-subset** is a subset of size *k*.

Question 1.3.3.
  ~ How many *k-subsets* of a set with size *n* have?

**Answer:** Consider a more specific case: \
How many 4-subsets of a set with size 6 are there?

+ The first *position* is available for 6 possible choices.
+ The second *position* is available for $6-1=5$ possible choices.
+ The third *position* is available for $6-2=4$ possible choices.
+ The fourth *position* is available for $6-3=3$ possible choices.

So we now have $6 \times 5 \times 4 \times 3$ possible permutations. Notice
for sets, $\{1,2\} = \{2,1\}$, that is, the order does not matter. For
each permutation, we have 4! repetitive arrangements and to eliminate them,
we need to divide them with 4!. So, the answer is given by:
$$ \frac{6\times 5\times 4\times 3}{4!} = 15$$

More generally, the number of **k-subsets** of a set with size *n* is:
$$ \begin{aligned}
    \binom nk
    &= \frac{n\times (n-1)\times \cdots \times (n-k+1)}{k!} \\
    &= \frac{n\times (n-1)\times \cdots \times (n-k+1) \times (n-k)
      \times (n-k-1) \times \cdots \times 1}{k! \times (n-k) \times (n-k-1)
      \times \cdots \times 1}\\
    &= \frac{n!}{k!(n-k)!}\\
    &\text{where }n,k \in \mathbb{Z}.
   \end{aligned}$$

Each **k-subset** is called a **k-combination** and the number of
**k-combinations** is given by the formula above.

**Remarks:**

1. $\binom nk = 0 \text{ if } k > n.$
2. $\binom n0 = 1 \text{ since } 0! = 1.$
3. $\binom nk = \binom n{n-k}.$

## 1.4 Bijections

Definition 1.4.1.
  ~ *f* is **injective/one-to-one** if for any $x_1, x_2 \in S$,
    $$f(x_1) = f(x_2)\Rightarrow x_1 = x_2.$$
  ~ **surjective/onto** if for all $y \in T$ there exists an element $x \in S$
    such that $f(x) = y$.
  ~ **bijective/one-to-one correspondence** if *f* is both injective and surjective.

\newpage

## 1.5 Bijective Proof Examples //Jan 8^th^ Lecture 2

Definition 1.5.1.
  ~ A **Combinatorial Proof** is either:
  + A proof by **double counting**.
  + A **bijective proof**.

**Motivation:** we will use a new proof method to prove following properties
as oppose to the algebra method. That is, to show LHS and RHS have equal
quantity, we construct two sets, say *S* and *T*, which have their cardinalities
 corresponds to quantity of LHS and RHS. Then, if we can construct an
function $f: \, S \rightarrow T$ and it has its **inverse function**
*(T has an one-to-one correspondence with S and vice versa)* and thus it is
a **bijection function** between *S* and *T*, then we can conclude that set *S*
and set *T* has the same cardinality and hence LHS is equivalent to RHS. This
proof method is called **Bijective Proof**. We will see **double-counting proof**
examples next lecture.

Proposition 1.5.2.
  ~ $$\binom nk = \binom n{n-k} \text{ for all } 0 \leq k \leq n.$$

Example 1.5.3.
  ~ $$\binom {5}{2} = \binom {5}{3}.$$


*We will showcase a bijective proof for this proposition.*\
**Proof Idea:** "Picking *k*-subset from set with size n is like not picking
($n-k$)-subsets".\


*Proof.* Let
  $$\begin{aligned}
    &S = \{k\text{-element subset of } \{1,\cdots ,n\} \}\\
    &T = \{(n-k)\text{-element subset of } \{1,\cdots ,n\} \}.
    \end{aligned}$$    
  Consider a function $\phi : S\rightarrow T$ (*mapping elements in S to elements in T*)
  defined by $$\phi (x) = \{1,2, \cdots ,n\} \backslash x \text{ for each } x \in S.$$

  Note that if $x \in S$ then $|x| = k$ so
  $$ |\phi (x)| = |\{1, \cdots ,n\}| - |x| = n-k \text{ so } \phi (x) \in T.$$
  Also, we have
  $$  \begin{aligned}
  \phi (\phi (x)) &= \{1,\cdots ,n\}\,\backslash\,(\{1, \cdots, n\} \backslash x)\\
                  &= x \text{ for all } x \in S\text{ and }x \in T.
      \end{aligned}$$
  Then, we've constructed a *bijection* between *S* and *T* and thus $|S|=|T|$.
  Therefore, $LHS = RHS$.

Proposition 1.5.4.
  ~ $$\binom nk = \binom {n-1}{k} + \binom {n-1}{k-1} \text{ for all } n\geq 1
      \text{ and } k \geq 1.$$

*We will showcase a bijective proof for this proposition.*\

*Proof.* Let
  $$\begin{aligned}
    &S = \{k\text{-element subset of } \{1,\cdots ,n\} \}\\
    &T = \{\text{Subsets of } \{1,\cdots ,n-1\} \text{ with size } k \text{ or } k-1\}.
    \end{aligned}$$  
  Note that $|S| = \binom nk,\ |T| = \binom {n-1}k + \binom {n-1}{k-1}$.

  Consider a function $\phi : S\rightarrow T$, defined by
    $$\phi(x) =
      \begin{cases}
        x,& \text{if } n\notin x\\
        x\backslash \{n\}, &\text{otherwise}.
      \end{cases}$$
  Since $|\phi(x)| = k \text{ or } k-1\text{, we have }\phi(x) \in T \text{ so }
  \phi \text{ is a function from } S \text{ to } T$.

  Consider a function $\psi : T\rightarrow S$, defined by
    $$\psi(y) =
      \begin{cases}
        y,& \text{if } |y| = k\\
        y\cup\{n\}, &\text{otherwise}.
      \end{cases}$$
  Since $|\psi(y)| = k \text{, we have } \psi(y) \in S \text{ so } \psi \text{
   is a function from } T \text{ to } S$.\


  We now show that $\psi$ is the inverse of $\phi$.

  Let $x\in S$.\
  If $n \in x, \ \psi(\phi(x)) = \psi(x\backslash \{n\}) =
  (x\backslash \{n\})\cup \{n\} = x$ since $|x\backslash \{n\}| = k-1$.\
  If $n \notin S, \ \psi(\phi(x)) = \psi(x) = x$.

  Let $y\in T$.\
  If $|y| = k, \ \phi(\psi(y)) = \psi(y) = y$.\
  If $|y| = k-1, \ \phi(\psi(y)) = \psi(y\cup \{n\}) = (y\cup \{n\})\backslash \{n\}=y$.

  Therefore$\,\phi\text{ is the inverse of }\psi \text{ , so } \phi
    \text{ is a bijection, so } |S| = |T| \text{ , so }$
    $$\binom nk = \binom {n-1}{k} + \binom {n-1}{k-1}.$$

\newpage

## 1.6 Double-counting Proof Examples//Jan 10^th^ Lecture 3

Theorem 1.6.1. (Binomial Theorem)
  ~ $$(1+x)^n = \sum_{k=0}^n {n \choose k}x^k.$$

Example 1.6.2.
  ~ $$\begin{aligned}
       (1+x)^4 &= {4 \choose 0}x^0 + {4 \choose 1}x^1 + {4 \choose 2}x^2 +
                  {4 \choose 3}x^3 + {4 \choose 4}x^4 \\
               &= 1+4x+6x^2+4x^3+x^4. \\
      \end{aligned}$$

*Proof using induction.* Since $(1+x)^0 = 1 = {0 \choose 0} =\sum_{k=0}^0
  {k \choose 0}x^k$, it is true for $n=0$. Suppose that $n\geq 1$ and that
  the statement holds for $n-1$.
  $$\begin{aligned}
     (1+x)^n &= (1+x)(1+x)^{n-1} \\
             &= (1+x)\sum_{k=0}^{n-1} {n-1 \choose k}x^k \\
             &= \sum_{k=0}^{n-1} {{n-1} \choose k}x^{k} +
                x\cdot \sum_{k=0}^{n-1} {{n-1} \choose {k}}x^{k} \\
             &= \sum_{k=0}^{n-1} {{n-1} \choose {k}}x^{k} +
                \sum_{k=0}^{n-1} {{n-1} \choose {k}}x^{k+1} \\
             &= \sum_{k=0}^{n-1} {{n-1} \choose {k}}x^{k} +
                \sum_{k=1}^{n} {{n-1} \choose {k-1}}x^{k}. \\
             &= {n-1 \choose 0}x^0 + \sum_{k=1}^{n-1} {{n-1} \choose {k}}x^{k} +
                \sum_{k=1}^{n-1} {{n-1} \choose {k-1}}x^{k} +
                {{n-1} \choose {n-1}}x^{n} \\
             &= 1+\left(\sum_{k=1}^{n-1}
                    \left({{n-1} \choose {k}} + {{n-1} \choose {k-1}}\right)x^{k}
                  \right) + x^n\\
             &= 1 + \left(
                      \sum_{k=1}^{n-1} {{n} \choose {k}}x^{k}
                    \right) + x^n\\
             &= {n \choose 0} x^0 + \left(
                                      \sum_{k=1}^{n-1} {{n} \choose {k}}x^{k}
                                    \right) + {n \choose n}x^n\\
             &= \sum_{k=0}^{n} {{n} \choose {k}}x^{k}.
    \end{aligned}$$

**Note:** The **Binomial Theorem** can be also stated as
  $$(1+x)^n = \sum_{k\geq 0} {{n} \choose {k}}x^{k}.$$

Proposition 1.6.3.
  ~ If $0\leq k \leq n$, then $$ {n \choose k}=\frac{n!}{k!(n-k)!}.$$

*We will showcase a proof using double-counting for this proposition.*

*Proof.* Let *S* be the set of all ordered k-tuples of distinct elements from $\{1,\ldots,n\}$.

  *One way of counting:*
  To choose *k*-tuple $(x_1,x_2,\ldots,x_k) \in S$, we make one of *n* choices
  from $x_1$, then one of $n-1$ choices for $x_2$, and so on, ending with one of
  $n-k+1$ choice for $x_k$. So $|S|=n(n-1)(n-2)\cdots (n-k+1)$.

  *Another way of counting:*
  Alternatively, we can describe an element $(x_1,\ldots,x_k)$ of *S* by first
  specifying the set $\{x_1,\ldots,x_k\}$, then giving the order its elements
  appear. There are ${n \choose k}$ choices for the set, and $k!$ orderings of
  the set, so $|S|=k!{n \choose k}$.

  Therefore $n(n-1)\cdots (n-k+1)=|S|=k!{n \choose k}$.\
  Also since
  $$\text{LHS} = \frac{n(n-1)\ldots 2\times 1}{(n-k)\times \cdots \times 2 \times 1}
    = \frac{n!}{(n-k)!},$$
  we have:
  $$\begin{aligned}
      &\frac{n!}{(n-k)!} = k!{n \choose k}\\
      &{n \choose k} = \frac{n!}{k!(n-k)!}.
    \end{aligned}$$

Proposition 1.6.4.
  ~ If $m,n \geq 0$ and $0\leq k \leq m+n$, then
  $$ {m+n \choose k} = \sum_{i=0}^k {m \choose i}{n \choose k-i}.$$

*We will showcase a proof using double-counting for this proposition.*

*Proof (Model of formality of Assignments).* Let *S* be the collection of *k*-
  element subsets of $\{1,\ldots ,m+n\}$.

  *First way:*
  By definition, $|S|={m+n \choose k}$.

  *Second way:*
  For each *i*, $0 \leq i \leq k$, let $S_i$ be the number of sets in *S*
  containing exactly *i* elements of $\{1,\ldots ,m\}$ and exactly $(k-i)$
  elements of $\{m+1,\ldots ,m+n\}$. Since each set in *S* has size *k*, the
  set *S* is the disjoint union of $S_i$. Thus
  $$ |S| = \sum_{i=0}^{k} |S_i|.$$
  For each $i$, to specify an element of $S_i$, we need to give an $i$-element
  subset of $\{1,\ldots ,m\}$ and a $(k-i)$-element subset of $\{m+1,\ldots ,m+n\}$,
  so
  $$ |S_i| = {m \choose i}{n \choose {k-i}}.$$

  Thus
  $$ {m+n \choose k} = |S| = \sum_{i=0}^{k} {m \choose i}{n \choose {k-i}}.$$

\newpage

## 1.7 Generating Functions //Jan 13^th^ Lecture 4

We want to count how many stars can we get when combining two pieces
from set $A$ and $B$. To count the stars, we found that:
$$\overbrace{(x^1+x^2+x^2+x^0)}^{\Phi_{A}(x)}\overbrace{(x^1+x^2)}^{\Phi_{B}(x)}
 = 1x^1+2x^2+3x^3+2x^4$$
Notice that the relation between coefficients and its variables,
it follows fact that:

  + There is 1 star: 1 occurrence --> $1x^1$
  + There are 2 stars: 2 occurrences --> $2x^2$
  + There are 3 stars: 3 occurrences --> $3x^3$
  + There are 4 stars: 2 occurrences --> $2x^4$

The way we count stars in an element of $A \text{ or } B$ is called a
**weight function**.

Definition 1.7.1.
  ~ Given a set $S$, and a "weight" function $w:S\rightarrow \mathbb{Z}_{\geq 0}$,
    we define **generating function** to be
    $$ \Phi_{S}(x) = \sum_{\sigma \in S}x^{W(\sigma)}$$
    which also called the **generating series** for $S$ with respect to $w$.

Example 1.7.2.
  ~ $$S = \{\text{cow, sheep, chicken, duck, goose}\}, w(\sigma) = \text{ \# of legs}.$$
*Answer:*
  $$\begin{aligned}
      \Phi_{S}(x) &= x^4+x^4+x^2+x^2+x^2\\
                  &= 2x^4+3x^2.
    \end{aligned}$$

Example 1.7.3.
  ~ $$S = \mathbb{Z}_{>0}, w(\sigma) = \text{\# of decimal digits of }\sigma.$$
*Answer:*
$$\begin{aligned}
    \Phi_{S}(x) &= 9x^1+90x^2+900x^3+\cdots\\
                &= 9x(1+10x+100x^2+\cdots)\\
                &= \frac{9x}{1-10x}.
  \end{aligned}$$

Proposition 1.7.4.
  ~ If $S$ is a set and $w$ is a weight function, (i.e. $w$ is a function from
    $S$ to $\{1,2,\ldots\}$), then for each $k\geq 0$, the coefficient of $x^k$
    in $\Phi_{S}(x)$ is equal to the number of element of $S$ whose weight is $k$.\
    i.e.
    $$\sum_{\sigma \in S}x^{W(\sigma)}=\sum_{k\geq 0}a_k x^{k}$$
    where $a_k$ is the number of element of weight $k$ in $S$.


*"A generating function is a clothesline upon which we hang a sequence
of coefficients for display"* -wilf

Proposition 1.7.5.
  ~ Let $w$ be a weight function on a *finite* set $S$.\
    Then\
    (a)  $\Phi_{S}(1) = |S|$\
    (b)  The sum of the weight of the elements in $S$ is the \
         derivative of $\Phi_{S}$, i.e. $\Phi_{S}'(1)$\
    (c)  The average weight of an element in S is $\frac{\Phi_{S}'(1)}{\Phi_{S}(1)}$.

To intuitively understand what does this means, we use example 1.6.2 as context:

>(a) $\Phi_{S}(1) = 2\times (1)^4+3\times (1)^2 = 5$, this means there
    are 5 animals in the set\
(b) $\Phi_{S}'(1) = 8\times (1)^3+ 6\times (1)^1 = 14$, this means there
    are 14 legs for all 5 animals\
(c) $\frac{\Phi_{S}'(1)}{\Phi_{S}(1)} = \frac{14}{5} = 2.8$, this means
    the average legs for an animals in $S$ is 2.8 legs.

*Proof.* To see (a), we have
  $$ \Phi_{S}(1) = \sum_{\sigma \in S} 1^{w(\sigma)} = \sum_{\sigma \in S} 1 = |S|.$$
  Now for (b),
  $$  \begin{aligned}
        &\Phi_{S}'(x) = \frac{d}{dx}\sum_{\sigma \in S}x^{w(\sigma)} =
        \sum_{\sigma \in S}w(\sigma)x^{w(\sigma)-1} \text{ so}\\
        &\Phi_{S}'(1) = \sum_{\sigma \in S}w(\sigma).\\
      \end{aligned}$$
  Thus for (c)
  $$\text{average weight }=\frac{\sum_{\sigma \in S}w(\sigma)}{|S|}=
  \frac{\Phi_{S}'(1)}{\Phi_{S}(1)}.$$

\newpage

## 1.8 Formal Power Series //Jan 15^th^ Lecture 5

Definition 1.8.1.
  ~ A **formal power series** *(fps)* is an expression of the form
    $$ a_{0}x^0+a_{1}x^1+a_{2}x^2\cdots$$
    where $a_0,a_1,\ldots \in \mathbb{Q}$ (*rational numbers*).\


    If $A(x)$ is a formal power series and $k\geq 0$, then we use
    $$ [x^k]A(x)$$ to denote the coefficient of $x^k$ in $A(x)$, i.e.,
    $$ [x^k](a_0+a_{1}x^1+\cdots) := a_k$$

Example 1.8.2.
  ~ $[x^3](1-x+2x^2-3x^3+4x^4+\cdots) = -3$.
**Note:** we use shorthand where its meaning is obvious, e.g.,
$$1-2x+3x^2-4x^3+\cdots \text{ means } 1+(-2)x+3x^2+(-4)x^3+\cdots,$$
and
$$ 1-5x \text{ means } 1+(-5)x+0(x^2)+0(x^3)+\cdots. $$

We will explore **addition, subtraction, multiplication, and division** on fps
in the following part.

Definition 1.8.2. (Equivalency)
  ~ Two formal power series are said to be **equal**, if for all $k\geq 0$,
    they have the same coefficient of $x^k$, i.e.,
    $$ [x^k]A(x)=[x^k]B(x) \text{ for all } k\geq 0.$$

Definition 1.8.3. (Addition)
  ~ If $A(x)$ and $B(x)$ are *fps*, then $(A+B)(x)$ is the *fps* such that
    $$ [x^k](A+B)(x) = [x^k]A(x)+[x^k]B(x)$$
    for each $k\geq 0$, i.e., if $A(x) = a_0+a_{1}x^1+\cdots$, $B(x) = b_0+b_{1}x^1+\cdots$
    then
    $$(A+B)(x) = (a_0+b_0)+(a_1+b_1)x+(a_2+b_2)x^2+\cdots.$$

Example 1.8.4.
  ~ $$\begin{aligned}
        &\hspace{13pt}(2+3x+4x^2+5x^3+\cdots)(1+x+x^2+\cdots)\\
        &=2+(2\times 1+3 \times 1)x+(2\times 1+3 \times 1+4\times 1)x^2+\cdots\\
        &=2+5x+9x^2+\cdots\\
        \\
        &\hspace{13pt}(a_0+a_1x+a_2x^2+\cdots)(b_0+b_1x+b_2x^2+\cdots)\\
        &=a_0b_0+(a_0b_1+a_1b_0)x+(a_0b_2+a_1b_1+a_2b_0)x^2+
        (a_0b_3+a_1b_2+a_2b_1+a_3b_0)x^3+\cdots\\
      \end{aligned}$$

Definition 1.8.5. (Multiplication)
  ~ If $A(x) = a_0+a_{1}x^1+\cdots$, $B(x) = b_0+b_{1}x^1+\cdots$, then
    $AB(x)$ is defined to be the *fps* such that
    $$\begin{aligned}
        {[x^m]}AB(x) &= a_0b_m+a_1b_{m-1}+\cdots +a_{m-1}b_1+a_mb_0\\
                   &= \sum_{k=0}^m a_kb_{m-k}
      \end{aligned}$$
    which means the coefficient for each $x^k$ is defined so, in general
    $$ \left(\sum_{n\geq 0} a_n x^n\right)\left(\sum_{n\geq 0}b_nx^n\right) =
        \sum_{n\geq 0} \left(\sum_{k=0}^n a_n b_{n-k}\right)x^n.$$

Definition 1.8.6. (Division)
  ~ Given two *fps* $P(x), Q(x)$, it can be possible to find a *fps*
    $A(x)$ so that $Q(x)A(x) = P(x)$.

Example 1.8.7.
  ~ Let $Q(x)=1-x-x^2, P(x)=1+x$. So we want to solve
      $$(1-x-x^2)A(x) = 1+x.$$
    Let $A(x)=a_0+a_1x+a_2x^2+\cdots$. We have
      $$(1-x-x^2)(a_0+a_1x+a_2x^2+\cdots)=1+x$$
    where
      $$\begin{aligned}
        \text{LHS}&=a_0+(a_1-a_0)x+(a_2-a_1-a_0)x^2+(a_3-a_2-a_1)x^3+(a_4-a_3-a_2)x^4+\cdots\\
        &= a_0+(a_1-a_0)x+\sum_{n\geq 2}(a_n-a_{n-1}-a_{n-2})x^n.\\
        \end{aligned}$$
    Since $\text{LHS}=\text{RHS}$, we can equate coefficients, so we have
      $$ a_0+(a_1-a_0)x+\sum_{n\geq 2}(a_n-a_{n-1}-a_{n-2})x^n = 1+1x+0x^2+0x^3+\cdots.$$
    and hence
      $$\begin{aligned}
        &a_0 = 1\\
        a_1-a_0=1 \rightarrow {}&a_1 = 2\\
        a_2-a_1-a_0=0 \rightarrow {}&a_2 = 3\\
        a_3-a_2-a_1=0 \rightarrow {}&a_3 = 5\\
        a_4-a_3-a_2=0 \rightarrow {}&a_4 = 8\\
        &\vdots\\
        &a_n = a_{n-1}+a_{n-2} \text{ for }n\geq 2
        \end{aligned}$$
    So we get a fibonacci sequence
      $$ a_0,a_1,a_2,\ldots = 1,2,3,5,8,13,21,\ldots.$$
    Then
      $$\begin{aligned}
          A(x) &= \frac{1+x}{1-x-x^2}\\
               &= 1+2x+3x^2+5x^3+8x^4+13x^5+\cdots \text{ (in formal power series form).}
        \end{aligned}$$

\newpage


## 1.9 Formal Power Series Cont'd //Jan 17^th^ Lecture 6

We will present an general idea of finding the result of dividing two *fps*.

Say we are given *fps*
  $$\begin{aligned}
      &P(x)=p_0+p_1x+\cdots\\
      &Q(x)=q_0+q_1x+\cdots
    \end{aligned}$$
And we wish to find $A(x)=a_0+a_1x+\cdots$ such that $Q(x)A(x)=P(x)$, i.e.,
  $$ (q_0+q_1x+\cdots)(q_0+q_1x+\cdots) = p_0+p_1x+\cdots$$
equating the coefficients given
  $$\begin{aligned}
      q_0a_0&=p_0  \hspace{2cm} (0)\\
      q_1a_0+q_0a_1&=p_1  \hspace{2cm} (1)\\
      q_0a_2+q_1a_1+q_1a_0&=p_2  \hspace{2cm} (2)\\
      \vdots\\
      q_ka_0+q_{k-1}a_1+\cdots+a_0a_k&=p_k   \hspace{2cm} (k)\\
      \vdots\\
    \end{aligned}$$


Say we wish to find $a_k$ for some fixed $a_k$ (e.g. $a_5$).\
\
To find such $a_k$, notice in equation $(k)$:
  $$q_ka_0+q_{k-1}a_1+\cdots+a_0a_k = p_k$$
$a_k$ is related to all $a_0,\ldots,a_{k-1}$. So, all equations from $(0)$ to
$(k)$ are related, therefore to solve $a_k$, we have a system of $k+1$ linear equations in
$a_0,\ldots,a_k$:
  $$\begin{aligned}
      q_0a_0&=p_0\\
      q_1a_0+q_0a_1&=p_1\\
      q_2a_0+q_1a_1+q_0a_1&=p_2\\
      \vdots\\
      q_ka_0+q_{k-1}a_1+\cdots+a_0a_k&=p_k\\
    \end{aligned}$$

since they are all linear equations, in the language of linear algebra:
  $$\begin{pmatrix}
      q_0[e_{11}] & 0[e_{12}] & 0[e_{13}] & \cdots & 0[e_{1k}] \\
      q_1[e_{21}] & q_0[e_{22}] & 0[e_{23}] & \cdots & 0[e_{2k}] \\
      q_2[e_{31}] & q_1[e_{32}] & q_0[e_{33}] & \cdots & 0[e_{3k}] \\
      \vdots & \vdots & \vdots & \ddots & \vdots \\
      q_k[e_{k1}] & q_{k-1}[e_{k2}] & q_{k-2}[e_{k3}] & \cdots & q_0[e_{kk}]
    \end{pmatrix}
    \begin{pmatrix}
        a_0\\
        a_1\\
        a_2\\
        \vdots\\
        a_k
    \end{pmatrix}
    =
    \begin{pmatrix}
        p_0\\
        p_1\\
        p_2\\
        \vdots\\
        p_k
    \end{pmatrix}$$

Recall the definition of **lower triangular matrix**:

> An $m\times n$ matrix is said to be **lower triangular** if $l_{ij} = 0$ whenever $i<j$,
> where i is the row count, j is the column count.

Note that
  $$e_{12}=e_{13}=\cdots=e_{1k}=\joinrel= e_{23}=e_{24}=\cdots=e_{2k}=\joinrel=\cdots=0$$
where $e_{ij}=0$ whenever $i<j$, so the matrix is lower triangular. By theorem

> If an $n\times n$ matrix $A$ is upper triangular or lower triangular, then
$$ \text{det} \  A = e_{11}e_{22}\cdots e_{nn}.$$

then determinant of the matrix is ${q_0}^k$. By **Invertible Matrix Theorem**, we have

> The system of equations $A\overrightarrow{x} = \overrightarrow{b}$ is consistent
with a **unique solution** for all $\overrightarrow{b}\in \mathbb{R}^n \iff
\text{det}(A) \neq 0$.

That is to say, if $q_0 \neq 0$, then there is a unique solution for each $a_i \in
\{a_1,a_2,\ldots\}$ such that
$$ (q_0+q_1x+\cdots)(a_0+a_1x+\cdots)=(p_0+p_1x+\cdots).$$
(we are hiding some infinity mess here: we only deal with some finite $a_k$,
which is not the ininity case here, but the conclusion is correct).\
\
More informally speaking, we can "devide by" a *fps* $Q(x)$ if the constant term
$q_0$ is nonzero.
\
\
\
If $Q(x)A(x)=P(x)$, then we write $A(x)=\frac{P(x)}{Q(x)}$.

Definition 1.9.1.
  ~ If $Q(x)A(x)=1=(1+0x+0x^2+\cdots)$ then $A(x)$ is the **inverse** of $Q(x)$,
    and we write
    $$ Q(x)=\frac{1}{A(x)}=A^{-1}(x). $$

Proposition 1.9.2.
  ~ If $Q(x)=q_0+q_1x+\cdots$ then the inverse of $Q(x)$ exists if and only if
    $q_0\neq 0$. If it exists, it is **unique**.

Proposition 1.9.3.
  ~ The inverse of $A(x)=1-x$ is
      $$B(x)=\frac{1}{1-x}=1+x+x^2+\cdots=\sum_{n\geq0} x^n.$$

*Proof.*
  $$\begin{aligned}
      &\hspace{13pt}(1-x)(1+x+x^2+\cdots)\\
      &=(1+x+x^2+\cdots)-x(1+x+x^2+\cdots)\\
      &=1+(1-1)x+(1-1)x^2+\cdots\\
      &=1.
    \end{aligned}$$

The formal power series $1+x+x^2+\cdots$ arises frequently, since it is the
generating series for the non-negative integers. We call this a **geometric
series**. The powers of geometric series arise often in problems that we
will face later.

Theorem 1.9.4. (Negative Binomial Theorem)
  ~ Let $k\geq1$. The inverse of $(1-k)^k$ is
  $$ (1-x)^{-k}=\sum_{n\geq0} {{n+k-1}\choose {k-1}}x^n.$$

*Proof.* We have
  $$\begin{aligned}
      &\hspace{13pt}(1-x)^{-k}\\
      &=({(1-x)}^{-1})^{k}\\
      &=\underbrace{(x^0+x^1+x^2+\cdots)(x^0+x^1+x^2+\cdots)
        \cdots(x^0+x^1+x^2+\cdots)}_{k\text{  times}} \hspace{1cm} \text{(1)}\\
      &\text{by proposition 1.9.3.}\\
    \end{aligned}$$

Informally, the coefficients of $x^n$ ($n$ is any number in $\mathbb{Z}_{\geq0}$)
in this expression is the number of of ways of choosing terms $x^{a_1}, x^{a_2},
 \ldots, x^{a_k}$ from the $k$ brackets so that the total power is n; by
 Assignment 1, this is ${{n+k-1} \choose {k-1}}$.

 More formally,
 $$ \begin{aligned}
        ({(1-x)}^{-1})^{k} &= \underbrace{\left(\sum_{a_1 \geq 0} x^{a_1}\right)
        \left(\sum_{a_2 \geq 0} x^{a_2}\right) \cdots \left(\sum_{a_k \geq 0}
        x^{a_k}\right)}_{k\text{ times}}\\
      &= \sum_{a_1 \geq 0} \sum_{a_2 \geq 0} \cdots \sum_{a_k \geq 0}
          x^{a_1}x^{a_2}\cdots x^{a_k}\\
      &= \sum_{a_1,a_2,\ldots,a_k\geq 0}x^{a_1+a_2+\cdots+a_k = n}\\
    \end{aligned}$$
for some fixed $n \geq 0$, each such $x^n$ is a term in result of equation (1).
For each combination of $a_1,a_2,\ldots,a_k = n$, there is one term of $x^n$,
and by assignment 1 problem 3, we have ${{n+k-1} \choose {k-1}}$ combinations.
Thus
  $$ (1-x)^{-k}=\sum_{n\geq0} {{n+k-1}\choose {k-1}}x^n.$$

Definition 1.9.4.
  ~ The **composition** of formal power series $A(x)=a_0+a_1x+a_2x+\cdots$ and
    $B(x)$ is defined by
      $$ A(B(x)) = a_0+a_1B(x)+a_2(B(x))^2+\cdots.$$

Consider any two *fps* $A(x)$ and $B(x)$, in the form of
  $$ A(B(x)) = a_0+a_1B(x)+a_2(B(x))^2+\cdots$$
this may not make sense, e.g., if $A(x)=1+x+x^2+\cdots \text{ and } B(x)=1+x$,
then
  $$ A(B(x)) = 1+(1+x)+(1+x)^2+(1+x)^3+\cdots$$
This is meaningless because it has an undefined constant term (i.e., its constant
term is $\infty$). However, $A(B(x))$ does make sense if $B(x)$ has zero
constant term, e.g., if $A(x)=1+x+x^2+\cdots, \ B(x)=x+x^2$,then
  $$\begin{aligned}
      A(B(x))&=1+(x+x^2)+(x+x^2)^2+(x+x^2)^3+\cdots\\
             &=1+x(1+x)+x^2(1+x)^2+x^3(1+x)^3+\cdots.
    \end{aligned}$$

Proposition 1.9.5.
  ~ If $B(x)$ has 0 constant term (i.e., $[x^0]B(x)=0)$) then
      $$A(B(x))=\sum_{n\geq0}a_nB(x)^n$$
    is well-defined for every formal power series $A(x)=\sum_{n\geq0}a_nx^n$.

*Proof.* Let $A(x), C(x)$ be any *fps*, and $B(x)=xC(x)$. Note that $B(x)$ is a
formal power series with constant term equal to zero. Then
  $$\begin{aligned}
    A(B(x))&=A(xC(x))\\
           &=a_0+a_1xC(x)+a_2(xC(x))^2+\cdots\\
           &=a_0+a_1xC(x)+a_2x^2(C(x))^2+\cdots\\
    \end{aligned}$$

Example 1.9.6.
  ~ $$\begin{aligned}
      \frac{x}{1+2x^2} &= x\times\frac{1}{1-(-2x^2)}\\
                       &= x\times A(B(x)) \hspace{1cm} (1)\\
    \end{aligned}$$
    where $A(x)=\frac{1}{1-x},\ B(x)=-2x^2$. By proposition 1.9.3,
    $$\begin{aligned}
      (1) &= x\times\left(1+(-2x^2)+{(-2x^2)}^2+\cdots\right)\\
          &= x\sum_{n\geq0}{(-2x^2)}^n.\\
      \end{aligned}$$

Problem 1.9.7.
  ~ Determine the inverse of $1-x+2x^2$.
*Solution.* Let $P(x)=1-x$. Note that $1-x+2x^2=1-(x-2x^2)=P(x-2x^2)$. By
proposition 1.9.3,
  $$\begin{aligned}
    {(1-x+2x^2)}^{-1} &= P(x-2x^2)^{-1}\\
                  &= 1+(x-2x^2)+(x-2x^2)^2+\cdots\\
                  &= x^0{(1-2x)}^0+x^1{(1-2x)}^1+x^2{(1-2x)}^2+\cdots\\
                  &= \sum_{n\geq0}x^n(1-2x)^n.\\
    \end{aligned}$$

\newpage

## 1.10 Additional Example for 1.9

Example 1.10.1.
  ~ $$\begin{aligned}
        [x^n]\frac{x^k}{(1-x)^k}&=[x^n]x^k\sum_{t\geq 0}{{t+k-1}\choose{k-1}}x^t
        \text{  (by Negative Binomial Theorem)}\\
             &=[x^n]\sum_{t\geq 0}{{t+k-1}\choose{k-1}}x^{t+k}\\
        \text{let }n=t+k\text{, we have}\\
             &={{n-1}\choose{k-1}}.
      \end{aligned}$$


Example 1.10.2.
  ~ \begin{equation*}
    \begin{aligned}
        &[x^{239}]\frac{1}{(1-2x^2)^7}\cdot\frac{x^5}{(1-3x^3)^3}\\
        &=[x^{239}]x^6
          \cdot\sum_{t\geq 0}{{t+6}\choose{6}}(2x^2)^t
          \cdot\sum_{s\geq 0}{{s+4}\choose {4}}(3x^3)^s\\
        &=[x^{239-6}]\bcancel{x^6}
          \cdot\sum_{t\geq 0}{{t+6}\choose{6}}(2x^2)^t
          \cdot\sum_{s\geq 0}{{s+4}\choose {4}}(3x^3)^5\\
      \text{let }k=2t+3s\text{ we have}\\
        &=[x^{233}]\sum_{k\geq 0}\overbrace{\left[\sum_{2t+3s=k}{{t+6}\choose t}2^t
          {{s+4}\choose4}3^s\right]}^{\text{coefficient}}x^k\\
        &=\sum_{2t+3s=233}{{t+6}\choose t}2^t{{s+4}\choose4}3^s=(1)\\
    \end{aligned}
    \end{equation*}
    list possible values for $t$, we have
    \begin{equation*}
    \begin{aligned}
      \text{When }&t=0,\ 3s=233 \Rightarrow \text{ no solution for } s\in\mathbb{Z}_{\geq0}\\
      &t=1,\ 3s=231 \Rightarrow \text{ has solution}\\
      &t=2,\ 3s=229 \Rightarrow \text{ no solution}\\
      &t=3,\ 3s=227 \Rightarrow \text{ no solution}\\
      &t=4,\ 3s=225 \Rightarrow \text{ has solution}\\
      &t=5,\ 3s=223 \Rightarrow \text{ no solution}\\
      &t=6,\ 3s=221 \Rightarrow \text{ no solution}\\
      &t=7,\ 3s=219 \Rightarrow \text{ has solution}\\
      &\hspace{8pt}\vdots\\
      &t=3i-2, i\in\mathbb{Z}_{\geq 1}\text{ , there is a solution.}\\
    \end{aligned}
    \end{equation*}
    then
    \begin{equation*}
    \begin{aligned}
      s &= \frac{233-2t}{3}\\
        &= \frac{233-2(3i-2)}{3}\\
        &= 79-2i.
    \end{aligned}
    \end{equation*}
    To determine the upper limit of $i$, i.e., the upper bound of the summation, we have
    \begin{gather*}
    t_{\text{max}}=\lfloor\frac{233}{2}\rfloor\\
    \Rightarrow 3i_{\text{max}}-2=116\\
    i_{\text{max}}=\lfloor\frac{118}{3}\rfloor\\
    i_{\text{max}}=39.
    \end{gather*}

    Thus,
      $$(1)=\sum_{i=1}^{39}{{3i-2+6}\choose{6}}2^{3i-2}{{79-2i+4}\choose{4}}3^{79-2i}.$$

\newpage

## 1.11 Sum Lemma & Product Lemma //Jan 20^th^ & part of Jan 22^th^ Lecture 7,8

Theorem 1.11.1. (Sum Lemma)
  ~ Let $(A,B)$ be a partition of $S$ ($A$ and $B$ are disjoint sets whose union
    is $S$). Then
      $$\Phi_{S}(x) = \Phi_{A}(x)+\Phi_{B}(x)$$
    More generally, if $A$ and $B$ are not disjoint, then
      $$\Phi_{S}(x) = \Phi_{A}(x)+\Phi_{B}(x)-\Phi_{A\cap B}(x).$$

Theorem 1.11.2. (Product Lemma)
  ~ Let $A$ and $B$ be sets of configurations with weight functions $\alpha$
    and $\beta$ respectively. If $w(\sigma)=\alpha(a)+\beta(b)$ for each
    $\sigma = (a,b)\in A \times B$, then
      $$ \Phi_{A\times B} = \Phi_{A}(x) \Phi_{B}(x) $$

*Proof.* We have
  $$\begin{aligned}
      \Phi_{A\times B}(x) &= \sum_{\sigma \in A\times B}x^{w(\sigma)}=
        \sum_{(a,b)\in A\times B}x^{\alpha(a)+\beta(b)}=
        \sum_{(a,b)\in A\times B}x^{\alpha(a)} \cdot x^{\beta(b)}\\
      &=\sum_{a\in A}\left(x^{\alpha(a)}\cdot \sum_{b\in B}x^{\beta(b)}\right)
        = \sum_{a\in A}x^{\alpha(a)} \cdot \sum_{b\in B}x^{\beta(b)}\\
      &=\Phi_{A}(x)\Phi_{B}(x).
    \end{aligned}$$

Problem 1.11.3.
  ~ Prove the number of solutions to
      $$ t_1+t_2+\cdots+t_k = n \hspace{1cm} (*)$$
    where $t_i\geq 1, t_i \in \mathbb{Z} \text{ for all } i \in \{1,\ldots,k\}$ is
      $$ [x^i]\sum_{n\geq 0}{{n-1} \choose {k-1}}x^n = [x^{n-k}]\frac{1}{(1-x)^k}.$$

*Solution.* Let $S={1,2,\ldots}$ and for all $i\in \mathbb{N}$. We define
    $$ w_i(\sigma_i)=a_1+a_2+\cdots+a_i $$
  for each $\sigma_i=(a_1,a_2,\ldots,a_i)\in S^i =
  \underbrace{S \times \cdots \times S}_{\text{i times}}$
  By **Product Lemma**,
    $$\begin{aligned}
        \Phi_{S^k}(x)&=
          \overbrace{\Phi_{S}(x)\cdot\Phi_{S}(x)\cdot\ \cdots\ \Phi_{S}(x)}^{\text{k times}}\\
        &= [\Phi_S(x)]^k\\
        &= (x+x^2+\cdots)^k\\
        &= \underbrace{(x+\cdots)(x+\cdots)\cdots (x+\cdots)}_{\text{k times}}\\
      \end{aligned}$$
    $$\begin{aligned}
        [x^n](x+x^2+\cdots)^k &= [x^n]x^k(1+x+\cdots)^k\\
        &= [x^{n-k}](1+x+\cdots)^k\\
        &= [x^{n-k}]\frac{1}{(1-x)^k}=\text{RHS}.
      \end{aligned}$$
  For LHS,
    We imagine find the solutions is like placing $n$ balls on the board. How
    do we partition them into $k$ labelled sets? Place $k-1$ dividers to separate
    the balls into $k$ sets. Let $t_i$ be the number of balls between dividers
    $i-1$ and $i$ for $i\in \{2,\ldots,k-1\}$.\
    $t_1$ are the balls left for the first divider and $t_k$ are the balls right
    of the last divider. Then $a_n$ is the number of ways to place $k-1$ dividen
    in $n-1$ positions
      $$ a_n={{n-1} \choose {k-1}}. $$

Proposition 1.11.4. (Identities)
  ~ $$\begin{aligned}
      [x^n]\frac{1}{(1-x)^k} &= [x^{n-k}]\frac{1}{x^k(1-x)^k} =
                                [x^n]\frac{1}{x^k}\sum_{n\geq 0}{{n-1} \choose {k-1}}x^n\\
                             &= [x^{n+k}]\sum_{n\geq 0}{{n-1}\choose{k-1}}x^n =
                                {{n+k-1} \choose {k-1}}.
      \end{aligned}$$

\newpage

# Chapter 2 Compositions and Strings

## 2.1 Compositions of an Integer

Definition 2.1.1. (Composition of an Integer)
  ~ For non-negative integer $n$ and $k$, a **composition** of $n$ with $k$ parts
    is an ordered list $(c_1,\ldots,c_k)$ of positive integers such that
    $c_1+\ldots+c_k=n$. The positive integers $c_1,\ldots,c_k$ are called the
    **parts** of the composition. There is one composition of 0, the empty
    composition, which is a composition with 0 parts, we denote it as $\varepsilon$.
Note that all **parts** are greater than 0 and when writing a composition, we
need to use the parentheses() but not curly ones{}.\
\
\

**Sum** & **Product Lemma** are highly abstract and hard to grasp, we need
following examples to understand them.

Problem 2.1.2.
  ~ How many **compositions** are there in a number $n$?

*Solution.* Let $S=\{\text{all possible compositions}\}$. We want to find
$[x^n]\Phi_{S}(x)$ so that the number of compositions for $n$ is clear. By the
idea of decomposing $S$ by number of parts, we have
\begin{align*}
  S &=\{\varepsilon,(1),(2),\ldots,(1,1),(1,2),\ldots,(2,1),(2,2)\ldots\}\\
    &=S_0\cup S_1\cup S_2\cup\cdots=(1)\\
\end{align*}
where $S_i$ denotes all compositions with $i$ parts, e.g.,
\begin{align*}
  &S_0=\{\varepsilon\}\\
  &S_1=\{(1),(2),\ldots,(n),\ldots\}\\
  &S_2=(1,1),(1,2),\ldots,(2,1),(2,2),\ldots,(3,1),(3,2),\ldots\\
  &\hspace{10.5pt}=S_1\times S_1=\{(\alpha_1,\alpha_2)\,|\,\alpha_1,\alpha_2\in S_1\}\\
  &S_3=(1,1,1),(1,1,2),\ldots,(2,1,1),(2,1,2),\ldots\\
  &\hspace{10.5pt}=S_1\times S_1\times S_1=
    \{(\alpha_1,\alpha_2,\alpha_3)\,|\,\alpha_1,\alpha_2,\alpha_3\in S_1\}\\
  &\hspace{5pt}\vdots\\
  &S_k=S_1\times\cdots\times S_1={S_1}^k\\
\end{align*}
and also since we have $w(\alpha_1,\alpha_2,\ldots,\alpha_k)=\alpha_1+\alpha_2+
\cdots+\alpha_k=w(\alpha_1)+w(\alpha_2)+\cdots+w(\alpha_k)$ and $S_k=
\underbrace{S_1\times S_1\times\cdots\times S_1}_{\text{k times}}$ by definition,
$$\begin{aligned}
    \Phi_{S_k}(x) &\stackrel{\text{P.L.}}{=}  \left[\Phi_{S_1}(x)\right]^k\\
    &\hspace{3pt}=[x+x^2+\cdots]^k\\
    &\hspace{3pt}=\left(\frac{x}{1-x}\right)^k\hspace{2cm}(2)
  \end{aligned}$$

By equation (1) and since $S_i\cap S_j=\emptyset \ \ \forall \,i\neq j$, i.e.,
they are all disjoint, we have
\begin{align*}
    \Phi_{S}(x) &\stackrel{\text{S.L.}}{=} \Phi_{S_0}(x)+\Phi_{S_1}+\cdots\\
    &\hspace{3pt}=\sum_{k\geq 0}\Phi_{S_k}(x)\\
    &\hspace{3pt}=\Phi_{S_0}(x)+\sum_{k\geq 1}\left(\frac{x}{1-x}\right)^k\\
    &\hspace{3pt}=\Phi_{\{\varepsilon\}}(x)+\sum_{k\geq 1}\left(\frac{x}{1-x}\right)^k\\
    &\hspace{3pt}=(1)x^0+\sum_{k\geq 1}\left(\frac{x}{1-x}\right)^k
    \text{(by definition of composition)}\\
  \intertext{notice that $\sum_{k\geq 1}\left(\frac{x}{1-x}\right)^k$ is a geometric
    series with the common ratio equal to $(\frac{x}{1-x})$, then}
    &\hspace{3pt}=(1)x^0+\frac{1}{1-\frac{x}{1-x}}\\
    &\hspace{3pt}=(1)x^0+\frac{x}{1-2x}\\
\end{align*}

Now we have the rational expression of $\Phi_{S}(x)$. To answer the question, we get
\begin{align*}
  [x^n]\frac{x}{1-2x} &= [x^n]x\cdot\sum_{k\geq 0}(2x)^k \text{by proposition}\\
                      &= [x^n]\sum_{k\geq 0}2^kx^{k+1}\\
  \intertext{let $n=k+1$,}
                      &= [x^n]\sum_{n-1\geq 0}2^{n-1}x^n\\
                      &= 2^{n-1}.
\end{align*}

Thus, we have
$$[x^n]\Phi_{S}(x) =
\begin{cases}
  1,& n=0\\
  2^{n-1},& n>0.
\end{cases}$$


Problem 2.1.4.
  ~ Given a non-negative integer $n$, how many composition are there with parts $\geq2$

*Solution.* Let $S=\text{\{compositions where every part is} \geq 2 \}$. \
For each $k\geq 0$, let $S_k$ be the set of compositions in $S$ with exactly $k$ parts,
that is,
\begin{equation*}
\begin{aligned}
  S_0&=\{()\}&&=\{2,3,4,\ldots\}^0\\
  S_1&=\{(2),(3),(4),\ldots\}&&=\{2,3,4,\ldots\}^1\\
  S_2&=\{(2,2),(2,3),\ldots,(3,2),(3,3)\ldots\}&&=\{2,3,4,\ldots\}^2\\
  \vdots
\end{aligned}
\end{equation*}

So we have
\begin{equation*}
\begin{aligned}
  &\text{\# of composition of $n$ with all parts $\geq 2$}\\
  &=\text{\# of elements of $S$ with weight $n$}\\
  &=[x^n]\Phi_{S}(x)\\
  &=[x^n]\left[\Phi_{S_0}(x)+\Phi_{S_1}(x)+\cdots\right] \hspace{1cm}\text{(by Sum Lemma)}\\
  &=[x^n]\left[{\Phi_{\mathbb{Z}_{\geq 2}}(x)}^0+
  {\Phi_{\mathbb{Z}_{\geq 2}}(x)}^1+\cdots\right] \hspace{1cm}\text{(by Product Lemma)}\\
  &=[x^n]\left[(x^2+x^3+\cdots)^0+(x^2+x^3+\cdots)^1+\cdots\right]\\
  &=[x^n]\left[{\left(\frac{x^2}{1-x}\right)}^0+{\left(\frac{x^2}{1-x}\right)}^1+\cdots\right]\\
  &=[x^n]\left(\frac{1}{1-\frac{x^2}{1-x}}\right)\\
  &=[x^n]\left(\frac{1-x}{1-x-x^2}\right)\\
\end{aligned}
\end{equation*}
We want the coefficients of
\begin{equation*}
\begin{aligned}
  \frac{1-x}{1-x-x^2}&=a_0+a_1x+\cdots\\
  1-x&=(1-x-x^2)(a_0+a_1+\cdots)
\end{aligned}
\end{equation*}

Equating coefficients gives
\begin{align*}
  1&=a_0\\
  -1&=a_1-a_0\\
  0&=a_k-a_{k-1}-a_{k-2} \hspace{1cm}\text{where $k\geq 2$}\\
\end{align*}
So
$$[x^n]\frac{1-x}{1-x-x^2}=(n-2)\text{th Fibbonacci number}.$$

\newpage

##2.2 Subsets with Restrictions //Jan 24^th^ Lecture 9

Problem 2.2.1.
  ~ How many different sequences of coins from {5 cents, 10 cents, 25 cents,
    100 cents, 200 cents} can make a given total $n$?

*Solution.* Let $T$ be the set of all compositions with this property, and for
  each $k\geq 0$, let $T_k$ be the set of compositions in $T$ with exactly $k$
  parts. Let $S={5,10,25,100,200}$.\
  By the sum lemma, # of compositions of $n$ in $T$ is
    \begin{align*}
      [x^n]\Phi_{T}(x)&=[x^n]\sum_{l\geq 0}\Phi_{T_l}(x)\\
                      &=[x^n]\sum_{l\geq 0}\left[\Phi_{T_S}(x)\right]^l
                        \hspace{1cm} \text{by product lemma}\\
                      &=[x^n]\frac{1}{1-\Phi_S(x)}\\
                      &=[x^n]\frac{1}{1-(x^5+x^{10}+x^{25}+x^{100}+x^{200})}
    \end{align*}
  computing the coefficient for $n$ gives the answer.

Problem 2.2.2.
  ~ What if we want to find the number of ways to make \$5.45 where we do not
    distinguish orderings of coins?

*Solution.* The number of ways is the number of solutions to
  $$a_1+a_2+a_3+a_4+a_5=n$$
  where
  \begin{align*}
    &a_1\in S_5=\{0,5,10,15,20,\ldots\}\\
    &a_2\in S_1=\{0,10,20,30,40,\ldots\}\\
    &a_3\in S_{25}=\{0,25,50,\ldots\}\\
    &a_4\in S_{100}=\{0,100,200,\ldots\}\\
    &a_5\in S_{200}=\{0,200,400,\ldots\}\\
  \end{align*}
  Note that we do not cut upper limit of $S_{200}$ to 400 as
  it may make the series easier to calculate, but with the same answer.

  Let $S=(a_1,a_2,a_3,a_4,a_5)$. Then
  \begin{align*}
    \text{\# of solutions}&=[x^n]\Phi_{S}(x)\\
      &=[x^n]\Phi_{S_5}(x)\Phi_{S_{10}}(x)\Phi_{S_{25}}(x)\Phi_{S_{100}}(x)\Phi_{S_{200}}(x)
      \hspace{1cm}\text{(by Product Lemma)}\\
      &=[x^n](1+x^5+x^{10}+\cdots)(1+x^{10}+x^{20}+\cdots)\\
      &\hspace{30pt}(1+x^{25}+x^{50}+\cdots)(1+x^{100}+x^{200}+\cdots)
      (1+x^{200}+x^{400}+\cdots)\\
      &=[x^n]\frac{1}{(1-x^5)(1-x^{10})(1-x^{25})(1-x^{100})(1-x^{200})}.\\
  \end{align*}

Problem 2.2.3.
  ~ How many subsets of $\{1,2,\ldots,n\}$ of size $k$ contain no two consecutive
    elements? \
    For example, for $n=7$, $k=3$, subsets are
    \begin{align*}
      \{&(1,3,5),(1,3,6),(1,3,7),\\
        &(1,4,6),(1,4,7),(1,5,7),\\
        &(2,4,6),(2,4,7),(2,5,7),\\
        &(3,5,7)\}
    \end{align*}, $|S|=10$.

*Solution.* We will present a bijective proof.\
Consider such subset $\{a_1,a_2,\ldots,a_k\}$ where $a_1<a_2<a_3<\cdots<a_k$.\
Let
  \begin{align*}
   &S_{k,n}=\{\text{k-element subsets of }\{1,\ldots,n\} \text{ without consecutive elements}\}\\
   &T_{k,n}=\{\text{ (k+1)-tuples } (d_1,d_2,\ldots,d_{k+1})\\
  &\hspace{37pt}\text{ where } d_1\geq 1,d_2,\ldots,d_k\geq 2,d_{k+1}\geq 0\text{, and } d_1+\cdots+d_{k+1}=n\}
  \end{align*}
Let $T_k$ be the set of all such $(k+1)$-tuples with any sum.\
The function $\psi:S_{k,n}\rightarrow T_{k,n}$ is defined by
  $$ \phi(a_1,\ldots,a_k)=a_1,a_2-a_1,\ldots,a_k-a_{k+1},n-a_k$$
where $\{a_1,\ldots,a_k\}\in S_{n,k},\ a_1<a_2<\cdots<a_k$ is a bijection from
$S_{k,n}$ to $T_{k,n}$. So $|S_{k,n}|=|T_{k,n}|$.\

Now
\begin{align*}
  |T_{k,n}|&=[x^n]\Phi_{T_k}(x)\\
           &=[x^n]\Phi_{\mathbb{N}\geq 1}(x)\cdot[\Phi_{\mathbb{N}\geq 2}(x)]^{k-1}
           \cdot\Phi_{\mathbb{N}\geq 0}(x)\\
           &=[x^n](x+x^2+\cdots)(x^2+x^3+\cdots)^{k-1}(1+x+x^2+\cdots)\\
           &=[x^n]\left(\frac{x}{1-x}\right)\left(\frac{x^2}{1-x}\right)^{k-1}
           \left(\frac{1}{1-x}\right)\hspace{1cm}\text{by Geometric Series}\\
           &=[x^n]x^{2k-1}\cdot\frac{1}{(1-x)^{k+1}}\\
           &=[x^{n-2k+1}](1-x)^{-(k+1)}\\
           &=[x^{n-2k+1}]\sum_{m\geq 0}{{m+(k+1)-1}\choose{(k+1)-1}}x^m
           \hspace{1cm}\text{by Negative Binomial Theorem}\\
           &=[x^{n-2k+1}]\sum_{m\geq 0}{{m+k}\choose{k}}x^m\\
           &={{n-2k+1+k}\choose{k}}\\
           &={{n-k+1}\choose{k}} = |S_{k,n}|.
\end{align*}
\newpage

## 2.3 Binary Strings //Jan 27^th^ Lecture 10

Definition 2.3.1.
  ~ A **Binary String** is an expression $a_1a_2\ldots a_n$ where $a_1,a_2,\ldots
    \in\{1,0\}$, and its length is $n$. We use $\varepsilon$ to denote the empty string
    of length 0.

Example 2.3.2.
  ~ A binary string "01101" has length 5.

Definition 2.3.2.
  ~ If $a$ and $b$ are strings $a_1\ldots a_n$ and $b_1\ldots b_m$, then
    the **concatenation** $ab$ is the string $a_1\ldots a_n b_1\ldots b_m$.

Definition 2.3.3.
  ~ A string $a'$ is a **substring** of a string $a$, if
      $$ a=ba'c \hspace{10pt}\text{for some strings $b$ and $c$} $$

**Remark:** When constructing generating series for sets of strings, the weight
  function will (for us) be the length of the string.

Example 2.3.4.
  ~ \begin{align*}
      &S=\{\varepsilon,0,10,100,0011,0110\}\\
      &\Phi_{S}(x)= x^0+x^1+x^2+x^3+2x^4\\
    \end{align*}

Example 2.3.5.
  ~ \begin{align*}
      &S=\{\text{all binary strings}\}\\
      &\Phi_{S}(x)= x^0+2x^1+4x^2+8x^3+\cdots=\sum_{i\geq 0}(2x)^i=\frac{1}{1-2x}\\
    \end{align*}

Note that if $A$ and $B$ are sets of strings, then $AB$ denotes the set
  $$ AB=\{ab|a\in A, b\in B\} $$
where AB is result of **"Concatenation Product"**, and we use $A^k$ to denote
$\underbrace{(A\ldots A)}_{\text{concatenate k times}}$.
For a set $A$, we write $A^* {}$ for the set
  $$A^* =\{\varepsilon\}\cup A^1\cup A^2\cup A^3 \cup \cdots$$

Example 2.3.6.
  ~ $$\{0,01\}\{0,10,11\}=\{00,010,011,\cancelto{\text{repetition}}{010},0110,0111\}$$

Example 2.3.7.
  ~ $$0^* =\{\varepsilon,0,00,000,0000,00000,\ldots \}$$

Example 2.3.8.
  ~ $$\{00,11\}^* = \{\text{strings where every "block" of 0's and 1's has even length}\}$$

Definition 2.3.9.
  ~ A **Block** of a string $a$ is a maximal substring of $a$ that only contains
    0 or only contains 1.

Problem 2.3.10.
  ~ How many binary strings of length $n$ have no "10" substring?

*Solution.* Let $S=\{\text{binary strings with no "10" substring}\}$.\
We want to construct $[x^n]\Phi_S(x)$. It is easy to see that
\begin{align*}
  S&=\text{\{strings of the form $ab$, where $a$ is all 0's and $b$ is all 1's\}}\\
   &=\{ab|a\in\{0\}^* , b\in\{1\}^* \}\\
   &=\{0\}^* \{1\}^* \text{ (concatenation)}\\
\end{align*}
so
\begin{align*}
  \Phi_S(x)&=\Phi_{\{0\}^* \{1\}^* }(x)\\
   &\stackrel{\text{S.L.}}{=} \Phi_{\{0\}^* }(x)\Phi_{\{1\}^* }(x)\\
   &=\Phi_{\{\varepsilon,0,00,\ldots\}}(x)\Phi_{\{\varepsilon,1,11,\ldots\}}(x)\\
   &=(x^0+x^1+x^2+\cdots)(x^0+x^1+\cdots)\\
   &=\frac{1}{(1-x)^2}
\end{align*}
so the strings in $S$ of length $n$ is
\begin{align*}
  [x^n]\Phi_S(x)&=[x^n]\frac{1}{(1-x)^2}\\
   &={{n+2-1}\choose{2-1}} \hspace{1cm}\text{by NBT}\\
   &=n+1
\end{align*}

Problem 2.3.11.
  ~ How many binary strings of length $n$ have no "00" substring?

*Solution.* Let $S=${string with no "00" substring}. Take an example, for string
$$"111011101011101110110"$$
we can decompose it by
$$\underbrace{1}_{}\underbrace{1}_{}\underbrace{1}_{}\underbrace{01}_{}
  \underbrace{1}_{}\underbrace{1}_{}\underbrace{01}_{}\underbrace{01}_{}
  \underbrace{1}_{}\underbrace{1}_{}\underbrace{01}_{}\underbrace{1}_{}
  \underbrace{1}_{}\underbrace{01}_{}\underbrace{1}_{}\underbrace{0}_{(possibly)}$$
so that every string in $S$ can be built uniquely from pieces in $\{1,01\}$ with
possibly a single "0" piece at the end. Hence,
$$S=\underbrace{\{1,01\}^* }_{\text{any number of "0" or "01" pieces}}
 \overbrace{\{\varepsilon,0\}}^{\text{(possibly) a single 0 piece}}$$

Therefore,
  \begin{align*}
    [x^n]\Phi_{S}(x)&=[x^n]\Phi_{\{1,01\}^* \{0,\varepsilon\}}(x)\\
    &\stackrel{\text{P.L.}}{=}[x^n]\Phi_{\{1,01\}^* }(x) \Phi_{\{0,\varepsilon\}}(x)\\
    &=[x^n]\Phi_{(\{\varepsilon\}\cup\{1,01\}\cup\{1,01\}\cup\{1,01\}^2\cup\cdots)} (x)
     \Phi_{\{0,\varepsilon\}}(x)\\
    &\stackrel{\text{S.L.}}{=}[x^n]
      [\Phi_{(\{\varepsilon\}}(x)+\Phi_{(\{1,01\}}(x)+\Phi_{(\{1,01\}^2}(x)+\cdots]
      [\Phi_{(\{0,\varepsilon\}}(x)]\\
    &\stackrel{\text{P.L.}}{=}[x^n]
      \left[(\Phi_{(\{1,01\}}(x))^0+(\Phi_{(\{1,01\}}(x))^1+(\Phi_{(\{1,01\}}(x))^2\cdots\right]
      \left[\Phi_{(\{0,\varepsilon\}}(x)\right]\\
    &=[x^n]\frac{1}{1-\Phi_{\{1,01\}}}\Phi_{\{0,\varepsilon\}}(x)\\
    &=[x^n]\frac{x^0+x^1}{1-(x^1+x^2)}\\
    &=[x^n]\frac{1+x}{1-x-x^2}\\
    &=(n+1)\text{th Fibonacci Number}
  \end{align*}

\newpage

## 2.4 Unambiguous Expressions //Jan 29^th^ Lecture 11

In prevous lecture, we applied our "rule" $\Phi_{AB}(x)=\Phi_A(x)\Phi_B(x)$,
where $AB$ is the result of concatenation of two set of strings,
$$ AB=\{ab|a\in A, b\in B\}. $$

Unfortunately, this rule is not always true. We will explore when and where
we can use it.

Example 2.4.1.
  ~ Let $A=\{0,01,011\},\hspace{5pt}B=\{0,10,100\}$, then
    $$\begin{aligned}
      &AB=\{00,010,0100,010,\cancelto{\text{repetition}}{0110},01100,
        \cancelto{\text{repetition}}{0110},01110,011100\}\\
      &\Phi_{AB}(x)=x^2+x^3+2x^4+2x^5+x^6  &&\text{(1)}\\
      &\Phi_{A}(x)\Phi_{B}(x)=(x+x^2+x^3)(x+x^2+x^3) &&\text{(2)}\\
    \end{aligned}$$

    For a quicker comparison, we can substitute $x=1$ into (1) and (2), we got
    $$ \Phi_{AB}(1)=7\neq 9=\Phi_A(1)\Phi_B(1) $$
    Or we expand (2):
    \begin{align*}
      \text{(2)}&=x^2+2x^2+3x^4+2x^5+x^6\\
      &\neq \Phi_{AB}(x)
    \end{align*}
    This is different from
      $$\Phi_A(x)\Phi_B(x)=\Phi_{A\times B}(x)$$
    where $A\times B$ contains both (0,10) and (01,0), where $AB$ only has one
    corresponding element "010". So $A\times B$ and $AB$ have different numbers
    of weight-3 elements. Thus
    $$\Phi_{AB}(x) \neq \Phi_A(x)\Phi_B(x)=\Phi_{A\times B}(x)$$

Example 2.4.2.
  ~ Let $A=\{0\}^* ,\hspace{5pt}B=\{1\}^* {}$, then
    $$\begin{aligned}
      &AB=\{0\}^* \{1\}^* &&=\{\varepsilon,0,1,00,01,10,11,000,001,\ldots\}\\
      &A\times B &&=\{(\varepsilon,\varepsilon),(0,\varepsilon),
        (\varepsilon, 1),(0,1),(0,0),(1,1),(00,1),\ldots\}
    \end{aligned}$$
    It is easy to see that we can construct a weight preserving bijection.

We will define the term **unambiguous** and **ambiguous** for operations of
concatenation, union, and \* respectively.

Definition 2.4.3. (Definition of Ambiguity for Concatenation)
  ~ If every string in $AB$ is obtained in a **unique** way as the concatenation
    of a string in $A$ and a string in $B$, we say that $AB$ is an **unambiguous**
    expression. If there are distinct pairs $(a,b)$ and $(a',b')$ in $A\times B$
    so that $ab=a'b'$, then this is not the case, and the expression $AB$ is
    **ambiguous**.

Note that if $A$ and $B$ are finite sets, then $AB$ is unambiguous if and only
if $|AB|=|A\times B|$.

**Important Remark: It is the description of the set of string using sum,
concatenation and the * operator which might be ambiguous. A set of string
itself is never ambiguous or unambiguous.**

Proposition 2.4.4.
  ~ If $AB$ is an unambiguous expression for a set of strings, i.e.,
    each string in $AB$ is obtained in exactly one way by concatenating a string
    in $A$ with one in $B$, then
      $$\Phi_{AB}(x)=\Phi_A(x)\Phi_B(x).$$

*Proof.* The unambiguity implies that there is a bijection
$\psi:A\times B\rightarrow AB$ that preserves the value of the weight function.
It follows that $A\times B$ and $AB$ contain the same number of elements of each
weight, so
  $$\Phi_{AB}(x)=\Phi_{A\times B}(x)\stackrel{\text{P.L.}}{=}\Phi_A(x)\Phi_B(x).$$

Definition 2.4.5. (Definition of Ambiguity for Union)
  ~ If $A,B$ are sets of strings, we call the expression $A\cup B$
    **unambiguous** if $A$ and $B$ are disjoint. If this is the case, the
    sum lemma gives $$\Phi_{A\cup B}(x)=\Phi_{A}(x)+\Phi_B(x).$$
\
\
\
\
Recall $A^* = \{\varepsilon\}\cup A\cup AA\cup AAA \cup\cdots$, is $A^* {}$ ambiguous
or not?

The expression $A^* {}$ is unambiguous if every union above is unambiguous (disjoint)
and every concatenation above is unambiguous. In other words, every string in
$A^* {}$ can be obtained uniquely by concatenating a sequence of strings in $A$.

Example 2.4.6.
  ~ $\{0,00\}^* {}$ is ambiguous because $(0)(00)=(0)(0)(0)$ so $A^2\cap A^3 \neq \emptyset$.\
    $\{0,1\}^* {}$ is unambiguous.

Definition 2.4.7. (Definition of Ambiguity for \*)
  ~ In general, any description of a set of strings using $\cup$, concatenation, and
    \* is **unambiguous** if every $\cup$, concatenation, and \* inside is
    **unambiguous**; otherwise, it is *ambiguous*.

Example 2.4.8.
  ~ The description of a set of string
    $$\{0\}^* \,(\{1\}\{1\}^* \{0\}\{0\}^* )^* \,\{1\}^* {}$$ is unambiguous. We
    will present it's proof in next few lectures.

Proposition 2.4.9.
  ~ If $A^* {}$ is an **unambiguous** expression for a set of expression, then
    $$\Phi_{A^* }(x)=\frac{1}{1-\Phi_A(x)}.$$

*Proof.*
\begin{align*}
  \Phi_{A^* }(x)&=\Phi_{(\{\varepsilon\}\cup A\cup AA\cup\cdots)}(x)\\
    &=\Phi_{\{\varepsilon\}}(x)+\Phi_{A}(x)+\Phi_{AA}(x)+\cdots\\
    \intertext{by Sum Lemma as the unambiguity of $A^* {}$ implies that
    the unions are disjoint}
    &=1+\Phi_A(x)+\left[\Phi_{A}(x)\right]^2+\cdots\\
    \intertext{by proposition 2.4.4 applied to each term}
    &=\sum_{n\geq 0}\left[\Phi_A(x)\right]^n
    \intertext{by constant term equals to 0}
    &=\frac{1}{1-\Phi_A(x)}
    \intertext{as required.}
\end{align*}

The previous two propositions allow us to quickly find a generating series from
an unambiguous expression.

Example 2.4.10.
  ~ Let $S = \{0\}^* \,\left(\{1\}\{1\}^* \{0\}\{0\}^* \right)^* \,\{1\}^* {}$.
    \begin{align*}
      \Phi_S(x)&=\frac{1}{1-\Phi_{\{0\}}(x)}\cdot
                 \frac{1}{1-\Phi_{\{1\}\{1\}^* \{0\}\{0\}^* }(x)}\cdot
                 \frac{1}{1-\Phi_{\{1\}}(x)}\\
               &=\left(\frac{1}{1-x}\right)\cdot
                 \left(\frac{1}{1-\Phi_{\{1\}}(x)\frac{1}{1-\Phi_{\{1\}}(x)}
                  \Phi_{\{0\}}(x)\frac{1}{1-\Phi_{\{0\}}(x)}}\right)\cdot
                 \left(\frac{1}{1-x}\right)\\
      \intertext{by proposition}
               &=\left(\frac{1}{1-x}\right)\cdot
                 \left(\frac{1}{1-x\frac{1}{1-x}
                  x\frac{1}{1-x}}\right)\cdot
                 \left(\frac{1}{1-x}\right)\\
      \intertext{by proposition}
               &=\left(\frac{1}{1-x}\right)^2\cdot\frac{1}{1-\frac{x^2}{(1-x)^2}}\\
               &=\frac{1}{(1-x)^2}\cdot\frac{(1-x)^2}{(1-x)^2-x^2}\\
               &=\frac{1}{1-2x}
    \end{align*}

Recall from **Example 2.3.5**. we have if $S=\{\text{all binary string}\}$,
then it's generating series:
  $$\Phi_S(x)=\frac{1}{1-2x}.$$
Is this implying something? We will find out next lecture.

\newpage

## 2.5 Some Decomposition Rules //Jan 31^st^ Lecture 12

**Recap:** for a expression $S=AB^* \cup C$, the order when determining its
ambiguity is check $B^* {}$ first, then $AB^* {}$ concatenation, and lastly
$AB^* \cup C$ union.

Checking the ambiguity of an expression is hard and not the focus of this
course, instead we will construct a unambiguous expression from clearly
unambiguous small subexpressions.

Example 2.5.1.
  ~ Let $S=\{\text{strings with exactly three blocks}\}$. Find $[x^n]\Phi_S(x)$.

*Solution.* We consider two unique constructing sequence for S here:
$$ [00\ldots0][11\ldots1][00\ldots0],\hspace{2cm}[11\ldots1][00\ldots0][11\ldots1].$$

Then we have
\begin{align*}
  S&=\{0,00,\ldots\}\{1,11,\ldots\}\{0,00,\ldots\}\cup
    \{1,11,\ldots\}\{0,00,\ldots\}\{1,11,\ldots\}\\
  &=\underbrace{(\{0\}\{0\}^* )}_{\text{at least one zero}}(\{1\}\{1\}^* )(\{0\}\{0\}^* )
    \cup(\{1\}\{1\}^* )(\{0\}\{0\}^* )(\{1\}\{1\}^* )\\
  &\text{because each string with 3 blocks is either starts 0 or 1 and in either}\\
  &\text{case, decomposes into 3 blocks in exactly one way, this expression is}\\
  &\text{unambiguous.}
\end{align*}

So
\begin{align*}
  \Phi_S(x) &\stackrel{\text{S.L.}}{=} \left(\Phi_{\{0\}}(x)\frac{1}{1-\Phi_{\{0\}}(x)}
  \Phi_{\{1\}}(x)\frac{1}{1-\Phi_{\{1\}}(x)}\Phi_{\{0\}}(x)\frac{1}{1-\Phi_{\{0\}}(x)}\right)+\\
  &\hspace{18pt}\left(\Phi_{\{1\}}(x)\frac{1}{1-\Phi_{\{1\}}(x)}
  \Phi_{\{0\}}(x)\frac{1}{1-\Phi_{\{0\}}(x)}\Phi_{\{1\}}(x)\frac{1}{1-\Phi_{\{1\}}(x)}\right)\\
  &= 2\left(x\frac{1}{1-x}x\frac{1}{1-x}x\frac{1}{1-x}\right)\\
  &=\frac{2x^3}{(1-x)^3}
\end{align*}
So number of string in $S$ with length $n$ is
\begin{align*}
  [x^n]&=\frac{2x^3}{(1-x)^3}=2[x^{n-3}](1-x)^{-3}\\
       &=2{{n-3+3-1}\choose{3-1}}\\
       &=2{{n-1}\choose{2}}.
\end{align*}
\
\
\
\
\
For this numerical result, we can understand it combinatorially:\
Building such desired string, we have two methods at first: choosing 0-starting
sequence or 1-starting sequence; and then we choose two positions where we  
switch the consecutive sequence (or end the consecutive sequence). This results in:
$$ 2\times{{n-1}\choose{2}}. $$

Example 2.5.2.
  ~ Let $S=\{\text{strings without}\geq k\text{ consecutive zeroes}\}$. Find $[x^n]\Phi_S(x)$.

*Solution.* It's easy to see
$$ S=\{\varepsilon,0,\ldots,0^{k-1}\}\{1,10,100,\ldots,1(0)^{k-1}\}^* $$
where $0^k=\underbrace{00\ldots0}_{k\text{ times}}$.

This expression for $S$ is **unambiguous** because if $s\in S$ and $s=a_0a_1\ldots a_l$
where
  $$ a_0\in\{\varepsilon,0,0^{k-1}\}\text{ and }a_1,\ldots,a_l\in\{1,10,\ldots,1(0)^{k-1}\} $$
then $a_0,\ldots,a_l$ can be determined by the string $s$: $a_0$ is the substring
consisting of everything proceeding the first 1 in $s$ (possiblely $a_0=\varepsilon$)
and $a_1,\ldots,a_l$ are the substrings beginning at the occurences of 1 in $s$,
and ending before the next occurence of 1 or the end of $s$.\
So
\begin{align*}
  \Phi_S(x)&=\Phi_{\{\varepsilon,0,\ldots,0^{k-1}\}}(x)\frac{1}
    {1-\Phi_{\{1,10,\ldots,1(0)^{k-1}\}}}\\
           &=(x^0+x^1+\cdots+x^{k-1})\cdot\frac{1}{1-(x^1+x^2+\cdots+x^k)}\\
           &=\left[(1+x+x^2+\cdots)-x^k(1+x+x^2+\cdots)\right]
             \left[\frac{1}{1-x\left(\frac{1}{1-x}-\frac{x^k}{1-x}\right)}\right]\\
           &=\frac{1-x^k}{1-2x+x^{k+1}}.
\end{align*}
Say we want to compute $[x^n]\Phi_S(x)$, equating coefficients:
\begin{align*}
  \frac{1-x^k}{1-2x+x^{k+1}} &= a_0+a_1x+\cdots\\
  1-x^k &= (1-2x+x^{k+1})\\
  0 &= a_n-2a_{n-1}+a_{n-k-1} \hspace{10pt}\ ,n\geq k+1.
\end{align*}

\newpage

# 2.6 Decomposition Using Blocks //Feb 3^rd^ Lecture 13

Consider the following string:

\begin{align*}
  &(\varepsilon)110011101000100\\
  \intertext{splitting with blocks of (100$\cdots$)}
  &(\varepsilon)(1)(100)(1)(1)(10)(1000)(100)\\
  \intertext{and we can abstract further}
  &\{\varepsilon,0,00,\ldots\}(\{1\}\{\varepsilon,0,\ldots,0^{k-1})^*
\end{align*}

The decomposition $S=\{\varepsilon,0,00,\ldots\}(\{1\}
\{\varepsilon,0,\ldots,0^{k-1})^* {}$ is unambiguous because the unique way to
obtain a string $s\in S$ via the above expression is to write $s$ as a
concatenation of pieces, where the pieces at the first char of $s$ and the
occurrence of 1 in $s$.

That is, the expression is unambiguous because it corresponds to a specific
decomposition rule: "split up at each 1".

Also,
$$ S = \{0\}^* (\{1\}\{0\}^* )^* {}$$
is an unambiguous expression for the set of all strings, for the same reason, it
corresponds to a specific decomposition rule: "split up at each 1".

This unambiguous decomposition $\{0\}^* (\{1\}\{0\}^* )^* {}$ for the set of all
strings can be "refined" to produce unambiguous decomposition for other sets
of strings.

Problem 2.6.1
  ~ Let $S=\{\text{strings in which each block of zeroes has length a mutiple
    of 3}$

*Solution.* We formalize it as:
\begin{align*}
  \{\text{all strings}\}=&\{0\}^* (\{1\}\{0\}^* )^* {}\\
    &\hspace{23pt}\downarrow \\
  &\{\varepsilon,000,000000,\ldots\}(\{1\}\{\varepsilon,000,000000\}^* )^* {}=
  \{000\}^* (\{1\}\{000\}^* )^* {}=S\\
\end{align*}
Notice that $\{000\}^* \text{ and } (\{1\}\{000\}^* )^* {}$ are subsets of $\{0\}^*
\text{ and } (\{1\}\{0\}^* )^* {}$ respectively. We have:
  $$ \Phi_S(x)=\frac{1}{1-x^3}\frac{1}{1-\frac{x}{1-x^3}} \text{ by proposition.}$$

We can also, symmetrically, start with the unambiguous expression
  $$ \{1\}^* (\{0\}\{1\}^* )^* {}$$
for the set of all strings (decompose at each 0) to solve similar problems where
the restrictions are on the lengths of blocks of 1's.
\
\
\
**What about there are both restrictions with 0,1's?**\
Sometimes we can find a simple expression, e.g., for even number of 0 and odd
number of 1, we have the generating series as:
$$ \{00,111\}^* $$
but not in general.\

For a string, if we split up it by decomposing at the beginning of each block of
zeros:
\begin{align*}
  &(111)(001)(011)(01)(0111)(0000011)(0)\\
  &\{1\}^* (\{0\}\{0\}^* \{1\}\{1\}^* )^* \{0\}^*
\end{align*}
gives a decomposition $s=a_0a_1\ldots a_k$ where
\begin{align*}
  &a_0\in\{\varepsilon,1,11,\ldots\}=\{1\}^* \\
  &a_k\in\{\varepsilon,0,00,\ldots\}=\{0\}^* \\
  &a_1,\ldots,a_{k-1}\in\{01,001,011,0011,0001,0111,\ldots\}\\
  & \hspace{52pt} =\{0\}\{0\}^* \{1\}\{1\}^*
\end{align*}

This gives the unambiguous decomposition
$$\{\text{all binary strings}\}=\{1\}^* (\{0\}\{0\}^* \{1\}\{1\}^* )^* \{0\}^* $$
similarly,
$$ \{0\}^* (\{1\}\{1\}^* \{0\}\{0\}^* )^* \{1\}^* $$
is unambiguous and obtained by decomposing at the start of each block of 1's.

Problem 2.6.2.
  ~ Find the generating series for
    $S=\{\text{strings where every block}\\ \text{have length}\geq 3\}$.

*Solution.* Start with
$$ \{\text{all binary strings}\}=\{1\}^*
(\underbrace{\{0\}\{0\}^* }_{\{\xcancel{0},\xcancel{00},000,\ldots\}}
 \underbrace{\{1\}\{1\}^* }_{\{\xcancel{1},\xcancel{11},111,\ldots\}})^* \{0\}^*
$$
Then
$$ S=(\{\varepsilon\}\cup\{111\}\{1\}^* )(\{000\}\{0\}^* \{111\}\{1\}^* )^*
  (\{\varepsilon\}\cup\{000\}\{0\}^* ) $$

So
\begin{align*}
  \Phi_S(x)&=\left(1+x^3\left(\frac{1}{1-x}\right)\right)
             \left(\frac{1}{1-x^3\frac{1}{1-x}x^3\frac{1}{1-x}}\right)
             \left(1+x^3\left(\frac{1}{1-x}\right)\right)\\
           &=\left(1+\frac{x^3}{1-x}\right)^2\left(\frac{1}{1-\frac{x^6}{(1-x)^2}}\right)\\
           &=\frac{(1-x+x^3)^2}{(1-x)^2}\cdot\frac{(1-x)^2}{(1-x)^2-x^6}\\
           &=\frac{(1-x+x^3)^2}{(1-x)^2-x^6}\\
           &=\frac{(1-x+x^3)^2}{(1-x-x^3)(1-x+x^3)}\\
           &=\frac{1-x+x^3}{1-x-x^3}.
\end{align*}

\newpage

## 2.7 Decomposition Using Blocks Cont'd //Feb 5^th^ Lecture 14

Example 2.7.1.
  ~ Let
    $S=\{\text{all binary strings with the property that at least}\\
    \text{three 1's and 0's are there when any block appears}\}$. Decompose the set with
    concatenation, $\cup$, and/or \* unambiguously.
    *Solution.*
    $$ S=(\{\varepsilon\}\cup\{111\}\{1\}^* )(\{000\}\{0\}^* \{111\}\{1\}^* )^*
     (\{\varepsilon\}\cup\{000\}\{0\}^* )$$

Example 2.7.2.
  ~ Let $S=\{\text{all binary strings with the property that no two 1's}\\
    \text{and 0's are there when any block appears}\}$. Decompose the set with
    concatenation, $\cup$, and/or \* unambiguously.
    $$ S=(\{\varepsilon\}\cup\{1\})
        \{01\}^*
     (\{\varepsilon\}\cup\{0\})$$

Problem 2.7.3.
  ~ Let $S=\{\text{strings withot "1100" substring}\}$. Decompose the set with
    concatenation, $\cup$, and/or \* unambiguously.

*Analysis.* A string is in $S$ if and only if, for each block $b_0$ of zeros in
$S$ that is preceded by a block $b_1$ of 1's, either $b_0$ or $b_1$ has length 1.
\
\
The description $\{0\}^* (\{1\}\{1\}^* \{0\}\{0\}^* )^* \{1\}^* {}$ can be refined
to describe the set $S$.

$$ \varepsilon\underbrace{10}\underbrace{1110}\underbrace{1000}\underbrace{10}\underbrace{110}
\underbrace{1} $$

Notice that the pieces in $(\{1\}\{1\}^* \{0\}\{0\}^* )^* {}$ have the form
10, 110, 1110, 100, 1000, 111000, etc. We want to eliminate all potential
occurrence of "1100", to do this we replace $\{1\}\{1\}^* \{0\}\{0\}^* $ with
the set
\begin{align*}
  &\{10,100,1000,\ldots,110,1110,11110,\ldots\}\\
  &=\{10\}\{0\}^* \cup \{11\}\{1\}^* \{0\}\\
  &=\{10\}\cup\{11\}\{1\}^* \{0\}\cup\{1\}\{00\}\{0\}^*
\end{align*}
we separated "10" to avoid ambiguity (for displaying purpose).
\
\
Let
$$ A= \{10\}\cup\{11\}\{1\}^* \{0\}\cup\{1\}\{00\}\{0\}^* . $$
\
Since every potential occurrence of "1100" in a string occurs with in the
$(\{1\{1\}^* \{0\}\{0\}^* )^* {}$ part of decomposition, we can describe $S$
unambiguously by restricting it as below:
\begin{align*}
  S&=\{0\}^* (\{10\}\cup\{11\}\{1\}^* \{0\}\cup\{1\}\{00\}\{0\}^* )^* \{1\}^* \\
   &=\{0\}^* A^* \{1\}^* {}.
\end{align*}

So we have
\begin{align*}
  \Phi_A(x)&=\Phi_{\{10\}}(x)+\Phi_{\{11\}}(x)\cdot\frac{1}{1-\Phi_{\{1\}}(x)}
             \cdot\Phi_{\{0\}}(x)\\
           &\mathrel{\phantom{=}} +\,\Phi_{\{100\}}(x)\cdot\frac{1}{1-\Phi_{\{0\}}(x)}\\
           &=\frac{x^2+x^3}{1-x}\\
  \Phi_{\{A^* \}}(x)&=\frac{1}{1-\frac{x^2+x^3}{1-x}}\\
                    &=\frac{1-x}{1-x-x^2-x^3}
  \intertext{hence}
  \Phi_{S}(x)&=\Phi_{\{0\}^* }(x)\Phi_{A^* }(x)\Phi_{\{1\}^* }(x)\\
             &=\frac{1}{1-x}\cdot\frac{1-x}{1-x-x^2-x^3}\cdot\frac{1}{1-x}\\
             &=\frac{1}{(1-x)(1-x-x^2-x^3)}\\
             &=\frac{1}{1-2x+x^4}.
\end{align*}

This technique can solve any "substring-exclusion" problem of the form
"$\underbrace{1\cdots1}_m \underbrace{0\cdots0}_n$" with some finite $m,n$,
and correspondingly change how $A$ is decomposed by finite unions.

\newpage

## 2.8 Recursive Decompositions of Binary Strings //Feb 7^th^ Lecture 15

We will display a way to decompose strings using the idea of recursion and
algebraically find the rational expression of its generating series.

Problem 2.8.1.
  ~ Let $S$ be the set of all binary strings.

*Analysis.* Consider
  $$S\{0,1\}=\{\text{all non-empty strings}\}$$
so
  $$ \{\varepsilon\}\cup S\{0,1\}=S.$$

Is it unambiguous?\
Yes, since

  + $S\{0,1\}$ is the set of all non-empty strings and
  + every string $s$ is uniquely expressible as $s_0 a$ for $s_0\in S, a\in \{0,1\}$.

*Solution.*
By the product and sum lemma,
\begin{align*}
  \Phi_{\{\varepsilon\}}(x)+\Phi_{S}(x)\Phi_{\{0,1\}}(x)&=\Phi_S(x)\\
  1+\Phi_S(x)\cdot(2x)&=\Phi_S(x)\\
  \Phi_S(x)&=\frac{1}{1-2x} \hspace{1cm} (=\sum_{n\geq 0}2^nx^n).
\end{align*}

Problem 2.8.2.
  ~ Let $S=\{\text{all binary strings with each block of zeroes has size}\geq 2\}$.

*Analysis.* Consider an example:
$$ 100011001\underbrace{100} $$
We will decompose at last occurrence of 1 in a string $s \in S$, we get
$$S=s_0a$$
where $s_0\in S$ and $a\in\{1,100,1000,\ldots\}$.\
Decomposing this way is always possible and uniquely determined, unless $s$
consists of all zeros, in which case
$$s\in\{\varepsilon,00,000,\ldots\}$$
This gives the unambiguous decomposition
$$\begin{aligned}
  S &=\{\varepsilon,00,000,\ldots\}\cup S\{1\}\{\varepsilon,00,000,\ldots\}\\
    &=\{\varepsilon\}\cup\{00\}\{0\}^* \cup S\{1\}(\{\varepsilon\}\cup\{00\}\{0\}^* )
  \end{aligned}$$
so by SL, PL we have
\begin{align*}
  \Phi_S(x)&=\Phi_{\{\varepsilon\}}(x)+\Phi_{\{00\}\{0\}^* }(x)+
             \Phi_S(x)\cdot(\Phi_{\{\varepsilon\}}(x)+\Phi_{\{00\}\{0\}^* }(x))\\
           &=1+\frac{x^2}{1-x}+\Phi_S(x)\cdot x\left(1+\frac{x^2}{1-x}\right)
\end{align*}
Equivalently,
\begin{align*}
  \Phi_S(x)\left(1-x\left(1+\frac{x^2}{1-x}\right)\right)&=1+\frac{x^2}{1-x}\\
  \Phi_S(x)(1-x-x(1-x+x^2))&=1-x+x^2\\
  \Phi_S(x)&=\frac{1-x+x^2}{1-2x+x^2-x^3}
\end{align*}

We will solve **Problem 2.7.3.** again using **Recursive Decomposition**.

*Solution.* Let $S=\{\text{strings without "1100" as a substring}\}$.\
Starting with our basic decomposition,
$$\{\varepsilon\}\cup S\{0,1\}=S\ (\text{not true for this set $S$}).$$

but if we construct a set $T$, such that
$$\{\varepsilon\}\cup S\{0,1\}=S\cup T$$
where $T$ is the set of strings with exactly one occurrence of "1100" at the end.
\
This decomposition is unique because every string $s\in S$ is either euqal to
$\varepsilon$, or can be decomposed as $s=s_0$, where $s_0\in S$ and $b\in \{0,1\}$.

$$ T=S\{1100\} $$
This is true (and unambiguous) because every string in $T$ is obtained from
a string in $S$ by appending 1100, and, appending 1100 to a string in $S$
always gives a string in $T$.\
Using SL & PL to both equations relating $S\ \&\ T$, we get
\begin{align*}
  1+2x\Phi_S(x)&=\Phi_S(x)+\Phi_T(x)\\
  1+2x\Phi_S(x)&=\Phi_S(x)+x^4\Phi_S(x)\\
  \Phi_S(x)&=\frac{1}{1-2x+x^4}
\end{align*}
\
\
\
**Excluding any substring:** The fact that $S\{1100\}=T$ in this example above
was crucial, and doesn't necessarily work if "1100" is changed to another
string. Making this technique work for any substring requires more ideas.

Problem 2.8.3.
  ~ Let $S=\{\text{strings withour 10101 as a substring}\}$.

*Analysis.* Let $T=\{\text{strings with exactly one occurrence of 10101 at the end}\}$.
Try to find an definition for $T$:
$$ S\{10101\}=T $$
This **FAILS**, since for example,
$$10 \in S\text{ but }\rlap{$\overbrace{\phantom{(10)(101}}^{\text{not in last}}$}
    \underbrace{(10)(10101)}_{\text{but}\,\in \,T\{01\}} \notin T$$
then we try to define $T$ once again:
$$ S\{10101\}=T\cup T\{01\}$$
Unfortunately, this **FAILS** again, since for example,
$$1010 \in S\text{ but }\rlap{$\overbrace{\phantom{10)(101}}^{\text{not in last}}$}
    \underbrace{(1010)(10101)}_{\text{but}\,\in \,T\{0101\}} \notin T\cup T\{01\}$$
Is it true that $S\{10101\}=T\cup T\{01\}\cup T\{0101\}$? Yes. Unambiguously.
\newpage

# Chapter 3 Recurrences, Binary Trees and Sorting

## 3.1 Coefficients of Rational Functions //Feb 10 ^th^ Lecture 16

Normally, we use **Binomial Theorem**, or **Negative Binomial Theorem** to
extract coefficients:

Example 3.1.1.
  ~ $$\begin{aligned}
        &\mathrel{\phantom{=}}[x^n]\frac{1}{(1-3x)^{-7}}\\
        &=[x^n]\sum_{m\geq 0}{{m+7-1}\choose{7-1}}(3x)^m\\
        &=3^n{{n+6}\choose{6}}.
    \end{aligned}$$

We will introduce **Partial Fraction** as another way to do this more efficiently:

Example 3.1.2.
  ~ $$f(x)=\frac{x-5}{(1-2x)(1-5x)}=\frac{x-5}{1-2x}\cdot\frac{1}{1-5x}$$

    Then $$[x^n]f(x)=\sum_{k=0}^n \left([x^k]\frac{x-5}{1-2x}\cdot
      [x^{n-k}]\frac{1}{1-5x}\right).$$
    This gives a way to extract coefficients from $x^n$ where each coefficient
    is the sum of $n+1$ terms. This is OK, but not good enough.

    Alternatively, observe that:
    \begin{align*}
      \frac{x-5}{(1-2x)(1-5x)}&=\frac{3}{1-2x}-\frac{8}{1-5x}
        \hspace{1cm}\text{(by Partial Fraction)}\\
      &=3\sum_{n\geq 0}(2x)^n - 8\sum_{n\geq 0}(5x)^n\\
      &=\sum_{n\geq 0}(3\cdot 2^n-8\cdot 5^n)x^n
    \end{align*}
    so $[x^n]f(x)=3\cdot 2^n-8\cdot 5^n$.

Example 3.1.3.
  ~ Let $S$ be the set of strings where every block of zeros has even length,
    i.e. $S=\{00,1\}^* {}$.

    Let $$\begin{aligned}
            a_n&=[x^{n-1}]\Phi_S(x)\\
            &=[x^{n-1}]\frac{1}{1-(x+x^2)}\\
            &=[x^n]\frac{x}{1-x-x^2}.
          \end{aligned}$$
    Solving for the coefficients gives the recursive formula defined by
    $$a_0=0, a_1=1, a_n=a_{n-1}+a_{n-2} \text{ for }n\geq 2$$
    so $(a_0,a_1,a_2,a_3,a_4,\ldots)=(0,1,1,2,3,5,8,\ldots)$.\
    This recursive formula gives a way to compute $a_n$ in around $n$ operations.
    We can improve this with **Partial Fractions**. To find $A,B,\alpha,\beta$
    so that $\frac{x}{1-x-x^2}=\frac{A}{1-\alpha x}+\frac{B}{1-\beta x}$.
    We have
      $$\begin{aligned}
          1-x-x^2&=(1-\frac12 x)^2-\frac54 x^2\\
                 &=(1-\frac12 x)^2-(\frac{\sqrt{5}}2 x)^2\\
                 &=(1-\frac{1+\sqrt{5}}2 x)(1-\frac{1-\sqrt{5}}2 x)
        \end{aligned}$$
    this suggests we should take $\alpha=\frac{1+\sqrt{5}}2,
    \beta=\frac{1-\sqrt{5}}2$. So we want $A, B$ such that
    $$\begin{aligned}
    \frac{x}{(1-\frac{1+\sqrt{5}}2 x)(1-\frac{1-\sqrt{5}}2 x)} &=
    \frac{A}{(1-\frac{1+\sqrt{5}}2 x)}+\frac{B}{(1-\frac{1-\sqrt{5}}2 x)}\\
    x&=A(1-\frac{1-\sqrt{5}}2 x)+B(1-\frac{1+\sqrt{5}}2 x)
    \end{aligned}$$
    equating coefficients we get
    $$\begin{cases}
        0=A+B & \text{take }x=0 \\
        1=\frac{-1-\sqrt5}2 A- \frac{1+\sqrt5}2 B & \text{take }x=1
      \end{cases}$$
    solving it gives
    $$A=\frac1{\sqrt5},B=-\frac{1}{\sqrt5}.$$
    Then
    $$\begin{aligned}
        \frac{x}{1-x-x^2}&=
          \frac1{\sqrt5}\cdot\left(1-\left(\frac{1+\sqrt5}{2}\right)x\right)^{-1}-
          \frac1{\sqrt5}\cdot\left(1-\left(\frac{1-\sqrt5}{2}\right)x\right)^{-1}\\
        &=\frac1{\sqrt5}\sum_{n\geq 0}{{n+1-1}\choose{1-1}}\left(\frac{1+\sqrt5}{2}\right)^n x^n-
          \frac1{\sqrt5}\sum_{n\geq 0}{{n+1-1}\choose{1-1}}\left(\frac{1-\sqrt5}{2}\right)^n x^n\\
        &=\frac1{\sqrt5}\sum_{n\geq 0}\left(\frac{1+\sqrt5}{2}\right)^n x^n-
          \frac1{\sqrt5}\sum_{n\geq 0}\left(\frac{1-\sqrt5}{2}\right)^n x^n\\
        &=\frac1{\sqrt5}\sum_{n\geq 0}\left(\left(\frac{1+\sqrt5}{2}\right)^n-
                                            \left(\frac{1-\sqrt5}{2}\right)^n\right) x^n
      \end{aligned}$$
    Thus
      $$ a_n=\frac1{\sqrt5}\left(\left(\frac{1+\sqrt5}{2}\right)^n-
      \left(\frac{1-\sqrt5}{2}\right)^n\right).$$

**Remark:**\
Notice that
$$\left(\frac{1+\sqrt5}{2}\right)^n-
\left(\frac{1-\sqrt5}{2}\right)^n = (1.618\ldots)^n - (-0.618\ldots)^n$$
which means this formula also gives a very precise asymptote estimate for
the Fibonacci number $a_n$, since $\lim_{n\to\infty}\left(\frac{1-\sqrt5}2\right)=0$,
we have
  $$ a_n \sim \frac1{\sqrt5} \left(\frac{1+\sqrt5}2\right)^n\text{, as }a_n\to\infty$$

***Something else to explore:***\
For a computer to compute $3^{10000}$, it's time complexity, in normal sense, is $O(n)$ where
$n=10000$, we can improve this by the fact that:
$$ 10000 = 8192 + 1024 + 512 + 256 + 16 = 2^{13} + 2^{10} + 2^9 + 2^8 + 2^4$$
then
\begin{equation}
  3^{10000} = (3)^{2^{13}}\cdot(3)^{2^{10}}\cdot(3)^{2^9}\cdot(3)^{2^8}\cdot(3)^{2^4}.
\end{equation}
We can design an algorithm for an computer to compute the sequence
$$ (3)^{2^{0}},(3)^{2^{1}},(3)^{2^{2}},\ldots,(3)^{2^{13}} $$
where each $(3)^{2^{i}}$ is the square of the former one. We record each term and
finally substitute them into equation (1) to compute the product.
\
Another computing technique when deal with real numbers is that to avoid
imprecision, we have
$$\begin{aligned}
  \left(\frac{A+{x^{\frac1k}}}{B}\right)^n &=\left(\frac AB+B^{-1}{x^{\frac1k}}\right)^n\\
    &=\sum_{i=0}^n {n \choose i}{\left(\frac AB\right)}^{n-i}{\left(B^{-1}{x^{\frac1k}}\right)}^i\\
    &=\sum_{i=0}^n {n \choose i}{\left(\frac AB\right)}^{n-i} B^{-i}x^{\frac ik}.
  \end{aligned}$$
where $A,B$ are constants.
\newpage

## 3.2 Solutions to Recurrence Equations //Feb 12^nd^ Lecture 17

We present an general method for founding Generating Series for any fraction form.

Proposition 3.2.1. (Partial Fraction)
  ~ Let $f(x), g(x)$ be polynomials where $deg(f)<deg(g)$ and $g$ has
    factorization
    $$ g(x)=(1-{\alpha}_1 x)^{p_1}(1-{\alpha}_2 x)^{p_2}\ldots(1-{\alpha}_k x)^{p_k} $$
    where $p_1,p_2,\ldots,p_k\in\mathbb{N}_{\geq 1}$ and distinct
    ${\alpha}_1,{\alpha}_2,\ldots,{\alpha}_k$. Then there exist polynomials
    $f_1,f_2,\ldots,f_k$ such that $deg(f_i)<p_i$ for each $i$, and
    $$\frac{f(x)}{(1-{\alpha}_1 x)^{p_1}\ldots(1-{\alpha}_k x)^{p_k}}=
      \frac{f_1(x)}{(1-{\alpha}_1 x)^{p_1}}+\cdots+
      \frac{f_k(x)}{(1-{\alpha}_k x)^{p_k}}$$

**Note:** A similar statement is true if $g$ is not factored completely, but
into relatively prime polynomial factors. For example,
$$ \frac{1-3x+2x^2}{(1-4x)(1+x+x^2)}=\frac{A}{1-4x}+\frac{Bx+C}{1+x+x^2}. $$

Proposition 3.2.2.
  ~ Let $\alpha\in\mathbb{R},\,\alpha\neq0,\,p\geq 1$, and $f(x)$ be a polynomial
    of degree $<p$. Then there exists a polynomial $h(n)$ of degree $<p$ such
    that
    $$ [x^n]\frac{f(x)}{(1-\alpha x)^p}=h(n)\cdot{\alpha}^n. $$

Example 3.2.3.
  ~ $$[x^n]\frac{Ax+B}{(1-2x)^2}=(Cn+D)\cdot\alpha^n$$

*Proof.* Let $f(x)=c_0+c_1x+c_2x^2+\cdots+c_{p-1}x^{p-1}=\sum_{i=0}^{p-1}c_ix^i$.
so $$\begin{aligned}
     [x^n]\frac{f(x)}{(1-\alpha x)^p}&=[x^n]\frac{\sum_{i=0}^{p-1}c_ix^i}{(1-\alpha x)^p}\\
      &=\sum_{i=0}^{p-1}[x^n]\frac{c_ix^i}{(1-\alpha x)^p}\\
      &=\sum_{i=0}^{p-1}c_i\cdot[x^{n-i}]\frac{1}{(1-\alpha x)^p}\\
      &=\sum_{i=0}^{p-1}c_i\cdot{{((n-i)+p-1)}\choose{p-1}}\alpha^{n-i}\hspace{1cm}\text{by NBT}
   \end{aligned}$$
For each $i$ and $p$, we have
  $$\begin{aligned}
    {{n-i+p-1}\choose{p-1}}&=\frac{(n-i+p-1)!}{(p-1)!(n-i)!}\\
      &=\frac{1}{(p-1)!}\cdot\underbrace{(n-i+p-1)(n-i+p-2)\cdots(n-i+1)}_{p-1\text{ terms}}
  \end{aligned}$$
this is a polynomial of degree $p-1$ in $n$ (when $p$ and $i$ are viewed as fixed).
Call this polynomial $h_i(n)$, we have
  $$\begin{aligned}
     [x^n]\frac{f(x)}{(1-\alpha x)^p}&=\sum^{p-1}_{i=0}c_i\cdot h_i(n)\cdot\alpha^{n-i}\\
     &=\alpha^n\cdot\underbrace{\sum^{p-1}_{i=0}\frac{c_i}{\alpha^i}h_i(n)}_{h(n)}.
  \end{aligned}$$

Since each $h_i$ is a polynomial of degree $<p$ in $n$, and the summation is a
linear combination of the $h_i$, the summation is a polynomial $h(n)$ of degree
$<p$.

Corollary 3.2.3.
  ~ Under the same hypothesis as the proposition 3.2.2., there are polynomials
    $$ h_1(n),\ldots,h_k(n)\hspace{1cm}\text{such that $deg(h_i)<p_i$, and }$$
    $$[x^n]\frac{f(x)}{(1-\alpha_1x)^{p_1}\cdots(1-\alpha_kx)^{p_k}}=
      h_1(n)\cdot\alpha_1^n+\cdots+h_k(n)\cdot\alpha_k^n$$

Knowing the formula takes this form, we can often solve easily for the constant
given some extra information we believe.

Example 3.2.4.
  ~ Suppose there is a counting problem where the answers are a sequence $a_0,a_1,\ldots$
    where it is known that $a_0=1,a_1=9,a_2=60$ and
    $$\sum_{k\geq 0}a_kx^k=\frac{1+3x^2}{(1-2x)^2(1-5x)}.$$
    By Corollary 3.2.3., there are constants $A,B,C$ such that
    $$ a_n=(An+B)\cdot2^m+C\cdot5^n $$
    Setting
    $$\begin{aligned}
      n=0,&\text{ we have } 1=a_0=B+C\\
      n=1,&\text{ we have } 9=a_1=2(A+B)+5C\\
      n=2,&\text{ we have } 60=a_2=4(2A+B)+25C\\
    \end{aligned}$$
    which gives
    $$A=-\frac76,\ B=-\frac{19}9,\ C=\frac{28}9.$$

\newpage

## 3.3 Characteristic Polynomial //Feb 14^th^ Lecture 18

Example 3.3.1.
  ~ Let $a_0=1,\ a_1=4,\ a_n=5a_{n-1}-6a_{n-2}\text{ for }n\geq 2$. Say we want
    to a explicit formula for $a_n$. Define a formal power series
    $$ A(x)=a_0+a_1x+\cdots=\sum_{i=0}a_ix^i $$
    so we have $a_n-5a_{n-1}+6a_{n-2}=0$ for $n\geq2$ and thus
    $$\begin{aligned}
      [x^n]A(x)-5\cdot[x^{n-1}]A(x)+6\cdot[x^{n-2}]A(x)&=0\\
      [x^n]A(x)+[x^n](-5x\cdot A(x))+[x^n](6x^2\cdot A(x))&=0\\
      [x^n][A(x)-5xA(x)+6x^2A(x)]&=0\\
      [x^n]A(x)(1-5x+6x^2)&=0 \text{ for }n\geq2
    \end{aligned}$$
    so
    $$\begin{aligned}
      A(x)(1-5x+6x^2)&=\text{ some deg $\leq1$ linear polynomial }\\
      A(x)&=\frac{\text{ some deg $\leq1$ linear polynomial }}{(1-5x+6x^2)}\\
      &=\frac{\text{ some deg $\leq1$ linear polynomial }}{(1-2x)(1-3x)}
    \end{aligned}$$
    By **Corollary 3.2.3**, there exists $C,D$ such that
    $$ a_n=[x^n]A(x)=C\cdot2^n+D\cdot3^n \text{ for all }n$$
    We can find $C,D$ by the fact that we know $a_0,a_1$
    $$C+D=1,\ 2C+3D=4 \implies C=-1,\ D=2$$
    Then $a_n=-2^n+2(3^n)$.

Definition 3.3.2.
  ~ The **Characteristic Polynomial** of a recursive relation of the form
    $$ a_n+c_1a_{n-1}+c_2a_{n-2}+\cdots+c_ka_{n-k}=0 $$
    is defined to be the polynomial
    $$ 1+c_1x+c_2x^2+\cdots+c_kx^k.$$

Theorem 3.3.3.
  ~ Let $\alpha_1,\ldots,\alpha_l$ be distinct and non-zero, and let
    $p_1,\ldots,p_l\in\mathbb{N}_{\geq1}$.Let $f(x)=(1-\alpha_1x)^{p_1}
    (1-\alpha_2x)^{p_2}\cdots(1-\alpha_lx)^{p_l}$.\
    Then a sequence $a_0,a_1,\ldots$ obeys a linear recursive relation with
    characteristic polynomial $f(x)$ if and only if\
    there exist polynomial $h_1,\ldots,h_l$ where $deg(h_i)<p_i$ for each $i$,
    and
    $$ a_n=h_1(n)\alpha_1^n+h_2(n)\alpha_2^n+\cdots+h_l(n)\alpha_l^n\text{ for all }n. $$

*Proof.* Let $f(x)=1+c_1x+c_2x^2+\cdots+c_kx^k$ (in its expanded form).\
Then $a_n$ obeys a recurrence with characteristic polynomial $f(x)$\
*iff* $a_n+c_1a_{n-1}+c_2a_{n-2}+\cdots+c_ka_{n-k}=0\text{ for all }n>k$\
Let $A(x)=\sum_{i\geq0}a_ix^i$.\
*iff* $[x^n]A(x)+c_1[x^{n-1}]A(x)+\cdots+c_k[x^{n-k}]A(x)=0$\
*iff* $[x^n](A(x)(1+c_1x+\cdots+c_kx^k))=0$\
*iff* $A(x)(1+c_1x+\cdots+c_kx^k)$ is a polynomial of degree $<k$\
*iff* $$\begin{aligned}
          A(x)&=\frac{\text{(some polynomial of degree) }<k}{(1+c_1x+\cdots+c_kx^k)}\\
          &=\frac{\text{(some polynomial of degree) }<k}{(1-\alpha_1x)^{p_1}
          (1-\alpha_2x)^{p_2}\cdots(1-\alpha_lx)^{p_l}}
      \end{aligned}$$
*iff* $$ a_n=h_1(n)\alpha_1^n+h_2(n)\alpha_2^n+\cdots+h_l(n)\alpha_l^n\text{ for all }n $$
by Corollary 3.2.3.

Example 3.3.4.
  ~ Find an explicit formula for the sequence $a_0,a_1,\ldots$ satisfying
    $$a_0=0,a_1=1,a_2=13 \text{ and } a_n=3a_{n-1}-4a_{n-3}.$$
    Since $a_n=3a_{n-1}-4a_{n-3}$, the characteristic polynomial is
    $$ 1-3x+4x^3=(1-2x)^2(1+x) $$
    so formula is given by $a_n=h_1(n)\cdot2^n+h_2(n)\cdot(-1)^n$ where
    $deg(h_1)<2$ and $deg(h_2)<1$. Then
    $$a_n=(Pn+Q)\cdot2^n+R\cdot(-1)^n\text{, $P,Q,R$ are constant.}$$
    Subing n=0,1,2, we get $P=2,Q=-1,R=1$ and thus
    $$ a_n=(2n-1)2^n+(-1)^n. $$

Example 3.3.5.
  ~ Say we have $$a_n=3n^2+7-2^{n-1}$$ we want a recurrence relation.
    We write $$a_n=(3n^2+7)1^n+(-\frac12)2^n$$ and this gives the character polynomial
    $$ (1-x)^3(1-2x)=1-5x+9x^2-4x^3+2x^4 $$ and thus
    $$ a_n-5a_{n-1}+9a_{n-2}-4a_{n-3}+2a_{n-4}=0.$$
