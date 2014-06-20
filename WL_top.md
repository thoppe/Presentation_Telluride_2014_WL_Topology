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

## Metropolis Sampling

## $ P(a \rightarrow b ) = \min \left( 1, \frac{w(b)}{w(a)} \right ) $

### Boltzmann vs. Wang-Landau

# $ w_\text{B}(a) =  e^{-E_a/kT} \\ w_\text{WL}(a) =  g(E_a)^{-1} $

Each samples a specific distribution.

====*

## Modification factors

#### Original formulation
$ H(E) \rightarrow H(E) + 1 $
$ \Omega(E) \rightarrow f \Omega(E)$
Reduce modification factor $f$ when $H$ is "flat".

#### Reduction rate, $1/t$
Use original formulation for inital sampling.
Siwtch to $f = 1/t$ when smallar than original formulation.

====*

### Advantages of Wang-Landau

| Samples the density of states directly.
| From partition function, all thermodynamic equilibrium information is avialble.
| Avoids energetic barriers.

====*

### Wang-Landau warnings:

| Non-markovion until converged.
| Detialed balance correction:

## $ P(E_a \rightarrow E_b ) = \frac{g(E_a)}{g(E_b)} \frac{n_{b\rightarrow a}}{n_{a\rightarrow b}} \frac{n_a}{n_b}$

====

## "Topology" of states?
Let $\phi$ be the set of microstates of the system. 
In order to process _any_ sampling algorithm, one needs

+ An *acceptance function*, $P(a \rightarrow b)$, $a,b \in \phi$.
+ A *microstate weighting function*, $w(a)$, $a\in \phi$.
+ A *moveset function*, $M : \phi \mapsto \phi$.

====*
## "Topology" of states?

The *moveset* defines a directed graph,
Vertices $v \in \phi$, and edges $e_{ij} = M(v_i, v_j)$.

====*

### Example: Ising/Potts model

A network of n "$(0,1)$ spin" sites that interact via
#### $\textstyle{\mathcal{H} = J \sum_{ij} \delta_{ij}}$
where the sum is over all adjacent sites (typically a lattice).

#### $\phi = \{0,1\}^n, |\phi| = 2^n$

Single spin "flips" define a moveset.
Other possible moves include double flips,
inversions, Glauber-type...

====

## Ising model "topology"
With fixed $M, \phi, w$, how does WL perform?

!(images/network_1D.png)<<height:220px>>
!(images/network_2D.png)<<height:220px>>
!(images/network_BA.png)<<height:220px>>
!(images/network_star.png)<<height:220px>>


What about graphs that follow other
degree distributions and correlations?

====*
### Is there a difference?
!(images/dos_1D.png)<<height:220px>>
!(images/dos_2D.png)<<height:220px>>
!(images/dos_BA.png)<<height:220px>>
!(images/dos_star.png)<<height:220px>>
<div class="footnote">[1D, 2D, BA, Star]</div>

====*
Star graph, $S_n$
!(images/dos_star.png)<<width:100%>><<transparent>>
====*
1D perodic chain, cycle graph, $C_n$
!(images/dos_1D.png)<<width:100%>><<transparent>>
====

+ Exact solution is known for the density of states [Beale]

MORE INFO + EXAMPLE

====

## Isomorph reduction
Reduce $2^N$ microstate space,
to macrostate space defined by *spin isomorphs*.

Grouped into isomorphically different arrangements of spins.
====+
e.g. all four (not five!) arrangments of
!(images/star/s3.png)<<width:25%>><<transparent>>

====

## Star topology, $S_4$
!(images/star/s0.png)<<width:12%>><<transparent>>
!(images/star/s1.png)<<width:12%>><<transparent>>
!(images/star/s2.png)<<width:12%>><<transparent>>
!(images/star/s3.png)<<width:12%>><<transparent>>
!(images/star/s4.png)<<width:12%>><<transparent>>

!(images/star/s5.png)<<width:12%>><<transparent>>
!(images/star/s6.png)<<width:12%>><<transparent>>
!(images/star/s7.png)<<width:12%>><<transparent>>
!(images/star/s8.png)<<width:12%>><<transparent>>
!(images/star/s9.png)<<width:12%>><<transparent>>
====+
!(images/star/final_star_5.png)<<width:55%>><<transparent>>
====*

## Cycle topology, $C_5$
!(images/cycle/c0.png)<<width:12%>><<transparent>>
!(images/cycle/c1.png)<<width:12%>><<transparent>>
!(images/cycle/c2.png)<<width:12%>><<transparent>>
!(images/cycle/c3.png)<<width:12%>><<transparent>>
!(images/cycle/c4.png)<<width:12%>><<transparent>>

!(images/cycle/c5.png)<<width:12%>><<transparent>>
!(images/cycle/c6.png)<<width:12%>><<transparent>>
!(images/cycle/c7.png)<<width:12%>><<transparent>>
====+
!(images/cycle/final_cycle_5.png)<<height:200px>><<transparent>>
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
Can "jumps" improve run-time?

====

### Optimize states

Need correct modification factor:

## $ P(E_a \rightarrow E_b ) = \frac{g(E_a)}{g(E_b)}  \frac{n_B}{n_A}$

Consider a reduction of the problem into isomorphs

[SHOW STAR, CIRCLE ISOMORPHS]

====

Connectivity for isomorphs:

[SHOW CONNECTIVITY FOR THESE TWO SYSTEMS, N=4]

====

## Metric for optimization

Let $\lambda_2$ be the second largest eigenvalue of the converged WL system, fully converged. We make the anstaz that the convergence is going to be proportional to this value. Certainly, sampling will be faster with a moveset of smaller $\lambda_2$.

[SHOW SPECTRUM FOR STAR, CYCLE]

Typically $\lambda_2 \propto .8$.

====

Consider movesets from one isomorph to the other that are symmetric, ensuring detailed balance. Other movesets may be possible, but these are easy to generate. For example, single spin flips, k spin flips, inversions, etc.

For each of the $k$ isomorphs, this creates a optimization parameter space of $p^{k(k-1)/2}$ where $p=\{0,1\}$. 
Surprisingly, there exist solutions (not necessarily minimal) with $\lambda_2 << 1$.

It can be show that these movesets still visit each energy with equal probability, they just do so much faster!

[SHOW MOVESET MATRIX]
[SHOW MOVESET GRAPH]



 

