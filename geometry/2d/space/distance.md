# A.K.A Hypotenuse of Triangle A.K.A Pythagorean Theorem

Let ```dx``` be a, and ```dy``` be b. So by the end distance is equal to the square root of a squared plus b squared, ergo pythagorean theorem.

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
