---
title: "Analysis of Nonlinear Dynamic Systems"
collection: open access
type: "Python-based"
permalink: /open access/2023-fall-open access-3
venue: "Nonlinear Dynamic Systems"
date: 2023-11-27
---

This Python code utilizes the sympy library to perform symbolic computations related to a given dynamic system described by two equations.

1. *Symbol Definition*: x, y, a, p, c1, c2 are defined as symbolic variables using sympy.
2. *Dynamic Equations*: Two dynamic equations, F1 and F2, representing a system of nonlinear equations, are defined based on the symbolic variables. These equations capture the dynamics of the system.
3. *Jacobian Matrix*: The code calculates the Jacobian matrix (J) of the system. The Jacobian matrix is a matrix of first-order partial derivatives that describes the linearization of the system around a given point.
4. *Output Jacobian Matrix*: The Jacobian matrix is printed to the console, providing insight into the linearization of the dynamic system at a particular state.
5. *Determinant and Trace*: The code then calculates the determinant and trace of the Jacobian matrix. These quantities provide information about the stability and behavior of the system near equilibrium points.
6. *Output Results*: Finally, the determinant and trace of the Jacobian matrix are printed to the console, with the expressions simplified for better readability.

In summary, the code analyzes the linearization properties of a given nonlinear dynamic system by calculating and examining its Jacobian matrix, determinant, and trace. This information is useful for understanding the stability characteristics of equilibrium points in the system.

```python
import sympy as sp

# Define symbols
x, y, a, p, c1, c2 = sp.symbols('x, y, a, p, c1, c2')

# Define dynamic equations
F1 = x*(1-x)*(a*p*y-c1)
F2 = y*(1-y)*((1-a)*p*x-c2);

# Calculate Jacobian matrix
J = sp.Matrix([[sp.diff(F1, x), sp.diff(F1, y)], [sp.diff(F2, x), sp.diff(F2, y)]])

# Output Jacobian matrix
print("Jacobian Matrix:")
print(J)

# Calculate determinant and trace of Jacobian matrix
det_J = sp.simplify(J.det())
trace_J = sp.simplify(J.trace())

# Output results
print("Determinant of Jacobian Matrix (Simplified):", det_J)
print("Trace of Jacobian Matrix (Simplified):", trace_J)
```
