# Week of @May 23, 2022 Combinatorics

### Table of Contents

---

## Theorem Sum Rule

When the later choices don’t depend on the previous ones

## Theorem Product Rule

When the later choices depend on the previous ones

## 4 Different ways of making choices

`@Param` Let $S$ be a set with $n$ elements.

`@Param` Suppose we need $r$ elements from $S$

<aside>
💡 The expression in **green** represent the number of choices at the current slot(if i keep writing ‘choices’ the whole table gets really big lol)

</aside>

$$
\begin{array}{|c|c|c|c|c|c|}
\hline
\text{Element}&?&?&?&\cdots&?\\
\hline
\text{Index}&1&2&3&\cdots&r\\
\hline
\end{array}
$$

1. With replacement
    
    We always have $n$ elements to choose from. For each slot, we have $n$ choices.
    
    There are $r$ slots, so $\underbrace{n\cdot n\cdot n\cdots n}_{r\text{ terms}} = n^r$ total choices.
    
    $$
    \begin{array}{|c|c|c|c|c|c|}
    \hline
    \text{Element}&?{\color{green}\;n\text{ choices}}&?{\color{green}\;n\text{ choices}}&?{\color{green}\;n\text{ choices}}&\cdots&?{\color{green}\text{ still}\;n\text{ choices}}\\
    \hline
    \text{Index}&1&2&3&\cdots&r\\
    \hline
    \end{array}
    $$
    
2. Without replacement
    
    We lose 1 element to choose from after each choice. 
    
    So the number of choices is $n, n-1, n-2\dots$
    
    $$
    \begin{array}{|c|c|c|c|c|c|}
    \hline
    \text{Element}&?{\color{green}\;n}&?{\color{green}\;n-1}&?{\color{green}\;n-2}&\cdots&?{\color{green}\;n-r+1\text{}}\\
    \hline
    \text{Index}&1&2&3&\cdots&r\\
    \hline
    \end{array}
    $$
    
    Total choices is:
    
    $$
    n\cdot n-1\cdot n-2\cdot\; \dots \;\cdot (n-r+1)
    $$
    
    So if we have $r=n$ slots this product just becomes the factorial $n!$.
    
    $$
    \begin{array}{|c|c|c|c|c|c|}
    \hline
    \text{Element}&?{\color{green}\;n}&?{\color{green}\;n-1}&?{\color{green}\;n-2}&\cdots&?{\color{green}\;n-n+1 = 1\text{}}\\
    \hline
    \text{Index}&1&2&3&\cdots&n\\
    \hline
    \end{array}
    $$
    
3. Permutation
    
    Ordering matters here.
    
    Notice how this is exactly the same as choosing without replacement
    
    $$
    P(n, r) = P^n_r=\frac{n!}{(n-r)!}
    $$
    
4. Combination
    
    Ordering doesn’t matter here.
    
    $$
    \underbrace{C(n, r  ) = C^n_r = {n\choose r}}_\text{the 3 common notations} = \frac{n!}{r!(n-r)!}
    $$
    
    The $r!$ term in the denominator removes the duplicates from $P^n_r$
    

## Theorem Inclusion Exclusion

`@Hint` This is basically saying don’t count the overlapping sections multiple times when finding the size of unions

### 2–Set version

$$
|A\cup B| = |A| + |B| - |A\cap B|
$$

![Untitled](Week%20of%20@May%2023,%202022%20Combinatorics%20067951cf5db74d35b2f17e7b5e9a4c00/Untitled.png)

Notice if we just do $|A| + |B|$ the intersection gets counted twice.

So we just subtract it.

### 3–Set version

$$
|A\cup B\cup C| = |A| + |B| + |C| - |A\cap B| - |A\cap C|  - |B\cap C|+ |A\cap B\cap C|
$$

![Untitled](Week%20of%20@May%2023,%202022%20Combinatorics%20067951cf5db74d35b2f17e7b5e9a4c00/Untitled%201.png)

So the 2–set intersections are removed correctly, but the red section also got removed when the subtractions happened. We need to add that back, hence $+|A\cap B \cap C|$

