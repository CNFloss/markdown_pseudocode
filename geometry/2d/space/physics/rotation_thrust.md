# Rotation and Thrust
...and other butt stuff. 

## Table of Contents
 - (Falling Object With Thrust)[#Determining the Path to a Point with Rotation and Thrust]

## Determining the Path to a Point with Rotation and Thrust:

In this function, we calculate the path to a point while considering rotation and thrust. 
The loop continues until the vertical speed is less than or equal to 40 and the horizontal
speed is less than or equal to 20. The clamp function is used to limit the rotation and
thrust within specified bounds.

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


##Determining the Path of a Vector2:

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
