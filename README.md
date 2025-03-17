Let $G$ be a $d$-regular graph on $n$ vertices. We define a *degree greedy* exploration process on $G$ as follows. At time $t = 0$ all vertices are *active*, and we set $A_{0} = V(G)$. Given $A_{t-1}$ for some $t \geq 1$, we select a vertex $\alpha_{t}$ uniformly at random from the set of vertices with minimum degree in $G[A_{t-1}]$ and set $A_{t} = A_{t-1} \setminus \{\alpha_{t}\}$. In other words, at each step the process randomly selects a vertex of minimum degree from the remaining graph and removes it. We let $I_{t} = V(G) \setminus A_{t}$ be the set of *inactive vertices* at time $t$. The process terminates at time $t = n$, when we have $A_{t} = \varnothing.$

For $i = 0,1,\dots,d$, let $D_{i}(t)$ be the set of vertices of degree $i$ in $G[A_{t}]$. Let $Y_{i}(t) = |D_{i}(t)|$ and $Y(t) = (Y_{0}(t), Y_{1}(t),\dots, Y_{d}(t))$. Thus $Y(0) = (0,0,\dots,n)$. Observe that for all $t$ we have $\sum_{i=0}^{d}Y_{i}(t) = n-t$. We are interested in approximating the quantitiy

$$
  M(t) := \max_{t = 0,\dots,n}\sum_{i=0}^{d-1}Y_{i}(t) = \max_{t = 0,\dots,n}(n - t - Y_{d}(t))
$$

when the underyling graph is $G = G_{n,d}$, the random $d$-regular graph on $n$ vertices. Using a deprioritized version of the algorithm above, Wormald showed that the trajectory of the vector $Y(t)$ in this setting is well-approximated by $ny(t/n) := ny(x)$, where $y(x)$ is the solution to a particular initial value problem $y' = F_{d}(x,y)$, $y(0) = (0,0,\dots,1)$. [[1]](#1). In this notebook, we solve this problem numerically using scipy.integrate. 

Note that to obtain an estimate for $M(t)$, we can simply maximize the function $1 - x - y_{d}(x)$ on $[0,1]$. The critical point solves the equation $y_{d}(x) = -1$, and we include a step in our simulation to estimate this point.

## References
<a id="1">[1]</a> 
Wormald, Nicholas C. (2003). 
Analysis of greedy algorithms on graphs with bounded degrees. 
Discrete Mathematics, 273.1-3, 235-260.
