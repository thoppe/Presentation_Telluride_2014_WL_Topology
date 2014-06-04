{"theme":"beige.css"}

## Topological Considerations

of the

## Wang-Landau sampling algorithm

*[Travis Hoppe](http://thoppe.github.io/)*, [(deck source)](https://github.com/thoppe/Telluride-WL-Topology-Talk)

====*

## Motivation

Investigate the roughness / connectivity of the state space in connection with the Wang-Landau algorithms convergence and accuracy.

====

## Prior Work

====

## Wang-Landau

Original form

$1/f$ reduction rate

====

Find system with comparable states, whose topology can be manipulated.

Spin models

+ Ising model
+ Potts model
+ XY-models

====

### System under study

Two-state Potts model, isomorphic to the Ising model

$\mathcal{H} = \sum \sigma_{ij}$

Fix $N=100$, thus $|\Omega|=2^N$.

====

Ising model topology

[SHOW GRID]
[SHOW STAR]
[SHOW CIRCLE]

What about graphs that follow other degree distributions and correlations?

====

Is there a difference?

SHOW RESULTS FOR STAR, CIRCLE

====

## Erdős–Rényi graphs

Studied under percolation theory

MORE INFO + EXAMPLE

====*

## Barabási–Albert graphs

Scale free!

MORE INFO + EXAMPLE

====*

## Star graphs

MORE INFO + EXAMPLE

====*

## Grid graphs

+ Exact solution is known for the density of states [Beale]

MORE INFO + EXAMPLE

====

# Convergence conclusions?

Convergence times are widely distribution, even for the same graph.

Does it correlate to:
+ the number of edges?
+ curvature of the DOS?
+ correlation of the graph?

====

# Accuracy plots

Use $1/f$ mode?
Run at high acceptance rate first.

====
Correlation plots for accuracy...?
====

What to make of this?
Can "jumps" improve runtime?




 
