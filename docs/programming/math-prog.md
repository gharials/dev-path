# Mathematics for Programming

Mathematics for programming is mainly about [integers](#integers). There's a dedicated branch of mathematics called _Discrete Mathematics_ for its study. The following basic mathematical ideas are necessary for programmers. Consult an authoritative discrete mathematics book for further details.

## Integers

In everyday life, we are used to working with mainly two types of numbers: whole numbers (e.g. $0, 1, 2, 3, ...$) and numbers with fractional parts (e.g. $0.5, 1.2, 3.14, ...$).

In mathematics, _whole numbers_ are called _integers_. They can be both positive and negative, including zero. Examples of integers include $-3$, $0$, and $42$. In daily life, we use integers most commonly for counting objects. Integers are very important in programming and computer science. A programmer should be aware of the basic facts about integers.

## Floor and ceiling functions

### The floor function

The floor of any real number is the greatest integer less than or equal to it. Floor of $x$ is denoted as $⌊x⌋$. Examples: $⌊2.3⌋ = 2$, $⌊8.9⌋ = 8$, $⌊7.0⌋ = 7$.

Sometimes we need to find the floor of the division of two integers, like $⌊n / d⌋$. In these cases, the floor is the _quotient of the division_. That means if $n = d × m + r$, then the floor is $m$. For example, $⌊14 / 4⌋ = 3$, because $14 = 4 × 3 + 2$. Dividing two integers this way is known as _integer division_.

???+ info
    **Integer division results in programming languages**

    Dividing two integers often results into a floating point number (e.g. $14 / 4 = 3.5$). In most programming languages (e.g. C, C++, Java) the result of division of two integers is floored. See the following C language snippet, for example:

    ```C
    int d = 14 / 4;
    // value of 'd' is 3 though mathematically it is 3.5
    ```

### The ceiling function

The ceiling of any real number is the smallest integer greater than or equal to it. Ceiling of $x$ is denoted as $⌈x⌉$. Examples: $⌈9.2⌉ = 10$, $⌈7.8⌉ = 8$, $⌈13.0⌉ = 13$.

!!! warning
    **Floor-ceiling functions and rounding off**

    Floor and ceiling functions must not be confused with _rounding off_.

???+ tip
    **Getting ceiling of integer division results in programming languages**

    As mentioned earlier, most languages floors the division result of two integers. Sometimes, however, you want the ceiling of division results instead. The trick is to add the divisor minus $1$ to the dividend before division. See the following snippet for an illustration in the C language:

    ```C
    int r = (m + d - 1) / d;
    ```

## Modular arithmetic

When an integer $n$ is divided by another integer $m$, it can have a remainder $r$. It is expressed in this formula $n = m \times q + r$, where $q$ is the quotient. As we will see, the remainder of the division is important in practice.

### The modulo operator

$a \mod m = r$ (pronounced $a$ modulo/mod $m$ equals $r$) means that $r$ is the remainder after dividing $a$ with $m$. Example: $14 \mod 3 = 2$.

In programming languages the `%` operator is used as the modulus operator. Example: `14 % 3`.

???+ question "Problems"
    1. Divisibility and congruence.
        1. Given an integer $n$, check whether it is divisible by another integer $m$.
        2. Given an integer $m$, what are the possible remainders after any integer is divided by $m$?
    2. Digits.
        1. Given an integer $n$, print all of its digits.
        2. Given an integer $n$, find the integer that is found by reversing the digits of $n$.
    3. Pagination.
        1. Given a number of elements $n$ to be paginated (divided into pages). Each page can contain at most $k$ elements. How many pages are required for $n$ elements? (This formula is also known as [_Pigeonhole principle_](#pigeonhole-principle).)
        2. Given that a page can contain $k$ elements, which page does the $i$-th element belong to?
        3. Given that a page can contain $k$ rows, do the $i$-th and $j$-th elements belong to the same rows in their respective pages?

## Number formats

Numbers are represented with _digits_ and _place values_. The most common number system, the _decimal system_, is $10$-based, meaning it has 10 digits and its place value increases by a factor of $10$. For example, the number $253$ actually equals $2 × 10^2 + 5 × 10^1 + 3 × 10^0 = 200 + 50 + 3$.

There are number formats with a base other than the usual 10-based decimal. A programmer has to be familiar with the following number representations.

### Binary numbers

Binary representation is $2$-based, meaning it has only two digits: $0$ and $1$. The place value of a binary number increases by a factor of $2$. For example, the binary number $1011$ actually equals $1 × 2^3 + 0 × 2^2 + 1 × 2^1 + 1 × 2^0 = 8 + 0 + 2 + 1 = 11$ in decimal.

!!! question "Problem"
    **Find the binary representation of an integer**

    Finding the binary representation of an integer means finding the binary digits of an integer, which is similar to finding all the decimal digits of an integer. In binary, however, the number is successively divided by 2 instead of 10. Try to write a program that finds the binary representation of an integer.

!!! info
    A binary digit is called a _bit_, short for _binary digit_, named by computer scientist [Claude Shannon](https://en.wikipedia.org/wiki/Claude_Shannon). Additionally, 8 bits is called a _byte_ and computers mostly work with bytes.

Notice the following _two special cases_ of binary numbers: the number $2^n$ in binary is a $1$ followed by $n$ number of $0$s, and, the number $2^n - 1$ in binary is $n$ number of $1$s.

| $n$ | $2^n$ in binary | $2^n - 1$ in binary |
|-----|--------------|-------------------|
| $0$ | $1$          | $0$               |
| $1$ | $10$         | $1$               |
| $2$ | $100$        | $11$              |
| $3$ | $1000$       | $111$             |
| $4$ | $10000$      | $1111$            |

### Hexadecimal numbers

Binary representation of numbers are too long and often hard to work with. The 16-based hexadecimal representation is shorter and more convenient for practical uses. There are 16 digits in this format: `0, 1, 2, 3, 4, 5, 6, 7, 8, 9, A, B, C, D, E, F`. Sometimes, small cases (`a, b, c, d, e, f`) are used to represent the last digits. A hexadecimal number is prefixed by a `0x` (or `x` sometimes) to indicate that it is a hexadecimal number.

Examples: `0x12` (the value is 18, not 12) `0xAF`, `0x2A`, `x20`, `xA4`, `xAC`.

???+ example
    **Hexadecimal representation of bytes**
    
    Notice that each hexadecimal digit is equivalent to 4 binary digits or 4 _bits_ and two hexadecimal digits form a byte (e.g. `0x7A`).

    **Hexadecimal representation of colors**

    Colors in computer are represented with numbers. Each color has its own unique number. For example, the color white is represented as `0xFFFFFF`, while black is `0x000000`. See this [resource](https://color-hex.org/) for a list of hexadecimal representation of commonly used colors. This hexadecimal color naming format is widely used in HTML and other applications.

## Counting

Counting (aka _combinatorics_) is a vast topic in mathematics. A programmer needs to know a few commonly used counting techniques.

### Sum rule and product rule

The sum and product rule of counting are particularly important. They occur frequently at work. Here follows a working definition of the two rules:

**Sum rule.** If a task has $n$ options and each option has $a_1, a_2, ... a_n$ choices, then there are $a_1 + a_2 + ... + a_n$ choices in total for completing the task.

For example, there are two options, buses and trains, to travel from city $A$ to $B$. There are $4$ buses and $3$ trains. Therefore, there are $4 + 3 = 7$ choices for traveling from city $A$ to $B$ in total.

**Product rule.** If a task has $n$ steps and there are $a_1, a_2, ... a_n$ choices for each of them, then there are $a_1 × a_2 × ... × a_n$ choices in total for completing the task. A common special case of the rule is when each option has the same $m$ number of alternatives, then there are total $m × m × ... × m = m^n$ choices.

For example, you have to travel from city $A$ to $C$ via city $B$. From city $A$ to $B$, there are $3$ trains, and from city $B$ to $C$, there are $2$ buses. Then, there are $3 × 2 = 6$ choices for traveling from city $A$ to $C$ in total.

???+ question
    1. From city $A$ to $B$ there are $m$ routes and from city $B$ to $C$ there are $n$ routes. How many routes are there from city $A$ to $C$?
    2. A mobile operator has numbers of this format: `0147 xxx xxx`. The first digits are fixed for the operator and the last $6$ digits may vary. How many users can this operator have at most?
    3. How many iterations do the following loop execute?
       ```javascript
       for (let i = 0; i < n; i++) {

           for (let j = 0; j < l; j++) {
           }

           for (let j = 0; j < m; j++) {
           }
       }
       ```

Consult this [resource](https://brilliant.org/wiki/rule-of-sum-and-rule-of-product-problem-solving/) for details.
 
### Pigeonhole principle

We often encounter a common counting problem in practice: given we have containers with capacity $m$ and we have $n$ items to put into them, how many containers do we need at least to put all the items? The well known formula for this problem is this: $\lceil n / m \rceil$. This formula is called the _Pigeonhole principle_. Notice that the formula uses the [ceiling function](#the-ceiling-function).

## Logarithms

Relationship between power and logarithm: $\log_b n = x$ means $b^x = n$. In other words, _$n$ can be successively divided by $b$ for $x$ times._

For example, $\log_2 8 = 3$ means $2^3 = 8$, or $8$ can be successively divided by $2$ for $3$ times: $8 / 2 = 4$, $4 / 2 = 2$, and $2 / 2 = 1$.

In computer science, $2$-based logarithm is frequent. It is sometimes written as $\lg$ in short (e.g., $\lg n = x$ means $2^x = n$).
