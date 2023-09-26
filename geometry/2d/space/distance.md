# A.K.A Hypotenuse of Triangle A.K.A Pythagorean Theorem

Let ```dx``` be A, and ```dy``` be B and ```distance``` be C. So by the end distance C is equal to the square root of A squared plus B squared (A<sup>2</sup>+B<sup>2</sup>=C<sup>2</sup>), ergo pythagorean theorem.

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
