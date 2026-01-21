# IMGD 5010 Assignment 1 Build your own binary : **TRIANGLES 101**

The triangle is the universal language of the GPU. Because it is the simplest shape to calculate, it forms the essential geometry for everything we render, from low-poly sprites to vast, cinematic environments.

I've developed a simple protocol that uses binary numbers from 1-bit to 4-bits that serves as instructions to manipulate a single triangle to create complex shapes through iteration.

## 1 - Creating the initial triangle
```
00 - Isosceles Triangle
01 - Scalene Triangle (long right side)
10 - Scalene Triangle (long left side)
11 - Equilateral Triangle
```

<img src="https://github.com/SeonShaji/Assignment-1-Build-your-own-binary/blob/fe861607b41a38178057b47773aa2a82db4836a7/Types%20of%20triangle.jpg" width="40%">
We're ignoring the lengths of the sides of the triangle, since it only affects the size of the final shape.

## 2 - Defining the angle
```
X      X      X      X
90°    60°    30°    15°
```

Each bit represent the corresponding value in degrees.

Examples of commonly used angles:
```
30°  - 0001
45°  - 0011
60°  - 0100
90°  - 1000
120° - 1010
135° - 1011
180° - 1110
```

## 3 - Manipulating the triangle
```
100 - Flip Left Once
010 - Flip Down Once
001 - Flip Right Once

110 - Flip Left and Loop
011 - Flip Right and Loop
111 - Flip Down and Loop
```

The above commands takes the initial triangle(or the last duplicated triangle) creates a copy and flips it along the given direction.

<img src="https://github.com/SeonShaji/Assignment-1-Build-your-own-binary/blob/main/Flip%20Once%20Examples.png" width="40%">
