# Trajectory Generation

The interpolation-curve-based method for trajectory generation involves fitting a smooth curve through a set of via points or waypoints to generate the desired trajectory. This method is commonly used in robotics for path planning and motion control. Here are the key points about this approach:
- It starts with a set of via points or waypoints that define the desired path the robot should follow.

- A smooth curve, typically a polynomial or spline curve, is fitted through these via points to generate a continuous trajectory.


- Common curve types used include cubic polynomials, quintic polynomials, B-splines, and piecewise polynomials.

- The curve fitting process ensures that the trajectory passes through all the via points while satisfying constraints like continuity of velocity, acceleration, or higher derivatives at the via points.

- The fitted curve provides a mathematical representation of the trajectory as a function of time or path parameter.


- This trajectory can then be sampled at discrete time steps to obtain the desired position, velocity, and acceleration profiles for execution on the robot.

- Advantages include the ability to generate smooth trajectories that avoid discontinuities and the flexibility to incorporate constraints like maximum velocity or acceleration limits.


The interpolation-curve approach offers a systematic way to generate trajectories for robotic systems, enabling precise motion control while adhering to the system's kinematic and dynamic constraints