- Details
    
    $|A| + |B| + |C|$counts:
    
    $\{x\mid x\in A\text{ only}\}$ once
    
    $\{x\mid x\in B\text{ only}\}$ once
    
    $\{x\mid x\in C\text{ only}\}$ once
    
    $\{x\mid x\in A\cap B\text{ only}\}$ twice
    
    $\{x\mid x\in A\cap C\text{ only}\}$ twice
    
    $\{x\mid x\in B\cap C\text{ only}\}$ twice
    
    $\{x\mid x\in A\cap B\cap C\text{ only}\}$ 3 times
    
    After $-|A\cap B|$, the changes are:
    
    $\{x\mid x\in A\cap B\text{ only}\}$ is now counted once
    
    $\{x\mid x\in A\cap B\cap C\text{ only}\}$ 2 times
    
    Similarly, after $-|A\cap C| - |B\cap C|$:
    
    $\{x\mid x\in A\cap C\text{ only}\}$ is now counted once
    
    $\{x\mid x\in B\cap C\text{ only}\}$ is now counted once
    
    $\{x\mid x\in A\cap B\cap C\text{ only}\}$ 0 times
    
    Now add it back.
    

### Generalized Version

![Screen Shot 2022-05-25 at 6.02.03 PM.png](Week%20of%20@May%2023,%202022%20Combinatorics%20067951cf5db74d35b2f17e7b5e9a4c00/Screen_Shot_2022-05-25_at_6.02.03_PM.png)

How to read this formula:

$\sum^n_{i = 1}|A_i|\hspace{1em}$ add all individual sizes together

$-\sum_{1\le i < j \le n}|A_i\cap A_j|\hspace{1em}$ remove all the 2–set intersections

$\sum_{1\le i < j <k\le n}|A_i\cap A_j\cap A_k|\hspace{1em}$ add back all the 3–set intersections

Keep alternating by the rule:

- Remove the even-number set intersections, so 2 set intersection, 4 set intersection etc.
- Add back the odd-number set intersections, so 3 set intersection, 5 sect intersection etc.

This is also where the $(-1)^{n + 1}$ came from. 

- When $n$ is even, $n+1$ is odd. $(-1)^{n+1} = -1$.
- When $n$ is odd, $n+1$ is even. $(-1)^{n+1} = +1$.

until we reach the intersection of all sets.

`@Hint` In the subscript the reason that $1\le i < j < k\le n$ has $<$ not $\le$ is because when we take set $A_i$, we can’t choose $A_i$ again so we must choose the next one.

## Theorem Binomial Theorem

`@Param` A binomial: $(x  + y)^n$ with $x, y\in\R, n\in\N$

$$
\sum^n_{k = 0}{n\choose k}x^{n-k}y^k
$$

Notice the binomial expansion has 3 components:

1. The coefficient
2. $x^{n-k}$
3. $y^{k}$

For the $x, y$ part, the exponent at each term always add up to $n$:

`@EX` $(x + y)^2 = x^2 + 2xy + y^2$. first term is 2 + 0, second term is 1 + 1, 3rd term is 0 + 2

## Poker Hands

![Screen Shot 2022-05-26 at 6.38.33 PM.png](Week%20of%20@May%2023,%202022%20Combinatorics%20067951cf5db74d35b2f17e7b5e9a4c00/Screen_Shot_2022-05-26_at_6.38.33_PM.png)

# Examples

### EX.1 Prove the binomial theorem

`Stategies: Induction`

![Screen Shot 2022-05-11 at 11.41.12 AM.png](Week%20of%20@May%2023,%202022%20Combinatorics%20067951cf5db74d35b2f17e7b5e9a4c00/Screen_Shot_2022-05-11_at_11.41.12_AM.png)

