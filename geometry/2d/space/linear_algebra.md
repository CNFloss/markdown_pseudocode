# Linear Algebra for Programmers

 - [Vector Addition](#vector-addition)
 - [Magnitude or Distance](#magnitude-or-distance)
 - [Linear Interpolation](#linear-interpolation)
 - [Normalize](#normalize)

## Basic Linear Algebra

### Vector Addition 

```
function vectorAddition(vector1, vector2):
    // Create a new vector to store the result
    resultVector = (0, 0)  // Initialize it as the zero vector

    // Add the corresponding components of the two vectors
    resultVector.x = vector1.x + vector2.x
    resultVector.y = vector1.y + vector2.y

    return resultVector
```

### Magnitude or Distance
#### A.K.A Hypotenuse of Triangle A.K.A Pythagorean Theorem

Let ```dx``` be A, and ```dy``` be B and ```distance``` be C. So the end distance C is equal to the square root of A squared plus B squared (A<sup>2</sup>+B<sup>2</sup>=C<sup>2</sup>), ergo pythagorean theorem.

##### Magnitude (Single Point/Vector)

```
magnitude = sqrt(vector.x^2 + vector.y^2)
```

#### Distance (Two Points/Vectors)
```
function distance(x1, y1, x2, y2):
    // Calculate the differences in x and y coordinates
    dx = x2 - x1
    dy = y2 - y1

    // Calculate the square of the differences
    dx_squared = dx * dx
    dy_squared = dy * dy

    // Calculate the sum of the squares
    sum_of_squares = dx_squared + dy_squared

    // Calculate the square root of the sum of squares to get the distance
    distance = square_root(sum_of_squares)

    return distance
```

### Direction

#### Radians

```
angle_rad = atan2(resultVector.y, resultVector.x)
```

### Degrees

```
angle_deg = angle_rad * (180 / π)
````

### Linear Interpolation

In this pseudocode ```A``` and ```B``` are the two endpoints between which you want to interpolate. ```t``` is the interpolation factor, typically ranging from 0 
(corresponding to point ```A```) to 1 (corresponding to point ```B```). Values of t outside this range can be clamped to ensure they stay within [0, 1].```C``` represents 
the interpolated point, and it's calculated by linearly interpolating between points ```A``` and ```B``` based on the value of ```t```.This pseudocode can be used for 
linear interpolation in 2D space, and you can adapt it to work in higher dimensions as well.

```
function linearInterpolation(A, B, t):
    // Ensure t is within the range [0, 1] to interpolate between A and B.
    t = clamp(t, 0, 1)

    // Calculate the interpolated point C.
    C.x = A.x + (B.x - A.x) * t
    C.y = A.y + (B.y - A.y) * t

    return C
```

### Normalize

```
function normalizeVector(vector):
    // Calculate the magnitude (length) of the vector
    magnitude = sqrt(vector.x^2 + vector.y^2)

    // Check for division by zero (if magnitude is zero)
    if magnitude == 0:
        // Handle the special case of a zero vector
        return (0, 0)
    else:
        // Normalize the vector by dividing each component by the magnitude
        normalizedVector.x = vector.x / magnitude
        normalizedVector.y = vector.y / magnitude

        return normalizedVector

```
