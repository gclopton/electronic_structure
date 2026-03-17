

## Expectation Value of a Local Operator


> [!exercise] Expectation Value of a Local Operator
> Let $x_i \equiv\left(\mathbf{r}_i, \sigma_i\right)$ and $\Psi\left(x_1, \ldots, x_N\right)$. 
> 1.) Write the expectation value of a local operator $\hat{O}=O\left(x_1, \ldots, x_N\right)= \frac{\langle\Psi| \hat{O}|\Psi\rangle}{\langle\Psi \mid \Psi\rangle}$ for an $N$-particle wavefunction in the complete position-spin basis.
> 2.) Write the expression in the case where the many-body coordinate is written compactly as $X=\left(x_1, \ldots, x_N\right)$.
> 3.) Write the expression for the case where $\Psi$ is normalized.


##### Part A

$$\langle\hat{O}\rangle=\frac{\langle\Psi| \hat{O}|\Psi\rangle}{\langle\Psi \mid \Psi\rangle}=\frac{\sum_{\sigma_1, \ldots, \sigma_N} \int d^3 r_1 \cdots d^3 r_N \Psi^*\left(x_1, \ldots, x_N\right) O\left(x_1, \ldots, x_N\right) \Psi\left(x_1, \ldots, x_N\right)}{\sum \int d^3 r_1 \cdots d^3 r_N\left|\Psi\left(x_1, \ldots, x_N\right)\right|^2}$$


##### Part B

$$\langle\hat{O}\rangle=\frac{\sum_{\left\{\sigma_i\right\}} \int d R \Psi^*(X) O(X) \Psi(X)}{\sum_{\left\{\sigma_i\right\}} \int d R|\Psi(X)|^2}, \quad d R \equiv d^3 r_1 \cdots d^3 r_N$$




##### Part C


$$\langle\hat{O}\rangle=\sum_{\sigma_1, \ldots, \sigma_N} \int d^3 r_1 \cdots d^3 r_N \Psi^*\left(x_1, \ldots, x_N\right) O\left(x_1, \ldots, x_N\right) \Psi\left(x_1, \ldots, x_N\right)$$



## State-Dependent Electron Density of the Many-Electron Wavefunction

> [!exercise] State-Dependent Electron Density of the Many-Electron Wavefunction
> Let $x_i \equiv\left(\mathbf{r}_i, \sigma_i\right)$ and $\Psi\left(x_1, \ldots, x_N\right)$. 
> 1.) Write the expression for the state-dependent electron density $n(\mathbf{r})$ of the $N$-electron wavefunction in the complete position-spin basis.
> 2.) Write the expression for the case where $\Psi$ is normalized.
> 3.) Write the expression for the case in which the electron wavefunction is antisymmetric.



> [!definition] State-Dependent Electron Density of the Many-Electron Wavefunction (Eq. 3.8)
>
> $$
> n(\mathbf{r})=\frac{\langle\Psi| \hat{n}(\mathbf{r})|\Psi\rangle}{\langle\Psi \mid \Psi\rangle}
> $$



$$n(\mathbf{r})=\frac{\langle\Psi| \hat{n}(\mathbf{r})|\Psi\rangle}{\langle\Psi \mid \Psi\rangle}$$
$$=\frac{\langle\Psi| \sum_{i=1}^N \delta\left(\mathbf{r}-\hat{\mathbf{r}}_i\right)|\Psi\rangle}{\langle\Psi \mid \Psi\rangle}$$

$$=\frac{\sum_{\sigma_1 \cdots \sigma_N} \int d \mathbf{r}_1 \cdots d \mathbf{r}_N \Psi^*\left(x_1, \ldots, x_N\right)\left(\sum_{i=1}^N \delta\left(\mathbf{r}-\mathbf{r}_i\right)\right) \Psi\left(x_1, \ldots, x_N\right)}{\sum_{\sigma_1 \cdots \sigma_N} \int d \mathbf{r}_1 \cdots d \mathbf{r}_N\left|\Psi\left(x_1, \ldots, x_N\right)\right|^2}$$

$$=\frac{\sum_{\sigma_1, \ldots, \sigma_N} \int d^3 r_1 \cdots d^3 r_N\left|\Psi\left(x_1, \ldots, x_N\right)\right|^2 \sum_{i=1}^N \delta\left(\mathbf{r}-\mathbf{r}_i\right)}{\sum_{\sigma_1, \ldots, \sigma_N} \int d^3 r_1 \cdots d^3 r_N\left|\Psi\left(x_1, \ldots, x_N\right)\right|^2}$$




### Case 1: $\Psi$ is normalized

$$n(\mathbf{r})=\sum_{\sigma_1, \ldots, \sigma_N} \int d^3 r_1 \cdots d^3 r_N\left|\Psi\left(x_1, \ldots, x_N\right)\right|^2 \sum_{i=1}^N \delta\left(\mathbf{r}-\mathbf{r}_i\right)$$



### Case 2: $\Psi$ is antisymmetric 


For an antisymmetric electron wavefunction, all particles are equivalent, so this is often written as

$$
n(\mathbf{r})=N \sum_{\sigma_1, \ldots, \sigma_N} \int d^3 r_2 \cdots d^3 r_N\left|\Psi\left(\mathbf{r} \sigma_1, x_2, \ldots, x_N\right)\right|^2,
$$

where the sum over $\sigma_1$ is included as part of the full spin sum.