- $\text{Answer}.$
    
    ### Part (a)
    
    Plug in $n = 1, 2, 3$:
    
    $$
    \begin{aligned}
    (a+b)^1 &= a + b = \binom 10a^1 + b^1\\
    (a+b)^2 &=a^2 + 2ab + b^2 = \binom 20a^2 + \binom 21 ab + b^2\\
    (a +b)^3 &= a^2+3a^2b+3ab^2+b^3 = \binom 30 a^3 + \binom 31a^2b + \binom 32ab^2 + b^3
    \end{aligned}
    $$
    
    ### Part (b) Pascal’s Identity
    
    Expand the given expression by the definition of binomials
    
    $$
    \begin{aligned}
    \binom nk + \binom n{k-1} &=\frac{n!}{k!(n-k)!}  +\frac{n!}{(k-1)!(n-k+1)!}\\
    &=\frac{n!(n-k+1)}{k!(n-k+1)!} + \frac{n!k}{k!(n-k+1)!}\\
    &=\frac{n!(n-k+1+k)}{k!(n-k+1)!}=\frac{n!(n+1)}{k!(n-k+1)!}\\
    &=\frac{(n+1)!}{k!(n-k+1)!}\\
    &=\binom{n+1}{k}
    \end{aligned}
    $$
    
    ### Part (c)
    
    Basis step: $n = 1$ shown in part (a)
    
    Induction step:
    
    Assume for $n = m$ the binomial theorem holds:
    
    $$
    (a + b)^m = \sum^m_{i = 0}\binom mia^{m-i}b^i
    $$
    
    Then for $n = m +1$:
    
    $$
    \begin{aligned}
    (a+b)^{m + 1} &= (a+b)^m\cdot (a + b)\\
    &=\sum^m_{i = 0}\binom mi a^{m-i}b^i(a+b)\\
    &=\sum^m_{i = 0}\binom mi a^{m-i+1}b^i +\underbrace{\sum^m_{i = 0}\binom mi a^{m-i}b^{i+1}}\\
    
    \end{aligned}
    $$
    
    Shift the index for the under-braced term:
    
    $$
    \sum^m_{i = 0}\binom mi a^{m-i}b^{i+1} = \sum^m_{i = 1}\binom m{i-1} a^{m-i+1}b^{i}
    $$
    
    Now the 2 summations have the same summand except the binomial part.
    
    Combine like terms:
    
    $$
    \begin{aligned}
    &\sum^m_{i = 0}\binom mi a^{m-i+1}b^i + 
    \sum^m_{i = 1}\binom m{i-1} a^{m-i+1}b^{i}\\
    &=a^m + \left[\sum^m_{i = 1}\left(\binom mi + \binom m{i-1}\right)a^{m-i+1}b^{i} \right]+ b^m\\
    
    \end{aligned}
    $$
    
    Using the result from Part (b):
    
    $$
    \begin{aligned}
    
    =a^m + \left[\sum^m_{i = 1}\binom{m+1}{i}a^{m-i+1}b^{i} \right]+ b^m\\
    
    \end{aligned}
    $$
    
    Merge the first and last term by starting the sum at $i = 0$:
    
    $$
    =\sum^m_{i = 0}\binom{m+1}{i}a^{m+1-i}b^{i} 
    $$
    
    Thus the binomial theorem holds for $m+1$.
    

### EX.2

$\text{Q.}$ Calvin wants to go to Milwaukee. He can choose from 3 bus services or 2 train services to head from home to downtown Chicago. From there, he can choose from 2 bus services or 3 train services to head to Milwaukee. How many ways are there for Calvin to get to Milwaukee from his house?

`Stategies: Sum Rule & Product Rule`

- $\text{Answer.}$
    
    So Calvin needs to take 2 steps.
    
    1. Home → Downtown Chicago
    2. Downtown Chicago → Milwaukee
    
    Consider each step separately first.
    
    1. 3 buses OR 2 trains
    2. 2 bus services OR 3 train services
    
    So at each step, there are $2 + 3 = 3 + 2 = 5$ combinations.
    
    Now we combine the 2 steps.
    
    For each travel method at step 1, there are 5 travel methods in step 2.
    
    Therefore $5\cdot 5 = 25$ total combinations from home to Milwaukee.
    

### EX.3

$\text{Q.}$ A new company with just two employees, Sanchez and Patel, rents a floor of a building with 12 offices. How many ways are there to assign different offices to these two employees?

`Stategies: Permutation`

- $\text{Answer.}$
    
    Assuming they are not sharing rooms, then after Sanchez gets a room, Patel can’t choose that room again.
    
    So the total number of choices decreases after each choice.
    
    Without loss of generality, let’s assign Sanchez a room first.
    
    Then Sanchez has 12 offices to choose from.
    
    Patel will have 11 to choose from after Sanchez.
    
    For each possible choice for Sanchez, there are 11 choices for Patel.
    
    Therefore $12\cdot 11 = 132$ total ways
    
    Same idea if we use permutation $P(12, 2) = \frac{12!}{(12-2)!} = 12 \cdot 11 = 132$
    

