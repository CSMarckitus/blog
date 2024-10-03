+++
title = 'Insights from an MIT Algebra I Lesson on Math and CS'
date = 2024-10-02T16:24:49+02:00
draft = false
readTime = true
math = true
+++

## People don't understand, rather choose to memorize
I started watching an MIT Linear Algebra lecture to refresh some math concepts I had forgotten. Within minutes, I realized something surprising: I had never truly understood the core foundations of algebra. I’d been doing the steps, memorizing procedures, but not grasping why.

Today, I want to share a simple idea that shifted my perspective completely. It’s not complicated, it’s just about multiplying matrices differently from the rigid, mechanical way we were taught. So, let me show you what blew my mind.

## Do you know how to multiply matrices?
If you've studied higher-level math—at least in Spain—you probably remember matrix multiplication as a series of clunky, rigid steps you had to memorize. It's not something that feels intuitive; instead, it’s often a mechanical process where you repeat the steps and hope you don't make a mistake.

Let's see an example of what I'm talking about.

$$
    \begin{array}{c}
        \begin{bmatrix}
            a_{11} & a_{12} \\\
            a_{12} & a_{22} 
        \end{bmatrix} \\\
        \text{A}
    \end{array}
    \times
    \begin{array}{c}
        \begin{bmatrix}
            b_{11} & b_{12} \\\
            b_{21} & b_{22}
        \end{bmatrix} \\\
        \text{B}
    \end{array}
    =
    \begin{array}{c}
        \begin{bmatrix}
        c_{11} & c_{12} \\\
        c_{21} & c_{22}
        \end{bmatrix} \\\
        \text{C}
    \end{array}
$$

In its simplest form, the only matrix multiplication we’re usually taught is that each **c** in the resulting matrix is calculated following this formula / system:

$$
C_{ij} = \sum_{k=1}^{n} A_{ik} B_{kj}
$$

Or in other words, is the same as:
$$
c11 = a11 \times b11 + a12 \times b21 \\\
c12 = a11 \times b12 + a12 \times b22 \\\
\dots \text{and so on for the other indices}
$$

I’m sure this formula looks familiar — it’s a lot like the formulas we use for solving quadratic equations, where everything feels mechanical and repetitive.

While trying to explain this, I realized that it's surprisingly hard to put into simple words. In computer science, there's a saying: if something is difficult to explain, it's often a sign there's a more intuitive way to approach it (though not always).

**So what's the alternative or the intuitive way to multiply matrices?**
### The importance of knowing where things came (developing intuition)
I've always been curious about where things come from — what motivates the people who create something, and why they needed it in the first place.

I believe that by approaching problems this way, we can keep learning indefinitely. It helps us develop a strong intuition that enables us to solve problems — even those that seem unsolvable at first glance. While this approach takes time, energy, and sometimes causes a headache, it always pays off in the end.

Matrices are a shorthand way of writing systems of equations, but they allow us to do so much more. To illustrate, imagine the following simple equation:


