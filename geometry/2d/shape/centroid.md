Not all pseudo code will be perfect.  The one possible issue with this example is keeping track of the points by incrementing in the ```for``` ... ```in`` ... loop over the 
iterable points datastructure.  But the notation for length of iterables in different language varies so it's a solution that probably upsets everbody but works and is n
correct which is probably the perfect realistic criteria for the best solution given any problem.

```
function findCentroid(points):
    // Initialize variables for the sums of x and y coordinates
    sum_x = 0
    sum_y = 0

    // Initialize a variable for the number of points
    num_points = 0

    // Loop through the ordered points
    for each point in points:
        // Add the x and y coordinates to the sums
        sum_x = sum_x + point.x
        sum_y = sum_y + point.y

        // Increment the number of points
        num_points = num_points + 1

    // Calculate the centroid coordinates
    centroid_x = sum_x / num_points
    centroid_y = sum_y / num_points

    return (centroid_x, centroid_y)

```