### EX.4

$\text{Q.}$ How many bit strings of length 8 either start with bit 1 or end with the two bits 00

`Stategies: Sum Rule, Product Rule, Inclusion Exclusion Principle`

- $\text{Answer.}$
    
    Let’s extract the given first.
    
    - Length is 8
    - Constraint: Start with 1 OR end with 00
    - It’s a bit string, so each bit can only be 0 or 1
    
    Consider strings that start with 1 first.
    
    We have 2 choices at each bit except the first 1.
    
    $$
    1\cdot 2^7 = 2^7
    $$
    
    Now consider strings that end with 00.
    
    We have 2 choices at each bit except the last 2 bits.
    
    $$
    2^6\cdot 1\cdot 1 = 2^6
    $$
    
    But notice that we counted the strings that start with 1 and end with 00 twice.
    
    So we need to use the inclusion exclusion principle here.
    
    The number of strings that start with 1 and end with 00 is:
    
    $$
    1\cdot 2^5\cdot 1\cdot 1 = 2^5
    $$
    
    Now use inclusion exclusion principle:
    
    $$
    \underbrace{2^7}_{|A|} + \underbrace{2^6}_{|B|} - \underbrace{2^5}_{|A\cap B|} = 160
    $$
    

### EX.5

$\text{Q.}$ How many positive integers not exceeding 1000 are divisible by 7 or 11?

`Strategies: Inclusion Exclusion Principle`

- $\text{Answer.}$
    
    The number of integers divisible by 7 is $\lfloor\frac {1000}7\rfloor  = 142$
    
    The number of integers divisible by 11 is $\lfloor\frac {1000}{11}\rfloor  = 90$
    
    The number of integers divisible by 7 and 11 is $\lfloor\frac {1000}{77}\rfloor  = 12$
    
    So the answer is:
    
    $$
    142 + 90 - 12 = 220
    $$
    

### EX.6

$\text{Q.}$ A survey of households in the United States reveals that 96% have at least one television set, 98% have telephone service, and 95% have telephone service and at least one television set. What percentage of households in the United States have neither telephone service nor a television set?

`Strategies: Inclusion Exclusion Principle`

- $\text{Answer.}$
    
    $$
    \underbrace{1}_\text{everyone}-\underbrace{(\overbrace{0.96}^{|A|} +\overbrace{0.98}^{|B|} - \overbrace{0.95}^{|A\cap B|})}_\text{people with either phone or TV} = 0.01 = 1\%
    $$
    

### EX.7

$\text{Q.}$ There are 345 students at a college who have taken a course in calculus, 212 who have taken a course in discrete mathematics, and 188 who have taken courses in both calculus and discrete mathematics. How many students have taken a course in either calculus or discrete mathematics?

`Strategies: Inclusion Exclusion Principle`

- $\text{Answer.}$
    
    $$
    (\overbrace{345}^{|A|} +\overbrace{212}^{|B|} - \overbrace{188}^{|A\cap B|}) = 369
    $$
    

### EX.8

How many permutations of the letters ABCDEFGH contain the string ‘ABC’?

`Stategies: Permutation`

- $\text{Answer.}$
    
    Essentially 3 of the slots are glued together to become 1 slot, so we only care about 6 positions.
    
    We are permuting all the elements from $\{ABC, D, E, F, G, H\}$.
    
    So we use choosing without replacement, or permutation with $r = n$.
    
    The answer is $6!$
    

### EX.9

![Screen Shot 2022-05-26 at 12.15.29 PM.png](Week%20of%20@May%2023,%202022%20Combinatorics%20067951cf5db74d35b2f17e7b5e9a4c00/Screen_Shot_2022-05-26_at_12.15.29_PM.png)

`Stategies: Combination, Product Rule`

