# Control Strategies

## PID Control
- PID is a reactive control strategy that calculates the control output based on the error between the desired setpoint and the measured process variable.
- It uses three terms (proportional, integral, and derivative) to adjust the control output based on the current error, accumulated past errors, and the rate of change of the error.
- PID controllers are widely used due to their simplicity, ease of implementation, and robustness for many linear systems.
- However, PID controllers can struggle with complex, nonlinear, or time-varying systems, as they do not explicitly consider the system's dynamics or constraints.
## Model Predictive Control (MPC)
- MPC is a proactive control strategy that uses a mathematical model of the system to predict its future behavior and optimize the control actions accordingly.
- It solves an optimization problem at each time step, considering the current state, setpoint, constraints, and disturbances, to determine the optimal control sequence over a prediction horizon.
- MPC can handle complex, nonlinear, and time-varying systems more effectively than PID controllers, as it explicitly considers the system's dynamics and constraints in the optimization problem.
- MPC is particularly useful for systems with multiple inputs and outputs, constraints, and long time delays or response times.
- However, MPC requires more computational power, system modeling, and tuning effort compared to PID controllers.
