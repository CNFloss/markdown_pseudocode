```
Function calculate_acceleration(speed, direction, gravity):
    // Calculate horizontal and vertical components of acceleration
    acceleration_x = 0  // No horizontal acceleration unless acted upon by external forces
    acceleration_y = gravity  // Vertical acceleration due to gravity

    // Convert direction to radians (assuming 0 degrees is to the right, 90 degrees is up)
    radians = degrees_to_radians(direction)

    // Calculate the horizontal and vertical components of acceleration
    // based on the current speed and direction
    acceleration_x += -speed * sin(radians)
    acceleration_y += speed * cos(radians)

    Return (acceleration_x, acceleration_y)
```
