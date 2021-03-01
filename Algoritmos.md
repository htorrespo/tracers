# Algorithms and Implementations

A vast amount of computer models are based on ordinary and partial differential equations. This book is an introduction to the various scientific ingredients we need for reliable computing with such type of models. A key theme is to solve differential equations numerically on a computer. Many methods are available for this purpose, but the focus here is on finite difference methods, because these are simple, yet versatile, for solving a wide range of ordinary and partial differential equations. The present chapter first presents the mathematical ideas of finite difference methods and derives algorithms, i.e., formulations of the methods ready for computer programming. Then we create programs and learn how we can be sure that the programs really work correctly.

Throughout industry and science it is common today to study nature or technological devices through models on a computer. With such models the computer acts as a virtual lab where experiments can be done in a fast, reliable, safe, and cheap way. In some fields, e.g., aerospace engineering, the computer models are now so sophisticated that they can replace physical experiments to a large extent.

A vast amount of computer models are based on ordinary and partial differential equations. This book is an introduction to the various scientific ingredients we need for reliable computing with such type of models. A key theme is to solve differential equations numerically on a computer. Many methods are available for this purpose, but the focus here is on finite difference methods, because these are simple, yet versatile, for solving a wide range of ordinary and partial differential equations. The present chapter first presents the mathematical ideas of finite difference methods and derives algorithms, i.e., formulations of the methods ready for computer programming. Then we create programs and learn how we can be sure that the programs really work correctly.


## 1.1 Finite Difference Methods

This section explains the basic ideas of finite difference methods via the simple ordinary differential equation u′=−au

Emphasis is put on the reasoning around discretization principles and introduction of key concepts such as mesh, mesh function, finite difference approximations, averaging in a mesh, derivation of algorithms, and discrete operator notation.

### 1.1.1 A Basic Model for Exponential Decay
Our model problem is perhaps the simplest ordinary differential equation (ODE): 


### 1.2.1 Computer Language: Python

Any programming language can be used to generate the un+1
values from the formula above. However, in this document we shall mainly make use of Python. There are several good reasons for this choice:

- Python has a very clean, readable syntax (often known as ‘‘executable pseudo-code’’).

- Python code is very similar to MATLAB code (and MATLAB has a particularly widespread use for scientific computing).

- Python is a full-fledged, very powerful programming language.

- Python is similar to C++, but is much simpler to work with and results in more reliable code.

- Python has a rich set of modules for scientific computing, and its popularity in scientific computing is rapidly growing.

- Python was made for being combined with compiled languages (C, C++, Fortran), so that existing numerical software can be reused, and thereby easing high computational performance with new implementations.

- Python has extensive support for administrative tasks needed when doing large-scale computational investigations.

- Python has extensive support for graphics (visualization, user interfaces, web applications).


The coming programming examples assumes familiarity with variables, for loops, lists, arrays, functions, positional arguments, and keyword (named) arguments.

### 1.2.2 Making a Solver Function

We choose to have an array u for storing the un values, n=0,1,…,Nt. The algorithmic steps are

1. initialize u0
     
2. for t=tn, n=1,2,…,Nt: compute un using the θ-rule formula
     
An implementation of a numerical algorithm is often referred to as a solver. We shall now make a solver for our model problem and realize the solver as a Python function. The function must take the input data I, a, T, Δt, and θ of the problem as arguments and return the solution as arrays u and t for un and tn, n=0,…,Nt. The solver function used as
Open image in new window

```
u, t = solver( I, a, T,  dt, theta)
```

One can now easily plot u versus t to visualize the solution.

The function solver may look as follows in Python:

```python
from numpy import *
def solver(I, a, T, dt, theta):
    """Solve u’=-a*u, u(0)=I, for t in (0,T] with steps of dt."""
    Nt = int(T/dt) # no of time intervals
    T = Nt*dt # adjust T to fit time step dt
    u = zeros(Nt+1) # array of u[n] values
    t = linspace(0, T, Nt+1) # time mesh
    u[0] = I # assign initial condition
    for n in range(0, Nt): # n=0,1,...,Nt-1
        u[n+1] = (1 - (1-theta)*a*dt)/(1 + theta*dt*a)*u[n]
    return u, t
```
