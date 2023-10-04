Based on https://gafferongames.com/post/integration_basics/ , in this JavaScript version, the State class represents 
the object's position and velocity in both X and Y axes. The Derivative class represents the derivatives of these
values with respect to time. The gravity function simulates the effect of gravity, where acceleration increases over time. 
The evaluate function calculates the derivatives at different points in time, and the integrate function updates the 
object's position and velocity based on the calculated derivatives and the time variable.

The example usage at the end demonstrates how the object's motion changes over time due to the simulated gravity. 

```
class State {
    constructor() {
        this.x = 0; // position in X-axis
        this.y = 0; // position in Y-axis
        this.horizontalVelocity = 0; // velocity in X-axis
        this.verticalVelocity = 0; // velocity in Y-axis
        this.horizontalVelocity = 0;
        this.verticalVelocity = 0;
    }
}

function gravity(t) {
    // Simulate gravity, where acceleration increases over time.
    // You can modify this function to create more complex behaviors.
    const gravityConstant = 9.81; // Gravity acceleration constant in m/s^2
    return gravityConstant * t;
}

function applyForces(state, t, dt, forceX, forceY) {
    // Apply your own forces here based on the helicopter's controls or other factors.
    // For example, you can set state.horizontalForce and state.verticalForce based on user input.
    state.horizontalForce = forceX * dt; // Apply your own horizontal force here
    state.verticalForce = forceY * dt; // Apply your own vertical (upward) force here
}

function integrate(state, t, dt) {
    // Calculate new velocity using semi-implicit Euler integration
    const horizontalAcceleration = state.horizontalForce; // Horizontal acceleration (can be negative for deceleration)
    const verticalAcceleration = gravity(t) + state.verticalForce; // Vertical acceleration (gravity + upward force)

    // Update velocity
    state.horizontalVelocity += horizontalAcceleration * dt;
    state.verticalVelocity += verticalAcceleration * dt;

    // Update position using updated velocity
    state.x += state.horizontalVelocity * dt;
    state.y += state.verticalVelocity * dt;
}

// Example usage
const helicopter = new State();
const dt = 0.1; // Time step in seconds
let totalTime = 0; // Total time elapsed

for (let i = 0; i < 100; ++i) {
    applyForces(helicopter, totalTime, dt); // Apply forces (user input or other factors)
    integrate(helicopter, totalTime, dt); // Integrate the motion based on forces
    totalTime += dt;

    console.log(`Time: ${totalTime.toFixed(2)} seconds, Position: (${helicopter.x.toFixed(2)}, ${helicopter.y.toFixed(2)}), Horizontal Velocity: ${helicopter.horizontalVelocity.toFixed(2)} m/s, Vertical Velocity: ${helicopter.verticalVelocity.toFixed(2)} m/s`);
}
```
