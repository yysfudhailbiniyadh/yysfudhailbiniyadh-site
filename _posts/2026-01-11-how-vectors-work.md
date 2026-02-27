---
layout: post
title: "I just understood how vectors work"
subtitle: "They are not really \"arrows\" in the graphical sense, rather an 'L'"
author: "Hoshizora Chi"
header-style: text
tags:
    - Misc
---

# Introduction  

I've never been a math guy. I might've written a compiler, LR(1) parser, or a document indexer algorithm before, but never used any real math on them. For me, it was hard to understand what the hell was Derreck Muller saying when I was watching Veritasium, or what on earth was some random Wikipedia article explaining when I was searching for math-based algorithms. So lately, I've been in position where I need to use math again, when the code my lecturer gave for a game development assignment didn't work. I got to debug the code but the code used a simple vector normalization equation. I scratched my head upon seeing that alien formula. Tried to ask ChatGPT but it kept talking about arrows and scaling. Classic ChatGPT. So I decided to dedicate my afternoon to get my head around it. Below is my explanation on what I had found.

# What do vectors do? 

Let's say we have two points in a 2D coordinate space, point A (1, 0) and point B (2, 3). Something like this:
```
3     B
2  
1 
0   A  
# 0 1 2 3
```
We just have to add point A's X and Y value with their difference with the point B's X and Y value. So basically
```
A and B difference: (Xa - Xb, Ya - Yb)
```
Where 
- Xa is X value of A
- Xb is X value of B
- Ya is Y value of A
- Yb is Y value of B

This gives us: `(3-1, 3-0)` which is `(2, 3)`
Remember, this doesn't represent a coordinate; this represents a distance. Basically, we are saying: To get from point A to point B, move the X value by 2, then move the Y value by 2. Here's the illustration:

```
3       B
2       |
1       |
0   A---
# 0 1 2 3
```

That is a vector! Yes, a vector just tells you a "direction". How much you need to move horizontally then vertically from a point to get to another point.

# Unit vectors

Let's ask another question. Let's say in the 2D space, the distance of zero to one, one to two, and so on is 1cm. How do we draw dashed lines by 1cm (similar to the distance unit of the 2D space) from point A to point B? Here's a clue: The vectors can form a triangle.

```
3       B
2     / |
1    /  |
0   A---
# 0 1 2 3
```

To make the line that we want to draw be 1cm, we have to find the length of the line, which is the hypotenuse, and divide it by itself. I'll explain later why we need to divide it instead of subtracting it. So basically the pythagoras theorem: `√x² + y²`, right? Which, if we use it for our case: `√2² + 3²`, which is about 3.6

Now divide 3.6 by 3.6, we got 1. But if we want to scale down the whole triangle, we need to divide the whole side of the triangle too by whatever number we're dividing it with. That's why we're dividing it and not subtracting it. You know, basic algebra. Thus, we get 0.55 for X, 0.83 and for Y. Voila! we just got the unit vector!. Unit vector is basically the vector when the direct line (the hypotenuse) from point A to B is 1. 

For my game assignment, by knowing the unit vector, I can multiply it by the speed variable so, say, a bullet can move to the player.


# Ending words

That's it for now! Thank you for reading!
