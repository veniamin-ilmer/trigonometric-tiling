# Power Operations

This is an alternative math representation for exponentiation.

## Motivation

Off the top of your head:

*Multipication* is to *Division*, as *Exponentiation* is to *what*?

Children learn addition, subtraction, multiplication, and division in grade school, yet exponentiation and logarithms are left over for precalculus students to fully understand.

Multiplication can be introduced as repeated addition. Exponentiation can be introduced as repeated multiplication.

Yet, exponentiation is considered much more complicated than multiplication.

I feel the reason for this, is a poor representation for exponentiation and logarithms.

It is inconsistent with all the other math operators, and makes it look quite alien to a grade school student.

## Anti-exponentiation

I feel that consistency with the rest of math operators is extremely important.

* Multiplication can be calculated with repeat adding. For example, 7 * 5 or 5 * 7 means you add 7 together 5 times.

* Division is the reverse of multiplication, and it can be done with repeat subtraction. For example, 41 / 7 means you start with 41, and keep subtracting it by 7 until the number becomes less than the subtractor. The answer is how many subtractions you did, plus some remainder.

As a reminder, lets divide 41 by 7 with repeated subtraction:

* 41 - 7 = 34
* 34 - 7 = 27
* 27 - 7 = 20
* 20 - 7 = 13
* 13 - 7 = 6

Since 6 is smaller than 7, we stop subtracting.

In total, we needed to subtract 5 times. Hence, 41 / 7 = about 5.

Moving on, we already know repeat multiplication is exponentiation.

Following the pattern, we'd want the reverse of exponentiation to be repeated division.

So for example, I have the number 100, and want to keep dividing it by, say 3, until the number becomes less than my divisor.

* 100 / 3 = 33.333...
* 33.333... / 3 = 11.111...
* 11.111... / 3 = 3.703...
* 3.703... / 3 = 1.235...

Since 1.235.. is smaller than 3, we stop dividing.

In total, we needed to divide 4 times, so 4 with some remainder is our answer.

In our current math system, how do we represent this calculation?

Well, that would be ln(100) / ln(3)

Why does the reverse of exponentiation require us to use three math operations? Convention.

The shorter variant, log<sub>3</sub>(100), is still unusual compared to all other operations.

3 + 4 is much easier to read than, for example add<sub>4</sub>(3).

Let's redefine the reverse of exponentiation as:

x <sub>v</sub> y = ln(x) / ln(y)

Hence, in our example 100 <sub>v</sub> 3 = about 4

I will call this operation *apower*, short for anti-power.

### *Apower* Identities

Like all basic math operations, *apower* has rules that you can use do solve equations:

* a <sub>v</sub> c + b <sub>v</sub> c = (a * b) <sub>v</sub> c

* a <sub>v</sub> c - b <sub>v</sub> c = (a / b) <sub>v</sub> c

* 1 / a <sub>v</sub> b = b <sub>v</sub> a

* a <sub>v</sub> c / b <sub>v</sub> c = a <sub>v</sub> b

If you'd like to see a list of all identites, [click here](identities.md).

Something that I love about this math operation is that it avoids using `e` by default, and hence can be taught to gradeschool students without involving calculus.

a <sub>v</sub> b feels like a normal math operation, unlike log<sub>b</sub>(a)

## Exponentiation

Although having a single operation for the reverse of exponentiation, is an excellent step towards consistency, there is one more important step we should do.

Exponentiation is unusual because the order matters.

a<sup>b</sup> does not equal b<sup>a</sup>

Now that we have *apower*, let's try and analyze what should be the correct order.

Starting with addition and subtraction. What is the solution to this problem?

a + b - b + b - b

Visually, it is easy to see that the `b`s cancel out, and we just have `a` remaining.

Okay, lets apply the same calculation to multiplication and division..

a * b / b * b / b

Visually, it is easy to see that the `b`s cancel out, and we just have `a` remaining.

What about exponentiation?

If we want to express the same concept with exponents, as we had with addition and multiplication, we are forced into writing this:

ln(b<sup>(ln(b<sup>a</sup>) / ln(b))</sup>) / ln(b)

or:

log<sub>b</sub>(b<sup>(log<sub>b</sub>(b<sup>a</sup>))</sup>)

Not the easiest to read..

Okay, now let's convert it to use the new *apower* operator:

b<sup>(b<sup>a</sup> <sub>v</sub> b)</sup> <sub>v</sub> b

Although it looks a little cleaner, it still is inconsistent with the addition and multiplication examples.

Biggest difference: Notice how `a` is in the middle of the equation, rather than the left side.

The reason why is that the reverse of the equation, reverses the left side of the exponent, rather than the right side, like in addition or multiplication.

So, perhaps the exponent order is wrong?

Let me redefine *power* as this:

a <sup>^</sup> b = b<sup>a</sup>

I have reversed the order in which something is placed to a power.

This means: 2 <sup>^</sup> a = a * a

By doing this switch, we finally get a simple answer that is consistent with the addition and multiplication:

a <sup>^</sup> b <sub>v</sub> b <sup>^</sup> b <sub>v</sub> b = a

I love how consistent this feels as in addition/subtraction and multiplication/division.

It feels great to be be able to do this:

* a <sup>^</sup> b <sub>v</sub> b = a

* a <sub>v</sub> b <sup>^</sup> b = a

### Order of Operations

To be clear:

1 <sup>^</sup> 2 <sup>^</sup> 3 <sub>v</sub> 4 <sup>^</sup> 5 is read as (((1 <sup>^</sup> 2) <sup>^</sup> 3) <sub>v</sub> 4) <sup>^</sup> 5

You just go left to right. Treat <sup>^</sup> and <sub>v</sub> the same.

1 + 2 * 3 <sup>^</sup> 5 * 8 <sub>v</sub> 9 / 4 - 10 is read as 1 + (2 * (3 <sup>^</sup> 5) * (8 <sub>v</sub> 9) / 4) - 10

Order of operations:

1. *power* and *apower*
2. *multiplication* and *division*
3. *addition* and *subtraction*

### *Power* Identities

* a <sup>^</sup> (b * c) = a <sup>^</sup> b * a <sup>^</sup> c

* a <sup>^</sup> (b / c) = a <sup>^</sup> b / a <sup>^</sup> c

* (a + b) <sup>^</sup> 2 = a <sup>^</sup> 2 * b <sup>^</sup> 2

* (a - b) <sup>^</sup> 2 = a <sup>^</sup> 2 / b <sup>^</sup> 2

* a <sup>^</sup> (b <sup>^</sup> c) = (a * b) <sup>^</sup> c

If you'd like to see a list of all identites, [click here](identities.md).

## Algebra with *power* and *apower*

If x <sup>^</sup> y = z then

* x = z <sub>v</sub> y
* y = (1 / x) <sup>^</sup> z

If x <sub>v</sub> y = z then

* x = z <sup>^</sup> y
* y = (1 / z) <sup>^</sup> x

If you'd like to see a list of all identites (including calculus), [click here](identities.md).

## Discussion

The changes proposed here are quite difficult for someone with many years of math experience to accept.

However I feel that this alternative method to understand exponentiation would save newcomers a lot of confusion.

I believe consistency with other math operations is crutial to helping us understand exponentiation better.

It further opens the doors to a better understanding of higher operations after exponentiation: [Tetration](https://en.wikipedia.org/wiki/Tetration)
