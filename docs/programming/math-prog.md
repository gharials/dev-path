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

    As mentioned earlier, most languages floors the division result of two integers. Sometimes, however, you want the ceiling of division results instead. The trick is to add the divisor minus $1$ to the dividend before division. See the following snippet for an illustration in the C language:

    ```C
    int r = (m + d - 1) / d;
    ```

## Modular arithmetic

### The modulo operator

$a \mod m ≡ r$ (pronounced $a$ modulo/mod $m$ equals $r$) means that $r$ is the remainder after dividing $a$ with $m$. Example: $14 \mod 3 ≡ 2$.

In programming languages the `%` operator is used as the modulus operator. Example: `14 % 3`.

## Number formats

### Hexadecimal numbers

Binary representation of numbers are too long and often hard to work with. The 16-based hexadecimal representation is shorter and more convenient for practical uses. There are 16 digits in this format and each digit is equivalent to 4 binary digits or 4 _bits_ (a binary digit is called a bit, named by computer scientist [Claude Shannon](https://en.wikipedia.org/wiki/Claude_Shannon)).

The 16 hexadecimal digits are the following: `0, 1, 2, 3, 4, 5, 6, 7, 8, 9, A, B, C, D, E, F`. Sometimes, small cases (`a, b, c, d, e, f`) are used to represent the last digits. A hexadecimal number is prefixed by a `0x` (or `x` sometimes) to indicate that it is a hexadecimal number.

Examples: `0x12` (the value is 18, not 12) `0xAF`, `0x2A`, `x20`, `xA4`, `xAC`.

???+ info
    **Hexadecimal representation of bytes**
    
    Computers mostly work with _bytes_ (8 bits equal a byte). Two hexadecimal digits form a byte (e.g. `0x7A`).

???+ info
    **Hexadecimal representation of colors**

    Colors in computer are represented with numbers. Each color has its own unique number. See this [resource](https://color-hex.org/) for a list of hexadecimal representation of commonly used colors. This hexadecimal color naming format is widely used in HTML and other applications.
