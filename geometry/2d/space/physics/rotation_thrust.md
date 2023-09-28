# Rotation and Thrust
...and other butt stuff. 

## Table of Contents
 - [Falling Object With Thrust](#Determining-the-Path-to-a-Point-with-Rotation-and-Thrust)
 - [Path Calculation](#Determining-the-Path-of-a-Vector2)

## Determining the Path to a Point with Rotation and Thrust:

Explanation:

We define a new function called calculate_path_with_constraints that takes several parameters: 
```current_x, current_y, target_x, target_y, gravity, y_constraint, x1,``` and ```x2```. 
These parameters represent the current position, target position, gravitational acceleration,
y-value constraint, and x-range constraint.

We initialize an empty list called path to store the positions of the Vector2 at each time step.

The main part of the algorithm is a while loop that continues until the vertical speed reaches -40 units. 
This loop represents the path calculation over time.

Inside the loop, we calculate the desired rotation and thrust to move towards the target point as before, 
taking into account constraints on rotation and thrust.

We calculate the new horizontal and vertical speeds based on thrust, gravity, and the current speeds, 
similar to the previous pseudocode.

We calculate the new position of the Vector2 based on the updated speeds and the time step, as before.

We apply constraints to ensure that the Vector2 stays within the specified x1 to x2 range and above the y_constraint. 
If the new position violates these constraints, we adjust the position accordingly.

We append the new position to the path list to record the Vector2's path over time.

We update the current position, speeds, and rotation for the next iteration of the loop.

The loop continues until the vertical speed is less than or equal to 40 and the horizontal speed is less than or equal to 20.

Finally, we return the path, which represents the path of the Vector2 while considering both x and y constraints, 
as well as the target point and gravitational effects.

This pseudocode calculates the path of a Vector2 while taking into account constraints on x and y values,
gravitational effects, and the target point.

```
Function calculate_path_with_constraints(current_x, current_y, target_x, target_y, gravity, y_constraint, x1, x2):
    // Initialize variables to store the path
    path = []

    While true:
        // Calculate the vector from the current point to the target point
        delta_x = target_x - current_x
        delta_y = target_y - current_y

        // Calculate the angle to the target point
        target_angle = atan2(delta_y, delta_x)

        // Calculate the desired rotation angle (limited to -90 to 90 degrees)
        rotation = clamp(target_angle - current_rotation, -90, 90)

        // Calculate the thrust (limited to 0 to 4 units)
        thrust = clamp(sqrt(delta_x^2 + delta_y^2) - 20, 0, 4)

        // Calculate the horizontal and vertical components of thrust
        thrust_x = thrust * cos(rotation)
        thrust_y = thrust * sin(rotation)

        // Calculate the new horizontal and vertical speeds
        new_horizontal_speed = current_horizontal_speed + thrust_x
        new_vertical_speed = current_vertical_speed + thrust_y - gravity

        // Calculate the new position based on speeds and time_step
        new_x = current_x + new_horizontal_speed * time_step
        new_y = current_y + new_vertical_speed * time_step

        // Apply constraints to stay within x1 to x2 range and above y_constraint
        If new_x < x1:
            new_x = x1
        ElseIf new_x > x2:
            new_x = x2
        If new_y < y_constraint:
            new_y = y_constraint

        // Append the new position to the path
        Append (new_x, new_y) to path

        // Update the current position, speeds, and rotation for the next iteration
        current_x = new_x
        current_y = new_y
        current_horizontal_speed = new_horizontal_speed
        current_vertical_speed = new_vertical_speed
        current_rotation += rotation

        // Check for termination conditions (vertical speed <= 40 and horizontal speed <= 20)
        If (current_vertical_speed <= 40 and abs(current_horizontal_speed) <= 20):
            Break

    Return path


// Without avoiding a Y value

Function calculate_path_to_point(current_x, current_y, target_x, target_y, gravity):
    // Initialize variables to store the path
    path = []

    While true:
        // Calculate the vector from the current point to the target point
        delta_x = target_x - current_x
        delta_y = target_y - current_y

        // Calculate the angle to the target point
        target_angle = atan2(delta_y, delta_x)

        // Calculate the desired rotation angle (limited to -90 to 90 degrees)
        rotation = clamp(target_angle - current_rotation, -90, 90)

        // Calculate the thrust (limited to 0 to 4 units)
        thrust = clamp(sqrt(delta_x^2 + delta_y^2) - 20, 0, 4)

        // Calculate the horizontal and vertical components of thrust
        thrust_x = thrust * cos(rotation)
        thrust_y = thrust * sin(rotation)

        // Calculate the new horizontal and vertical speeds
        new_horizontal_speed = current_horizontal_speed + thrust_x
        new_vertical_speed = current_vertical_speed + thrust_y - gravity

        // Calculate the new position based on speeds and time_step
        new_x = current_x + new_horizontal_speed * time_step
        new_y = current_y + new_vertical_speed * time_step

        // Append the new position to the path
        Append (new_x, new_y) to path

        // Update the current position, speeds, and rotation for the next iteration
        current_x = new_x
        current_y = new_y
        current_horizontal_speed = new_horizontal_speed
        current_vertical_speed = new_vertical_speed
        current_rotation += rotation

        // Check for termination conditions (vertical speed <= 40 and horizontal speed <= 20)
        If (current_vertical_speed <= 40 and abs(current_horizontal_speed) <= 20):
            Break

    Return path

```


## Determining the Path of a Vector2

```
Function calculate_path_to_point(current_x, current_y, target_x, target_y, gravity):
    // Initialize variables to store the path
    path = []

    While true:
        // Calculate the vector from the current point to the target point
        delta_x = target_x - current_x
        delta_y = target_y - current_y

        // Calculate the angle to the target point
        target_angle = atan2(delta_y, delta_x)

        // Calculate the desired rotation angle (limited to -90 to 90 degrees)
        rotation = clamp(target_angle - current_rotation, -90, 90)

        // Calculate the thrust (limited to 0 to 4 units)
        thrust = clamp(sqrt(delta_x^2 + delta_y^2) - 20, 0, 4)

        // Calculate the horizontal and vertical components of thrust
        thrust_x = thrust * cos(rotation)
        thrust_y = thrust * sin(rotation)

        // Calculate the new horizontal and vertical speeds
        new_horizontal_speed = current_horizontal_speed + thrust_x
        new_vertical_speed = current_vertical_speed + thrust_y - gravity

        // Calculate the new position based on speeds and time_step
        new_x = current_x + new_horizontal_speed * time_step
        new_y = current_y + new_vertical_speed * time_step

        // Append the new position to the path
        Append (new_x, new_y) to path

        // Update the current position, speeds, and rotation for the next iteration
        current_x = new_x
        current_y = new_y
        current_horizontal_speed = new_horizontal_speed
        current_vertical_speed = new_vertical_speed
        current_rotation += rotation

        // Check for termination conditions (vertical speed <= 40 and horizontal speed <= 20)
        If (current_vertical_speed <= 40 and abs(current_horizontal_speed) <= 20):
            Break

    Return path

```
