Based on https://gafferongames.com/post/integration_basics/ , in this JavaScript version, the State class represents
the object's position and velocity in both X and Y axes. The gravity function simulates the effect of gravity, where
acceleration increases over time, and the integrate function updates the object's position and velocity based on the
calculated derivatives and the time variable.

The example usage at the end demonstrates how the object's motion changes over time due to the simulated gravity.

```
Class State:
    Constructor():
        x = 0 // Position in X-axis
        y = 0 // Position in Y-axis
        HorizontalVelocity = 0 // Velocity in X-axis
        VerticalVelocity = 0 // Velocity in Y-axis

Function Gravity(t):
    GravityConstant = 9.81 // Gravity acceleration constant in m/s^2
    Return GravityConstant * t

Function ApplyForces(state, t, dt):
    state.HorizontalForce = 0 // Apply your own horizontal force here
    state.VerticalForce = 0 // Apply your own vertical (upward) force here

Function Integrate(state, t, dt):
    HorizontalAcceleration = state.HorizontalForce
    VerticalAcceleration = Gravity(t) + state.VerticalForce

    // Update velocity
    state.HorizontalVelocity += HorizontalAcceleration * dt
    state.VerticalVelocity += VerticalAcceleration * dt

    // Update position using updated velocity
    state.x += state.HorizontalVelocity * dt
    state.y += state.VerticalVelocity * dt

// Example usage
Helicopter = New State()
dt = 0.1 // Time step in seconds
TotalTime = 0 // Total time elapsed

For i = 0; i < 100; i++:
    ApplyForces(Helicopter, TotalTime, dt)
    Integrate(Helicopter, TotalTime, dt)
    TotalTime += dt

```

An example demonstrating semi-implicit Euler integration for simulating spacecraft motion in a gravitational field while applying thrust. This approach calculates velocities using the acceleration at the end of the time step, providing a more stable simulation:

```
Class Spacecraft:
    Constructor():
        x = 0 // Position in X-axis
        y = 0 // Position in Y-axis
        VelocityX = 0 // Velocity in X-axis
        VelocityY = 0 // Velocity in Y-axis

Function CalculateGravity(mass):
    GravitationalConstant = 9.81 // Gravitational constant in m/s^2
    Return mass * GravitationalConstant

Function ApplyThrust(spacecraft, ThrustForceX, ThrustForceY, dt):
    Mass = 1000 // Mass of the spacecraft in kg
    GravitationalForce = CalculateGravity(Mass)

    // Calculate acceleration using Newton's second law
    AccelerationX = (ThrustForceX / Mass)
    AccelerationY = (ThrustForceY / Mass) - (GravitationalForce / Mass)

    // Update position using the current velocity
    spacecraft.x += spacecraft.VelocityX * dt
    spacecraft.y += spacecraft.VelocityY * dt

    // Update velocity using the acceleration at the end of the time step
    spacecraft.VelocityX += AccelerationX * dt
    spacecraft.VelocityY += AccelerationY * dt

// Example usage
Spaceship = New Spacecraft()
dt = 0.1 // Time step in seconds
ThrustForceX = 5000
ThrustForceY = 6000
TotalTime = 0 // Total time elapsed

For i = 0; i < 100; i++:
    ApplyThrust(Spaceship, ThrustForceX, ThrustForceY, dt)
    TotalTime += dt

```

In this code, the semi-implicit Euler integration is applied within the `applyThrust` function.
First, the position is updated using the current velocity (explicit Euler), and then the velocity
is updated using the acceleration at the end of the time step (semi-implicit Euler). This approach
results in a more stable simulation compared to explicit Euler integration, especially for systems
with varying forces and accelerations over time.

```
Class Spacecraft:
    Constructor():
        x = 0 // Position in X-axis
        y = 0 // Position in Y-axis
        VelocityX = 0 // Velocity in X-axis
        VelocityY = 0 // Velocity in Y-axis

Function CalculateGravity(mass):
    GravitationalConstant = 9.81 // Gravitational constant in m/s^2
    Return mass * GravitationalConstant

Function ApplyThrust(spacecraft, ThrustForceX, ThrustForceY, dt):
    Mass = 1000 // Mass of the spacecraft in kg
    GravitationalForce = CalculateGravity(Mass)

    // Calculate acceleration using Newton's second law
    AccelerationX = (ThrustForceX / Mass)
    AccelerationY = (ThrustForceY / Mass) - (GravitationalForce / Mass)

    // Update position using the current velocity
    spacecraft.x += spacecraft.VelocityX * dt
    spacecraft.y += spacecraft.VelocityY * dt

    // Update velocity using the acceleration at the end of the time step
    spacecraft.VelocityX += AccelerationX * dt
    spacecraft.VelocityY += AccelerationY * dt

// Example usage
Spaceship = New Spacecraft()
dt = 0.1 // Time step in seconds
ThrustForceX = 5000
ThrustForceY = 6000
TotalTime = 0 // Total time elapsed

For i = 0; i < 100; i++:
    ApplyThrust(Spaceship, ThrustForceX, ThrustForceY, dt)
    TotalTime += dt

```

In this code, the semi-implicit Euler integration is applied within the applyThrust function.
First, the position is updated using the current velocity (explicit Euler), and then the velocity
is updated using the acceleration at the end of the time step (semi-implicit Euler). This approach
results in a more stable simulation compared to explicit Euler integration, especially for systems
with varying forces and accelerations over time.
