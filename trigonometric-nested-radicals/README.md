# Trigonometric Nested Radicals

I wondered for a while, why are 30 degree, 45 degree, 60 degree, and 90 degree angles so special.

Why do they have such simple cosines, and why are all the other angles significantly more complicated?

I've been trying to solve this for a while. The results are quite revealing.

Starting off with a few curiosities..

## Nested examples

![cos1_4](cos1_4.png)

![cos1_8](cos1_8.png)

![cos1_16](cos1_16.png)

![cos1_32](cos1_32.png)

You can test, this pattern will continue to be true for future cases.

Indeed, I found increasingly, that a lot of cosines can be expressed as adding or subtracting nested radicals of 2:

![cos3_8](cos3_8.png)

![cos3_16](cos3_16.png)

![cos5_16](cos5_16.png)

![cos7_16](cos7_16.png)

There are too many of these to be a coincidence..

Perhaps one can generate a nested radical solution for all rational cosines?

## Nested Radical Algorithm

Yep, I after many hours studying this thing, I figured out the algorithm to generate a solution for any rational cosine.

If you are interested in a formal proof, my colleague Dr. Thomas Morgan PhD. has written one up that you can review [here](Nested%20Radicals%20Proof.pdf).

Otherwise, below is the algorithm you can use to generate a nested radical for any rational cosine.

### Step 1

List all integers from 0 to the denominator.

Using sin(pi / 8) as an example:

|  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |

On the next row, start with the last number, (in this case 8), and keep subtracting 2.

If you get a negative number, take the absolute value:

|  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
| 8 | 6 | 4 | 2 | 0 | 2 | 4 | 6 | 8 |

Now split this table in half. The left side is positive. The right side is positive.

If there is a zero in the middle, it's plus or minus.

| + | + | + | + | ± | - | - | - | - |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
| 8 | 6 | 4 | 2 | 0 | 2 | 4 | 6 | 8 |

### Step 2

The top number row will be used as a key for this lookup table. The bottom row number will be used as a value to find the next key. The pluses and minuses will be added into the nested radical as we move through the table.

Continuing with sin(pi * 1 / 8) as the example, the numerator in this case is **1**.

So in our table, we start out with **1** in the top row. We highlight the whole column:

| + | **+** | + | + | ± | - | - | - | - |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 0 | ***1*** | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
| 8 | **6** | 4 | 2 | 0 | 2 | 4 | 6 | 8 |

Starting off, we see that we are on the positive side of the table.

So we start with positive root 2:

![+sqrt(2)](p.gif)

Next, we will use the **6** from the bottom row as a key in the next lookup:

| + | + | + | + | ± | - | **-** | - | - |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 0 | 1 | 2 | 3 | 4 | 5 | ***6*** | 7 | 8 |
| 8 | 6 | 4 | 2 | 0 | 2 | **4** | 6 | 8 |

Now, we are on the negative side of the table.

So we update our example:

![+sqrt(2-sqrt(2))](pm.gif)

Next, we will use the **4** from the bottom row as a key in the next lookup:

| + | + | + | + | **±** | - | - | - | - |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 0 | 1 | 2 | 3 | ***4*** | 5 | 6 | 7 | 8 |
| 8 | 6 | 4 | 2 | **0** | 2 | 4 | 6 | 8 |

Doing the same thing:

![+sqrt(2-sqrt(2±sqrt(2)))](pmn.gif)

Next we will use the **0** from the bottom row as a key in the next lookup:

| **+** | + | + | + | ± | - | - | - | - |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| ***0*** | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
| **8** | 6 | 4 | 2 | 0 | 2 | 4 | 6 | 8 |

Which gives:

![+sqrt(2-sqrt(2±sqrt(2+sqrt(2))))](pmnp.gif)

Next we will use the **8** from the bottom row as a key in the next lookup:

| + | + | + | + | ± | - | - | - | **-** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | ***8*** |
| 8 | 6 | 4 | 2 | 0 | 2 | 4 | 6 | **8** |

![+sqrt(2-sqrt(2±sqrt(2+sqrt(2-sqrt(2)))))](pmnpm.gif)

Noted that the 8 will keep looping to the same location indefinitely, meaning the radical will repeat:

![+sqrt(2-sqrt(2±sqrt(2+sqrt(2-sqrt(2-sqrt(2-sqrt(2-sqrt(2-sqrt(2-sqrt(2-...))))))))))](pmnpminf.gif)

Now, if we just divide this answer by two, we will get our solution:

![sin1_8inf](sin1_8inf.gif)

# Step 3

Some common repeating nested radicals reduce into simpler non-repeating radicals.

This is the case in our example:

sqrt(2-sqrt(2-sqrt(2-sqrt(2-sqrt(2-sqrt(2-sqrt(2-...)))))))

equals:

1

Meaning:

±sqrt(2+sqrt(2-sqrt(2-sqrt(2-sqrt(2-sqrt(2-sqrt(2-sqrt(2-...)))))))) = ±sqrt(2+1) = ±sqrt(3)

Also:

sqrt(2+sqrt(2+sqrt(2+sqrt(2+sqrt(2+sqrt(2+sqrt(2+...))))))) = 2
