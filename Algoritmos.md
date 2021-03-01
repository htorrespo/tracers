# Algorithms and Implementations

A vast amount of computer models are based on ordinary and partial differential equations. This book is an introduction to the various scientific ingredients we need for reliable computing with such type of models. A key theme is to solve differential equations numerically on a computer. Many methods are available for this purpose, but the focus here is on finite difference methods, because these are simple, yet versatile, for solving a wide range of ordinary and partial differential equations. The present chapter first presents the mathematical ideas of finite difference methods and derives algorithms, i.e., formulations of the methods ready for computer programming. Then we create programs and learn how we can be sure that the programs really work correctly.

Throughout industry and science it is common today to study nature or technological devices through models on a computer. With such models the computer acts as a virtual lab where experiments can be done in a fast, reliable, safe, and cheap way. In some fields, e.g., aerospace engineering, the computer models are now so sophisticated that they can replace physical experiments to a large extent.

A vast amount of computer models are based on ordinary and partial differential equations. This book is an introduction to the various scientific ingredients we need for reliable computing with such type of models. A key theme is to solve differential equations numerically on a computer. Many methods are available for this purpose, but the focus here is on finite difference methods, because these are simple, yet versatile, for solving a wide range of ordinary and partial differential equations. The present chapter first presents the mathematical ideas of finite difference methods and derives algorithms, i.e., formulations of the methods ready for computer programming. Then we create programs and learn how we can be sure that the programs really work correctly.


## 1.1 Finite Difference Methods

This section explains the basic ideas of finite difference methods via the simple ordinary differential equation u′=−au

Emphasis is put on the reasoning around discretization principles and introduction of key concepts such as mesh, mesh function, finite difference approximations, averaging in a mesh, derivation of algorithms, and discrete operator notation.

### 1.1.1 A Basic Model for Exponential Decay
Our model problem is perhaps the simplest ordinary differential equation (ODE): 
