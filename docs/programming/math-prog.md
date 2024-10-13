# Mathematics For Programming

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

    As mentioned earlier, most languages floors the division result of two integers. Sometimes, however, you want the ceiling of division results instead. The trick is to add the divisor less than $1$ to the dividend before division. See the following snippet for an illustration in the C language:

    ```C
    int r = (m + d - 1) / d;
    ```

## Modular arithmetic

### The modulo operator

$a \mod m ≡ r$ (pronounced $a$ modulo/mod $m$ equals $r$) means that $r$ is the remainder after dividing $a$ with $m$. Example: $14 \mod 3 ≡ 2$.

In programming languages the `%` operator is used as the modulus operator. Example: `14 % 3`.
