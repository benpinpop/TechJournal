# Week 1: Number Systems

## Number Systems | 8/26/25

### Key Journal Questions:

1\. Define Binary

2 Give an example of a binary number

3\. Define Hexadecimal

4\. Give an example of a hexadecimal number.

5\. Define Octal

6\. Give an example of an octal number.

7\. What is a signed number?

8\. Give an example of a signed number.

### [Number Systems — Decimal, Binary, Octal and Hexadecimal](https://medium.com/coderscorner/number-systems-decimal-binary-octal-and-hexadecimal-5e567e55ab28)

<br>

Base/Radix – “number of different digits or combination of digits and letters that a system of counting uses to represent numbers.”

\
<br>

| Bases                    | Numbers                                         |
| ------------------------ | ----------------------------------------------- |
| Decimal (10) \| STANDARD | 10 digits (0-9)                                 |
| Binary (2)               | 2 digits (0-1). Aka a 2 digit number system.    |
| Octal (8)                | 8 digits (0-7)                                  |
| Hexadecimal (16)         | 10 digits, 6 characters (0-9, A, B, C, D, E, F) |

<br>

#### The Decimal Number System (Base 10)

<br>

* When you hit 9, add a digit to the left, and make the right digit zero.
* Continue until all symbols on the right side are complete. When you reach the last symbol, increase the left digit by 1.
* When all symbols on the right and left digits are used up, you add another digit to the left, and make both right digits zero.

#### Calculating a digit’s value

<br>

The base is x, with the digit number being d. If we have a number 1234. The number 4 would be digit 1. To calculate the value of that digit alone, we multiply the digit by xd-1

<br>

Take a number: 2423. The first digit is multiplied by 101-1= 100=1. So 1 \* 3 = 3. The second digit is multiplied 102-1=101 and 2 \* 10 = 20. Hence, we have 23 in the first two digits. This process repeats until the last digit, where we can calculate the final value. In a different base, a number that is 2423 could mean something entirely different. Let’s take a look at binary instead.

<br>

### Binary

Binary contains only two digits, 0 or 1. Binary follows our same rules of adding up symbols:

<br>

When we add 1 to 1, it ends up becoming 10 (in Binary). To calculate 10 in binary to decimal, we look at the first digit, which is 21-0, aka 1 \* 0, so our first digit is 0. Our second digit is 22-1 aka 2 \* 1, which results in a 2. When we add the values of the first and second digit together, we get a value of 2 (in Decimal).&#x20;

<br>

### [Hexadecimal Notation](https://medium.com/coderscorner/hexadecimal-notation-c696eb32328a)

Hexadecimal contains 9 digits and 6 characters. (0-9, A, B, C, D, E, F) So how does that work? Digits are their normal number value, but after 9, values become letters. See the table below.&#x20;

<br>

| Letter | Value |
| ------ | ----- |
| A      | 10    |
| B      | 11    |
| C      | 12    |
| D      | 13    |
| E      | 14    |
| F      | 15    |

<br>

Let’s look at a basic example of a hexadecimal number: 4C. To calculate our first digit, we follow the same formula. We know our base is 16, so our x is 16: 161-0 = 160=1. We then multiply 1 by the letter value. C corresponds to 12 in our table, so our number is 12\*1. Starting to notice a pattern? The first digit is always the value multiplied by one. In the second digit, 161 is our multiplier. 4\*16 = 64 so our number is 64 + 12. 4C is 76 in hexadecimal.&#x20;

<br>

Number systems larger than base 10 with different bases are extremely useful for storing larger numbers.&#x20;

<br>

Note: In many coding languages and graphical displays, hexadecimals are displayed with a prefix of “0x” in front. For example, our number 4C would be 0x4C (or 0x4c; Capitalization doesn’t matter.)

<br>

#### Conversion with number systems other than Binary

#### Hex to Binary

<br>

To start, we separate their digits. Let’s use 13D as an example.

<br>

1      3     D

162\*1 161\*3 160\*13

256 + 48 + 13 (Decimal)

<br>

Instead of calculating to decimal and converting to binary, let’s skip a step:\
\
1 3 D (13) Hex

0001 0011 1101 Binary

<br>

Then we concatenate them together.

Final result: 000100111101

<br>

We need our hexadecimal numbers to convert to 4-digit binary numbers. This is because 4 bits of binary, 1111 in binary, can only hold up to 15 in decimal, meaning that to convert our numbers, we need 4 bits/digits to represent our number. (This heavily confused me at first)

<br>

If we were to reverse the process of converting, we would only need one digit of hexadecimal, as hex is base 16, and holds more numbers/information than binary in a single digit.

### Octal (Base 8)

Octal (which means 8 itself) contains 7 numbers (0-7), with the number 10 meaning 8 in decimal.

<br>

Let’s look at an example of an Octal number: 22. Following our formula, we know our first digit is 2, as it’s always multiplied by 1. Our second digit is 81\*2 so 16 in decimal. This means our number in decimal is 18.&#x20;

### [Signed Numbers](https://medium.com/coderscorner/signed-and-unsigned-numbers-c8cdc54bff87)

<br>

Computer Word - The length of bits a CPU can process at one time.&#x20;

<br>

For example, there are 32 and 64-bit systems. The more bits the computer can read, the more information it can process. (This doesn’t necessarily mean it’s more efficient). In a 32 bit system, there are 232 combinations of bits, which allows computers to hold large amounts of information.&#x20;

<br>

Least Significant Bit - The rightmost bit. If we have 1110, the least significant bit is 0.

Most Significant Bit - The leftmost bit. If we have 1110, the most significant bit is 1.

<br>

A signed number is a number with the most significant bit set to 1. (Not exactly sure what a complement number here is, as there’s no definition.)

<br>

The most significant bit is called the Sign Bit, as it denotes whether it is positive or negative. A sign bit of 1 is negative, a sign bit of 0 is positive. The sign bit is the only number counted as negative, so all the other bits are considered positive.

<br>

Zero extension is the act of adding zeroes onto a bit string to extend it to a certain length.&#x20;

<br>

To convert a number from a bits to b bits, we add the difference between a and b and invert the ones and zeroes, and then add one.

<br>

An example of a signed number would be 1011. Let’s break down the number. We know that the most significant bit is 1, so that means it’s signed, and negative.

\
<br>

| 1        | 0     | 1     | 1     |
| -------- | ----- | ----- | ----- |
| 23 \* -1 | 22\*0 | 21\*1 | 20\*1 |
| -8       | 0     | 2     | 1     |

<br>

Adding -8+2+1=-5, so 1011 is -5 in binary.

<br>
