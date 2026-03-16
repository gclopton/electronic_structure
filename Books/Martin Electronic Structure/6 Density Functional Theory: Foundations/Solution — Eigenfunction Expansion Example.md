# Solution — Eigenfunction Expansion on the Unit Disk

##### Problem

Solve $\nabla^2 u(r,\theta) = u(r,\theta) + 3r^2\cos 2\theta$ in the unit disk, given that $u = 0$ on the boundary.

---

##### Setting up in polar coordinates

The Laplacian in polar coordinates is

$$
\nabla^2 u = \frac{\partial^2 u}{\partial r^2} + \frac{1}{r}\frac{\partial u}{\partial r} + \frac{1}{r^2}\frac{\partial^2 u}{\partial \theta^2}
$$

so the PDE is

$$
\frac{\partial^2 u}{\partial r^2} + \frac{1}{r}\frac{\partial u}{\partial r} + \frac{1}{r^2}\frac{\partial^2 u}{\partial \theta^2} = u + 3r^2\cos 2\theta
$$

with the boundary condition $u(1,\theta) = 0$ for all $\theta$, and the regularity requirement that $u$ remain bounded at $r = 0$.

Rearranging to isolate the source:

$$
\frac{\partial^2 u}{\partial r^2} + \frac{1}{r}\frac{\partial u}{\partial r} + \frac{1}{r^2}\frac{\partial^2 u}{\partial \theta^2} - u = 3r^2\cos 2\theta
$$

##### Eigenfunction expansion in the angular variable

The eigenfunctions of $\frac{d^2}{d\theta^2}$ with $2\pi$-periodic boundary conditions are $\{1, \cos n\theta, \sin n\theta\}$ for $n = 1, 2, 3, \ldots$ These form a complete orthogonal set, so any well-behaved function on the disk can be expanded as

$$
u(r,\theta) = \frac{A_0(r)}{2} + \sum_{n=1}^{\infty}\left[A_n(r)\cos n\theta + B_n(r)\sin n\theta\right]
$$

The source term $3r^2\cos 2\theta$ contains only a single angular harmonic: $\cos 2\theta$ (i.e., $n = 2$). Since the PDE is linear, only the $n = 2$ cosine mode is excited. Therefore we seek a solution of the form

$$
u(r,\theta) = R(r)\cos 2\theta
$$

##### Deriving the radial ODE

Substitute $u = R(r)\cos 2\theta$ into the PDE. We need each term of the Laplacian:

$$
\begin{aligned}
\frac{\partial^2 u}{\partial r^2} &= R''(r)\cos 2\theta \\[6pt]
\frac{1}{r}\frac{\partial u}{\partial r} &= \frac{1}{r}R'(r)\cos 2\theta \\[6pt]
\frac{1}{r^2}\frac{\partial^2 u}{\partial \theta^2} &= \frac{1}{r^2}R(r)\frac{d^2}{d\theta^2}(\cos 2\theta) \\
&= \frac{1}{r^2}R(r)(-4\cos 2\theta) \\
&= -\frac{4}{r^2}R(r)\cos 2\theta
\end{aligned}
$$

Substituting into the rearranged PDE and dividing both sides by $\cos 2\theta$:

$$
\begin{aligned}
\left[R'' + \frac{1}{r}R' - \frac{4}{r^2}R\right]\cos 2\theta - R\cos 2\theta &= 3r^2\cos 2\theta \\[6pt]
\left[R'' + \frac{1}{r}R' - \frac{4}{r^2}R - R\right]\cos 2\theta &= 3r^2\cos 2\theta \\[6pt]
R'' + \frac{1}{r}R' - \frac{4}{r^2}R - R &= 3r^2
\end{aligned}
$$

Multiply through by $r^2$ to put this in standard form:

$$
r^2 R'' + r R' - (4 + r^2)R = 3r^4
$$

This is a modified Bessel equation of order $n = 2$ with a polynomial source on the right-hand side.

##### Solving the homogeneous equation

The homogeneous equation is

$$
r^2 R'' + r R' - (4 + r^2)R = 0
$$

This is the modified Bessel equation of order 2. Its two linearly independent solutions are $I_2(r)$ (modified Bessel function of the first kind) and $K_2(r)$ (modified Bessel function of the second kind). Since $K_2(r) \to \infty$ as $r \to 0$, regularity at the origin requires us to discard it. The homogeneous solution bounded at the origin is

$$
R_h(r) = C\, I_2(r)
$$

where $C$ is a constant to be determined by the boundary condition.

##### Finding a particular solution

We seek a particular solution $R_p(r)$ of

$$
R_p'' + \frac{1}{r}R_p' - \frac{4}{r^2}R_p - R_p = 3r^2
$$

Since the source is a polynomial in $r$, try $R_p = ar^2 + br^4$. Compute the necessary derivatives:

$$
\begin{aligned}
R_p &= ar^2 + br^4 \\
R_p' &= 2ar + 4br^3 \\
R_p'' &= 2a + 12br^2
\end{aligned}
$$

Substitute into the left-hand side of the ODE. We evaluate each of the four terms:

$$
\begin{aligned}
R_p'' &= 2a + 12br^2 \\[6pt]
\frac{1}{r}R_p' &= \frac{1}{r}(2ar + 4br^3) \\
&= 2a + 4br^2 \\[6pt]
-\frac{4}{r^2}R_p &= -\frac{4}{r^2}(ar^2 + br^4) \\
&= -4a - 4br^2 \\[6pt]
-R_p &= -ar^2 - br^4
\end{aligned}
$$

Now sum all four contributions, collecting by powers of $r$:

$$
\begin{aligned}
R_p'' + \frac{1}{r}R_p' - \frac{4}{r^2}R_p - R_p
&= (2a + 12br^2) + (2a + 4br^2) + (-4a - 4br^2) + (-ar^2 - br^4) \\
&= \underbrace{(2a + 2a - 4a)}_{r^0} + \underbrace{(12b + 4b - 4b - a)}_{r^2}\,r^2 + \underbrace{(-b)}_{r^4}\,r^4 \\
&= 0 + (12b - a)\,r^2 - b\,r^4
\end{aligned}
$$

Setting this equal to $3r^2$ and matching coefficients of each power of $r$:

$$
\begin{aligned}
r^0 &: \quad 0 = 0 \quad &\checkmark \text{ (automatically satisfied)} \\
r^2 &: \quad 12b - a = 3 \\
r^4 &: \quad -b = 0 \quad &\Longrightarrow \quad b = 0
\end{aligned}
$$

Substituting $b = 0$ into the $r^2$ equation:

$$
\begin{aligned}
12(0) - a &= 3 \\
-a &= 3 \\
a &= -3
\end{aligned}
$$

Therefore the particular solution is

$$
R_p(r) = -3r^2
$$

##### Verification of the particular solution

Substitute $R_p = -3r^2$ back into the ODE to confirm:

$$
\begin{aligned}
R_p'' + \frac{1}{r}R_p' - \frac{4}{r^2}R_p - R_p
&= (-6) + \frac{1}{r}(-6r) - \frac{4}{r^2}(-3r^2) - (-3r^2) \\
&= -6 + (-6) + 12 + 3r^2 \\
&= (-6 - 6 + 12) + 3r^2 \\
&= 0 + 3r^2 \\
&= 3r^2 \quad \checkmark
\end{aligned}
$$

##### General solution and boundary condition

The general solution bounded at the origin is

$$
R(r) = R_h(r) + R_p(r) = C\,I_2(r) - 3r^2
$$

Apply the boundary condition $u(1,\theta) = 0$, which requires $R(1) = 0$:

$$
\begin{aligned}
R(1) &= 0 \\
C\,I_2(1) - 3(1)^2 &= 0 \\
C\,I_2(1) - 3 &= 0 \\
C\,I_2(1) &= 3 \\
C &= \frac{3}{I_2(1)}
\end{aligned}
$$

##### Final solution

Substituting back:

$$
\begin{aligned}
R(r) &= \frac{3}{I_2(1)}\,I_2(r) - 3r^2 \\
&= 3\left[\frac{I_2(r)}{I_2(1)} - r^2\right]
\end{aligned}
$$

Therefore

$$
\boxed{u(r,\theta) = 3\left[\frac{I_2(r)}{I_2(1)} - r^2\right]\cos 2\theta}
$$

##### Verification of boundary conditions

At $r = 1$:

$$
\begin{aligned}
u(1,\theta) &= 3\left[\frac{I_2(1)}{I_2(1)} - 1^2\right]\cos 2\theta \\
&= 3\left[1 - 1\right]\cos 2\theta \\
&= 0 \quad \checkmark
\end{aligned}
$$

At $r = 0$: since $I_2(r) \sim \frac{1}{8}r^2$ as $r \to 0$ (from the series expansion $I_n(r) = \sum_{k=0}^{\infty}\frac{1}{k!\,\Gamma(k+n+1)}\left(\frac{r}{2}\right)^{2k+n}$, the leading term for $n=2$ is $\frac{1}{\Gamma(3)}\left(\frac{r}{2}\right)^2 = \frac{r^2}{8}$), we have

$$
\begin{aligned}
R(r) &\sim 3\left[\frac{r^2/8}{I_2(1)} - r^2\right] \\
&= 3r^2\left[\frac{1}{8\,I_2(1)} - 1\right] \\
&\to 0 \quad \text{as } r \to 0 \quad \checkmark
\end{aligned}
$$

The solution is bounded and continuous at the origin. $\quad\blacksquare$
