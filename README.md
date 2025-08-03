# Numerical_Method_solving_laplace_equations
Compare numerical methods to solve given Laplace equation.

# Problem Given
Our final project problem was given as follows:

**Solving 2D steady state heat equation on uniform Cartesian grid**

Equation:

$$ \nabla^{2} T = 0 \; \text{where} \; T(x,y) $$

Boundary Conditions:

$$ T(0,y) = 150 (K) \; \text{for} \; 0 \leq y \leq 1 $$
$$ T(1,y) = 0 (K) \; \text{for} \; 0 \leq y \leq 1 $$
$$ T(x,1) = 50 (K) \; \text{for} \; 0 \leq x \leq 1 $$
$$ T(x,0) = 100 (K) \; \text{for} \; 0 \leq x \leq 1 $$

**Find the steady state temperature distribution $T(x,y)$ on the plate by using:**

1. Jacobi scheme
2. SOR scheme
3. Gauss-Seidel scheme

Then provide discussion on; (1)**Physical interpretation of $T(x,y)$**, (2) Comparison of the results obtained from 1.-3. above in terms of **computational time**(relative to Jacobi) as well as the trend in the temperature field.


# Background
Our problem is 2D [laplace equation](https://en.wikipedia.org/wiki/Laplace%27s_equation). So that, we can express the problem as follows:

$$ \frac{\partial^{2} \varphi}{\partial x^{2}} + \frac{\partial^{2} \varPhi}{\partial y^{2}} = 0 $$

$$ \text{on} \; 0 \leq x \leq 1, \; 0 \leq y \leq 1 $$

with $\varphi = f(x,y)$ on $\partial D$

Each second derivative can approximate to center differencing approximation:

$$\frac{d^{2} f}{d x^{2}} \approx \frac{f_{i-1} - 2f_{i} + f_{i+1}}{\Delta x^{2}}$$

So, our equation can be written as follows:

$$ \frac{\varphi_{i-1,j} - 2 \varphi_{i,j} + \varphi_{i+1,j}}{\Delta x^{2}} + \frac{\varphi_{i,j-1} - 2 \varphi_{i,j} + \varphi_{i,j+1}}{\Delta y^{2}} = 0 $$

Rewrite this equation with assuming $\frac{\Delta x}{\Delta y} = 1$, then

$$ \varphi_{i+1,j} + \varphi_{i-1,j} + \varphi_{i,j+1} + \varphi_{i,j-1} - 4 \varphi_{i,j} = 0 $$

we can obatin this linear equation. This is the main equation to solve the laplace equation numerically.

# Solving Approach
## Jacobi scheme
Jacobi scheme is that update the next time step from the current step using following formula.

$$ \varphi_{i,j}^{n+1} = \frac{1}{4} \left( \varphi_{i-1,j} + \varphi_{i+1,j} + \varphi_{i,j-1} + \varphi_{i,j+1} \right) $$

Jacobi scheme is the one of the *explicit method*.

The result of Jacobi method is shown in [Fig. 1.](#fig1)

<a id="fig1"></a>
![Jacobi_result](Temp_Jacobi.png)
Fig. 1. Temperature distribution using **Jacobi** scheme

