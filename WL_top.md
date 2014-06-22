{"theme":"beige.css"}

## Topological Considerations

of the

## Wang-Landau sampling algorithm

*[Travis Hoppe](http://thoppe.github.io/)*, [(deck source)](https://github.com/thoppe/Telluride-WL-Topology-Talk)

====*

## Motivation

What connection is there between the

##### moveset, energy landscape and selection rules

on the convergence and accuracy of sampling algorithms.
====+
<br>
Can we do better?

====

## Metropolis Sampling

## $ P(a \rightarrow b ) = \min \left( 1, \frac{w(b)}{w(a)} \right ) $

### Boltzmann vs. Wang-Landau

# $ w_\text{B}(a) =  e^{-E_a/kT} \\ w_\text{WL}(a) =  g(E_a)^{-1} $

Each samples a specific distribution.

====*

## WL Modification factors

#### Original formulation
$ H(E) \rightarrow H(E) + 1 $
$ \Omega(E) \rightarrow f \Omega(E)$
Reduce modification factor $f$ when $H$ is "flat".

#### Reduction rate, $1/t$
Use original formulation for initial sampling.
Switch to $f = 1/t$ when smaller than original formulation.

====*

### Wang-Landau advantages:

| Samples the density of states directly.
| From partition function, all thermodynamic equilibrium information is available.
| Avoids energetic barriers.

====*

### Wang-Landau gotchas:

| Non-Markovian until converged.
| Detailed balance correction:

## $ P(E_a \rightarrow E_b ) = \frac{g(E_a)}{g(E_b)} \frac{n_{b\rightarrow a}}{n_{a\rightarrow b}} \frac{n_a}{n_b}$

====

## "Topology" of states?
Let $\phi$ be the set of microstates of the system. 
In order to process _any_ sampling algorithm, one needs

+ An *acceptance function*, $P(a \rightarrow b)$, $a,b \in \phi$.
+ A *microstate weighting function*, $w(a)$, $a\in \phi$.
+ A *moveset function*, $M : \phi \mapsto \phi$.


The moveset defines a directed graph with
vertices $v \in \phi$, and edges $e_{ij} = M(v_i, v_j)$.

====*

### Example: Ising/Potts model

A network of $n, (0,1)$ spin sites that interact via
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
1D periodic chain, cycle graph, $C_n$
!(images/dos_1D.png)<<width:100%>><<transparent>>
====

## Isomorphic reduction
Reduce $2^N$ microstate space,
to _mesostate_ space defined by *spin isomorphs*.

Grouped into isomorphically different arrangements of spins.
====+
e.g. all four (not five!) arrangements of
!(images/star/s3.png)<<width:25%>><<transparent>>

====*
## Star topology, $S_5$
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
!(images/star/final_star_5.png)<<height:200px>><<transparent>>
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
!(images/cycle/final_cycle_5.png)<<height:200px>><<transparent>>
====*
## Cycle topology, $C_6, C_7$
!(images/cycle/final_cycle_6.png)<<width:500px>><<transparent>>
!(images/cycle/final_cycle_7.png)<<width:600px>><<transparent>>

====
## Room for improvement?
Two systems, with similar $\mathcal{H}$ and DOS,
widely different convergence times...

Same moves (single-spin flips), different moveset graphs.

What can we change?

====*
## Measures of accuracy

Minimize "round-trip" time between two extermal states.

Minimize spectrum of converged WL walks.
====
### Spectrum analysis
Once WL is fully converged, it is Markovian with an
eigenvalue spectrum $ \lambda_1 = 1 \ge \lambda_2 \ge \lambda_3 \ge \ldots $
!(images/eig_cycle_6.png)<<width:400px>><<transparent>>
!(images/eig_star_6.png)<<width:400px>><<transparent>>
!(images/eig_ratio_6.png)<<width:400px>><<transparent>>

====*

## Moveset optimization

We can "optimize" a new move, by minimizing $\lambda_2$ and weighting the new move relative to the old ones...

Possible new moves, inversions, $k$-spin flips, bridges, "cheats".

This changes the "edges" in the moveset graph.

Assume that optimized moves will carry over during non-Markovian phase of algorithm.

====*
### Cheater moves, $C_6$
allow all possible isomorphs to connect, $\lambda_2/\lambda^*_2\approx 10^{-4}$
!(images/cheat_cycle_6.png)<<height:600px>><<transparent>>
====*
### Cheater moves, $S_6$
allow all possible isomorphs to connect, $\lambda_2/\lambda^*_2\approx 10^{-5}$
!(images/cheat_star_6.png)<<height:600px>><<transparent>>
====

## Weight optimization

Restrict the moveset, now try to optimize the weights.

Leads to non-flat histograms...





 