$$
2x - y = 0 \\\
\text{It's the same as:}
\begin{bmatrix}
2 & -1 & 0
\end{bmatrix}
$$

And it's geometric picture it's something like this:
![img](./first-matrix-example.png#small)

So far, so good, right? Now, let’s take it a step further. Using the matrix I introduced earlier, let's add another equation. What we’re doing now is creating a system of equations:
$$
\text{Equation to add}: -x + 2y = 3 \\\
\text{Added equation:}
\begin{bmatrix}
    2 & -1 & 0 \\\
    -1 & 2 & 3
\end{bmatrix}
$$
And the geometric picture of the second equation it's something like this:
![img](./second-matrix-example.png#small)

So now I ask you, what does it mean to find the solution to this system? In other words, do the linear combinations of the two equations cover the entire 2-D space?

The answer is fairly straightforward: solving a system of equations geometrically means finding the point in 2-D space that satisfies both equations (the point where both equations are true). 

In this case, the solution of the system is (1,2) or another way to say it: x=1 and y=2.
![img](./solution-presented-equations.png#small)

Up to this point, everything seems straightforward. We've been finding the solution to the system of equations by treating each equation individually, looking at them row by row. But now, I want to challenge that perspective.

What if, instead of viewing each equation as a separate row, we shift our focus? What happens if we start looking at the columns of the matrix as vectors? In other words, instead of thinking of the matrix purely in terms of individual equations, we can see it as a combination of column vectors — because remember, matrices aren't just for representing equations.

**Now probably you're thinking, how can I do that? Let's see.**

First, take the earlier matrix I presented and treat each column as a vector as I do in the following example:

$$
\text{x}
\begin{bmatrix}
    2 \\\
    -1
\end{bmatrix}
+
\text{y}
\begin{bmatrix}
    -1 \\\
    2
\end{bmatrix}
\text{=}
\begin{bmatrix}
    0 \\\
    3
\end{bmatrix}
$$

As we have a 2 x 3 matrix, I split the matrix into three chunks (vectors) where each of them have 2 dimensions — as there are 2 cols., but we can do that in any
dimension we want.

Now, let's play with the first two vectors. We want to multiply them by some numbers and combine them to see if we can transform them into the last vector. If it's possible, we’ll find a solution to the system; if not, it means the system has no solution — in other words, one equation depends on the other.

Since we already know the solution is (1,2), let's take a closer look at what’s really happening. First, I’ll draw the vector for the x-parameter:
![img](./sum-of-matrix.png#small)

What happens if I multiply the vector for the second parameter ( y ) by 2, because as we saw in the solution it is his solution, and then add it to the first vector? Let’s find out:
![img](./linear-combination.jpg#small)

Well, we see geometrically that the sum of the two vectors, that we represent as x-y params, have a solution in the 2-D space. So
if we use this method to add matrices, why not also use the same concept to multiply matrices?

Imagine we have the following system of equations, where x is a vector that have 2 dimensions (there are 2 items in the column):
$$
Ax=b\\\
\begin{array}{c}
    \begin{bmatrix}
        2 & 5 \\\
        1 & 3 
    \end{bmatrix} \\\
    \text{A}
\end{array}
\begin{array}{c}
    \begin{bmatrix}
        1 \\\
        2
    \end{bmatrix} \\\
    \text{x}
\end{array}
\text{=}
1
\begin{bmatrix}
    2 \\\
    1
\end{bmatrix}
\text{+ 2}
\begin{bmatrix}
    5 \\\
    3
\end{bmatrix}
\text{=}
\begin{array}{c}
    \begin{bmatrix}
        12 \\\
        7
    \end{bmatrix} \\\
    \text{b}
\end{array}
$$

If someone can't see what's happening, here is the development of the steps:
$$
1 \times 2 + 2 \times + 5 = 17 \text{, the x coordinate} \\\
1 \times 1 + 2 \times 3 = 7 \text{, the y coordinate}
$$

🤯 My mind blew up when I saw this, it's sooo simple and it makes sense. 

Now in my mind I can visualize what's happening on each step because I know that all is about vectors and I recognize the importance of dimensions. So although I'm working with equations, I can apply that to anything that can be represented as a matrix.

So now that you see that crazy thing and understanding, why not trying (playing) with more dimensions?
$$
\begin{array}{c}
    \begin{bmatrix}
        2 & 5 \\\
        1 & 3
    \end{bmatrix} \\\
    \text{A}
\end{array}
\begin{array}{c}
    \begin{bmatrix}
        1 & 5 \\\
        2 & 2
    \end{bmatrix} \\\
    \text{x \hspace{0.3cm}y}
\end{array}
\text{=} \\\
\text{1 col. (x param) =}
1
\begin{bmatrix}
    2 \\\
    1
\end{bmatrix}
\text{+ 2}
\begin{bmatrix}
    5 \\\
    3
\end{bmatrix}
\text{=}
\begin{array}{c}
    \begin{bmatrix}
        12 \\\
        7
    \end{bmatrix} \\\
    \text{1 vector}
\end{array} \\\
\text{2 col. (y param) =}
5
\begin{bmatrix}
    2 \\\
    1
\end{bmatrix}
\text{+ 2}
\begin{bmatrix}
    5 \\\
    3
\end{bmatrix}
\text{=}
\begin{array}{c}
    \begin{bmatrix}
        25 \\\
        14
    \end{bmatrix} \\\
    \text{2 vector}
\end{array} \\\
\text{Now the matrix result joined: }
\begin{array}{c}
    \begin{bmatrix}
        12 & 20 \\\
        7 & 11
    \end{bmatrix} \\\
    \text{c}
\end{array} \\\
$$

In conclusion, what we’re really seeing here is the same procedure we started with, but approached differently by changing the order of operations. Remember, playing with numbers and giving them context is crucial to truly understanding what we're doing.
$$
c_{ij} = \sum_{k=1}^{n} b_{kj} \times a_{ik}
$$

Doing that silly thing of see each column as a vector, now we can multiply matrices without making mistakes and without having to memorize anything because in each moment we can visualize in our brains what's happening.

Thanks to read that and I hope you enjoyed it as much as I enjoyed making it.

I also hope this has shed some light on the subject, so you no longer see it as a black box.

For more info: https://www.youtube.com/watch?v=ZK3O402wf1c&t=774s