- $\text{Answer.}$
    
    **Part 1**
    
    Directly use ${14\choose 6 } = 3003$
    
    Notice we use combination not permutation here because the order of how the friends are chosen doesn’t matter. Choosing friend ABC is the same as choosing friend CBA
    
    **Part 2**
    
    Now ordering matters. Seating order ABC is different from CBA.
    
    Suppose we have chosen 6 friends and there are 6 chairs.
    
    Then similar to EX.3, the number of available seats decreases after each choice.
    
    Use choosing without replacement or permutation with $r = n$ here: there are $6!$ choices.
    
    Now we combine this with the results from part 1.
    
    For each combination of friends, there are $6!$ seating permutations.
    
    So we multiply: $3003\cdot 6! = 2162160$
     total ways.
    

### EX.10

`Stategies: Binomial theorem`

$\text{Q.}$ What is the coefficient of $x^9$ in $(2-x )^{19}$

- $\text{Answer.}$
    
    We will worry about the 2 and the negative sign later. Let’s consider $(x + y)^{19}$ first
    
    Using the binomial theorem, since $x^9 = x^{19-10}$, the term is:
    
    $$
    \binom{19}{10}x^9y^{10}
    $$
    
    That’s our base. Now we need to consider 2 and the negative sign.
    
    Rewrite the given: $((-x) + 2)^{19}$
    
    Plug in: $x := -x$, $y:=2$
    
    $$
    {19\choose 10}(-x)^9\cdot 2^{10} = {19\choose 10}\underbrace{(-1)^9}_\text{odd exponent}\cdot 1024\cdot x^9 = -{19\choose 10}\cdot 1024\cdot x^9
    $$
    
    The numerical answer is 94595072
    

### Hard EX.11

![Screen Shot 2022-05-26 at 12.36.34 PM.png](Week%20of%20@May%2023,%202022%20Combinatorics%20067951cf5db74d35b2f17e7b5e9a4c00/Screen_Shot_2022-05-26_at_12.36.34_PM.png)

`Stategies: Product Rule`

- $\text{Answer.}$
    
    We are given the prime factors of 735000, so any product of these prime factors is a divisor of 735000.
    
    Observations:
    
    1. We don’t need to use all of the prime factors at once. So we need to consider the cases of using different amount of factors.
    2. The ordering doesn’t matter. $3\cdot 5$ and $5\cdot 3$ produce the same divisor.
    
    But notice $2_a\cdot 3\cdot 5_a = 2_b\cdot 3\cdot 5_a$ since we have multiple 2’s and 5’s
    
    **Therefore we are actually choosing the exponents, not directly choosing the factors.**
    
    $$
    2^\square\cdot 3^\square\cdot 5^\square\cdot 7^\square
    $$
    
    Each box has different amount of choices depending on the original exponent
    
    `@EX` 2 has 4 choices because 0 is a valid choice in addition to 1, 2, 3.
    
    Similarly add one to all the other ones.
    
    Now we can build factors by this small algorithm:
    
    ```jsx
    let divisors = [];
    For each exponent choice i of 2: // 0, 1, 2, 3
    	For each exponent choice j of 3: // 0, 1
    		For each exponent choice k of 5: // 0, 1, 2, 3, 4
    			For each exponent choice m of 7: // 0, 1, 2
    				divisos.push(i * j * k * m)
    ```
    
    `@Hint` don’t worry about the i j k m variables they are just there to make it look like pseudocode.
    
    Therefore we use product rule here: $4\cdot 2\cdot 5\cdot 3 = 120$
    

### EX.12

![Screen Shot 2022-05-26 at 5.40.09 PM.png](Week%20of%20@May%2023,%202022%20Combinatorics%20067951cf5db74d35b2f17e7b5e9a4c00/Screen_Shot_2022-05-26_at_5.40.09_PM.png)

`Stategies: Permutation`

- $\text{Answer.}$
    
    Consider the simple case first where the table is linear. Then the normal choosing without replacement applies here so there are $10!$ permutations.
    
    But the table is round. So some arrangements are equivalent.
    
    Think of a knob on a stove. No matter how many steps we turn the knob, the numberings on the knob is the same.
    
    If the knob has $10$ possible positions, then rotating $1, 2, 3,\dots, 10$ steps returns the same arrangement of numbers.
    
    Therefore each arrangement is counted 10 times in the permutation above.
    
    The answer is $10!/10 = 9!$