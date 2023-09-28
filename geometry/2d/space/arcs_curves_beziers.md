In this pseudocode:

 - ```start_x``` and ```start_y``` are the x and y coordinates of the starting point.
 - ```end_x``` and ```end_y``` are the x and y coordinates of the ending point.
 - ```arc_height``` is the height of the arc above the midpoint of the start and end points.

The function calculates the parameters of an arc that connects the start and end points 
while passing through the specified arc height. It determines the center of the circle, 
radius, and start and end angles of the arc.

```
Function calculate_arcing_path(start_x, start_y, end_x, end_y, arc_height):
    // Calculate the midpoint between the start and end points
    mid_x = (start_x + end_x) / 2
    mid_y = (start_y + end_y) / 2

    // Calculate the slope of the line between start and end points
    slope = (end_y - start_y) / (end_x - start_x)

    // Calculate the angle of the perpendicular bisector line
    bisector_angle = atan(-1 / slope)

    // Calculate the distance from the start to the midpoint
    distance_to_midpoint = sqrt((mid_x - start_x)^2 + (mid_y - start_y)^2)

    // Calculate the radius of the arc
    radius = (distance_to_midpoint^2 + arc_height^2) / (2 * arc_height)

    // Calculate the center of the circle that defines the arc
    circle_center_x = mid_x - radius * sin(bisector_angle)
    circle_center_y = mid_y + radius * cos(bisector_angle)

    // Calculate the start and end angles of the arc
    start_angle = atan2(start_y - circle_center_y, start_x - circle_center_x)
    end_angle = atan2(end_y - circle_center_y, end_x - circle_center_x)

    Return (circle_center_x, circle_center_y, radius, start_angle, end_angle)

```






