```
function generate_waypoints(current_position, current_speed, destination_area):
    waypoints = []  # Initialize an empty list to store waypoints
    current_point = current_position
    target_point = destination_area  # The target destination area

    while distance(current_point, target_point) > SAFE_VERTICAL_SPEED:
        # Calculate the vector from the current point to the target point
        direction_vector = normalize(target_point - current_point)

        # Calculate the desired speed vector based on the safe vertical speed
        desired_speed_vector = direction_vector * SAFE_VERTICAL_SPEED

        # Calculate the next waypoint based on the desired speed vector
        next_waypoint = current_point + desired_speed_vector

        # Add the next waypoint to the list
        waypoints.append(next_waypoint)

        # Update the current point for the next iteration
        current_point = next_waypoint

    # Add the destination area as the final waypoint
    waypoints.append(target_point)

    return waypoints
```
