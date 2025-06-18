# Mathematics for Programming

Mathematics for programming is mainly about integers. There's a dedicated branch of mathematics called _Discrete Mathematics_ for its study. The following basic mathematical ideas are necessary for programmers. Consult an authoritative discrete mathematics book for further details.

## Floor and ceiling functions

### The floor function

The floor of any real number is the greatest integer less than or equal to it. Floor of $x$ is denoted as $⌊x⌋$. Examples: $⌊2.3⌋ = 2$, $⌊8.9⌋ = 8$, $⌊7.0⌋ = 7$.

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

???+ info
    **Getting ceiling of integer division results in programming languages**

    As mentioned earlier, most languages floors the division result of two integers. Sometimes, however, you want the ceiling of division results instead. The trick is to add the divisor minus $1$ to the dividend before division. See the following snippet for an illustration in the C language:

    ```C
    int r = (m + d - 1) / d;
    ```

## Modular arithmetic

### The modulo operator

$a \mod m = r$ (pronounced $a$ modulo/mod $m$ equals $r$) means that $r$ is the remainder after dividing $a$ with $m$. Example: $14 \mod 3 = 2$.

In programming languages the `%` operator is used as the modulus operator. Example: `14 % 3`.

## Number formats

Numbers are represented with _digits_ and _place values_. The most common number system, the _decimal system_, is 10-based, meaning it has 10 digits and its place value increases by a factor of 10. For example, the number $253$ actually equals $2 × 10^2 + 5 × 10^1 + 3 × 10^0 = 200 + 50 + 3$.

There are number formats with a base other than the usual 10-based decimal. A programmer has to be familiar with the following number representations.

### Binary numbers

Binary representation is 2-based, meaning it has only two digits: `0` and `1`. The place value of a binary number increases by a factor of 2. For example, the binary number `1011` actually equals $1 × 2^3 + 0 × 2^2 + 1 × 2^1 + 1 × 2^0 = 8 + 0 + 2 + 1 = 11$ in decimal.

A binary digit is called a _bit_, short for _binary digit_, named by computer scientist [Claude Shannon](https://en.wikipedia.org/wiki/Claude_Shannon). Additionally, 8 bits is called a _byte_ and computers mostly work with bytes.

### Hexadecimal numbers

Binary representation of numbers are too long and often hard to work with. The 16-based hexadecimal representation is shorter and more convenient for practical uses. There are 16 digits in this format: `0, 1, 2, 3, 4, 5, 6, 7, 8, 9, A, B, C, D, E, F`. Sometimes, small cases (`a, b, c, d, e, f`) are used to represent the last digits. A hexadecimal number is prefixed by a `0x` (or `x` sometimes) to indicate that it is a hexadecimal number.

Examples: `0x12` (the value is 18, not 12) `0xAF`, `0x2A`, `x20`, `xA4`, `xAC`.

???+ info
    **Hexadecimal representation of bytes**
    
    Notice that each hexadecimal digit is equivalent to 4 binary digits or 4 _bits_ and two hexadecimal digits form a byte (e.g. `0x7A`).

???+ info
    **Hexadecimal representation of colors**

    Colors in computer are represented with numbers. Each color has its own unique number. See this [resource](https://color-hex.org/) for a list of hexadecimal representation of commonly used colors. This hexadecimal color naming format is widely used in HTML and other applications.

## Counting

Counting (aka _combinatorics_) is a vast topic in mathematics. A programmer needs to know a few commonly used counting techniques.

### Sum rule and product rule

The sum and product rule of counting are particularly important. They occur frequently at work. Here follows a working definition of the two rules:

**Sum rule.** If one and only one option is to be chosen from $n$ options and each option has $a_1, a_2, ... a_n$ alternatives, then the total number of choices is $a_1 + a_2 + ... + a_n$.

**Product rule.** If all of the $n$ options must be chosen and there are $a_1, a_2, ... a_n$ alternatives for each of them, then there are $a_1 × a_2 × ... × a_n$ choices in total. A common special case of the rule is when each option has the same $m$ number of alternatives, then there are total $m × m × ... × m = m^n$ choices.

Consult this [resource](https://brilliant.org/wiki/rule-of-sum-and-rule-of-product-problem-solving/) for details.

## Logarithms

Relationship between power and logarithm: $\log_b n = x$ means $b^x = n$. In other words, _$n$ can be successively divided by $b$ for $x$ times._

For example, $\log_2 8 = 3$ means $2^3 = 8$, or $8$ can be successively divided by $2$ for $3$ times: $8 / 2 = 4$, $4 / 2 = 2$, and $2 / 2 = 1$.

In computer science, $2$-based logarithm is frequent. It is sometimes written as $\lg$ in short (e.g., $\lg n = x$ means $2^x = n$).
