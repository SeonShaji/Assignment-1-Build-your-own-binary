# IMGD 5010 Assignment 1 Build your own binary : **ORIGAMI 101**

The triangle is the universal language of the GPU. Because it is the simplest shape to calculate, it forms the essential geometry for everything we render, from low-poly sprites to vast, cinematic environments.

I've developed a simple protocol that uses binary numbers from 1-bit to 4-bits that serves as instructions to manipulate a single triangle to create complex shapes through iteration.

## 1 - Creating the initial triangle
```
00 - Isosceles Triangle
01 - Scalene Triangle (long right side)
10 - Scalene Triangle (long left side)
11 - Equilateral Triangle
```

<img src="https://github.com/SeonShaji/Assignment-1-Build-your-own-binary/blob/fe861607b41a38178057b47773aa2a82db4836a7/Types%20of%20triangle.jpg" width="50%">
We're ignoring the exact measure of the lengths of the sides of the triangle, since it only affects the size of the final shape and not the pattern.

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

The above command can be used as follows:
1. To define the top angle of the triangle
2. To rotate the initial triangle (Anti-clockwise direction)
    Note: This operation can only be performed on the initial triangle

The following commands initializes a 60 ° isosceles triangle and rotates it 90 °.

```
00   (Isosceles Triangle)
0100 (Angle 60°)
1000 (Rotation 90°)
```
<img src="https://github.com/SeonShaji/Assignment-1-Build-your-own-binary/blob/223190854e5f62762c0579b3ae57ae4049cc37e7/Images/Rotation.png" width="40%">

## 3 - Manipulating the triangle
```
000 - Flip Up Once
100 - Flip Left Once
010 - Flip Down Once
001 - Flip Right Once

110 - Flip Left and Loop
011 - Flip Right and Loop
111 - Flip Down and Loop
```

The above commands takes the initial triangle(or the last duplicated triangle) creates a copy and flips it along the given side. 

Note: Because triangles can be rotated or flipped, 'left' and 'right' become relative. To reduce the complexity we can choose the side that most closely aligns with a cardinal direction (Up, Down, Left, or Right), ensuring predictable transformations regardless of the triangle's current rotation.

<img src="https://github.com/SeonShaji/Assignment-1-Build-your-own-binary/blob/7e0f1404980ce5f0294d8dc06709647247ad5dec/Images/Flip%20Once%20Example.png" width="40%">

The loop operations repeats the above process until it collides with another triangle. This process could produce an endless cycle based on the setup of the initial triangle.

## 4 - Advanced Combinations
After performing a flip operation you can change the type of the new triangle by using the 2-bit operations. You can also set the measure of the angle opposite to the flipped side using the 4-bit operations.

## Basic Examples
### Square
```
00   (Isosceles Triangle)
1000 (Angle 90°)
0011 (Rotation 45°)
010/001  (Flip Down/Flip Right) 
```
<img src="https://github.com/SeonShaji/Assignment-1-Build-your-own-binary/blob/7e0f1404980ce5f0294d8dc06709647247ad5dec/Images/Square.png" width="80%">

### Circle
```
00   (Isosceles Triangle)
0001 (Angle 15°)
0000 (Rotation 0°)
011  (Flip Right and Loop)
```
<img src="https://github.com/SeonShaji/Assignment-1-Build-your-own-binary/blob/7e0f1404980ce5f0294d8dc06709647247ad5dec/Images/Circles.png" width="40%">

### Trapezoid
```
11   (Equilateral Triangle)
0100 (Angle 60°) (Redundant since equilateral)
0000 (Rotation 0°)
001  (Flip Right)
001  (Flip Right)
```
<img src="https://github.com/SeonShaji/Assignment-1-Build-your-own-binary/blob/7e0f1404980ce5f0294d8dc06709647247ad5dec/Images/trapezoid.png" width="60%">

### Star/Sunburst
```
10   (Scalene larger left)
0100 (Angle 60°)
110  (Flip Left and Loop)
```
<img src="https://github.com/SeonShaji/Assignment-1-Build-your-own-binary/blob/7e0f1404980ce5f0294d8dc06709647247ad5dec/Images/_Stars.png" width="60%">

## Advanced Examples
### Ostrich?
```
00       (Isosceles Triangle)
1000     (Angle 90°)
1011     (Rotation 135°)
001      (Flip Right)
000      (Flip Up)
000      (Flip Left)
000      (Flip Up)
001      (Flip Right)
000      (Flip Up)
11       (Change to Equilateral Triangle)
0100     (Set Angle opposite to flipped side to 60) (Redundant since equilateral)
001      (Flip Right)
10       (Change to Scalene Left Larger)
1000     (Set Angle opposite to flipped side to 90)
000      (Flip Up)
001      (Flip Right)
010      (Flip Down)
```
<img src="https://github.com/SeonShaji/Assignment-1-Build-your-own-binary/blob/7e0f1404980ce5f0294d8dc06709647247ad5dec/Images/Ostrich.png" width="30%">

## Tasks (Easy)

### 1. Rectangle 
Note: Flipping an isosceles right angle triangle produces a kite, not a rectangle

### 2. Cat/Fox
<details>
  <summary>🔍 Hint: Click to see the Image</summary>
  
  <img src="https://github.com/SeonShaji/Assignment-1-Build-your-own-binary/blob/7e0f1404980ce5f0294d8dc06709647247ad5dec/Images/Cat.png" width="40%">

</details>

### 3. Snow Cone
<details>
  <summary>🔍 Hint: Click to see the Image</summary>
  
  <img src="https://github.com/SeonShaji/Assignment-1-Build-your-own-binary/blob/7e0f1404980ce5f0294d8dc06709647247ad5dec/Images/SnowCone.png" width="30%">

</details>

## Tasks (Hard)
1. Dumbbell
<details>
  <summary>🔍 Hint: Click to see the Image</summary>
  
  <img src="https://github.com/SeonShaji/Assignment-1-Build-your-own-binary/blob/7e0f1404980ce5f0294d8dc06709647247ad5dec/Images/Dumbbell.png" width="60%">

</details>
