# A 63-dimensional counterexample to Borsuk's conjecture

This repository contains a proof PDF and an exact finite verification script for a construction showing that Borsuk's conjecture fails in dimension $63$. Equivalently, if $d_B$ denotes the least dimension in which Borsuk's conjecture fails, then

$$
d_B\le 63.
$$

The previous best published upper bound was $d_B\le64$, due to Jenrich and Brouwer [[JB2014](#JB2014)], building on Bondarenko's $G_2(4)$ construction [[Bon2014](#Bon2014)].

The proof is here:

- [borsuk_63_counterexample.pdf](borsuk_63_counterexample.pdf)

The exact finite verification is here:

- [verify_borsuk63.py](verify_borsuk63.py)
- [GitHub Actions workflow](.github/workflows/verify.yml)

The construction and proof were obtained with assistance from GPT-5.5 Pro.

## Idea

Starting from the $65$-dimensional $G_2(4)$ counterexample, we remove a structured set of $96$ points so that the remaining $320$ points lie in a $63$-dimensional subspace. We then adjoin one projected point while preserving the same clique obstruction: every subset of smaller diameter has size at most $5$.

Thus the final set has $321$ points in $\mathbb R^{63}$, and any partition into smaller-diameter subsets requires at least

$$
\left\lceil \frac{321}{5}\right\rceil=65>64
$$

parts.

Only the input configuration uses the standard two-distance $G_2(4)$ representation. After adjoining the projected point, the final $321$-point set is not two-distance.

## What the verification checks

The script reconstructs the finite $G_2(4)$ model over $\mathbb F_{16}$ and verifies the finite data used in the proof.

It checks:

- the projective model has $273$ points, split into $65$ isotropic and $208$ non-isotropic points;
- the graph has $416$ vertices and is strongly regular with parameters $(416,100,36,20)$;
- the graph has a $5$-clique and no $6$-clique;
- the partition $V=B\sqcup C$ has $|B|=96$ and $|C|=320$;
- the induced graph on $B$ has three connected components $B_1,B_2,B_3$, each of size $32$;
- the degree data used for the codimension-two argument:

$$
\begin{aligned}
&|N(u)\cap B_i|=20 &&(u\in B_i),\\
&|N(u)\cap B_j|=0 &&(u\in B_i,\ i\ne j),\\
&|N(u)\cap C|=80 &&(u\in B),\\
&|N(c)\cap B_i|=8 &&(c\in C,\ i=1,2,3),\\
&|N(c)\cap C|=76 &&(c\in C);
\end{aligned}
$$

- the additional clique checks on $C$ and on $N(b)\cap C$ used as consistency checks for the obstruction.

The script is deterministic and uses exact finite-field arithmetic and integer bitsets. Its checks are implemented with explicit exceptions rather than Python `assert` statements, so they remain active when Python is run with optimization flags such as `-O`.

## Running the verification

Run:

```bash
python verify_borsuk63.py
```

The final line should be:

```text
all exact verification checks passed
```

The same command is run automatically by the GitHub Actions workflow.

## References

<a id="Bon2014"></a>[Bon2014] A. V. Bondarenko, *On Borsuk's conjecture for two-distance sets*, Discrete & Computational Geometry 51 (2014), 509--515. Preprint: https://arxiv.org/abs/1305.2584

<a id="JB2014"></a>[JB2014] T. Jenrich and A. E. Brouwer, *A 64-dimensional counterexample to Borsuk's conjecture*, Electronic Journal of Combinatorics 21(4), P4.29 (2014). PDF: https://www.combinatorics.org/ojs/index.php/eljc/article/view/v21i4p29/pdf

<a id="BroG24"></a>[BroG24] A. E. Brouwer, *The $G_2(4)$ graph*, graph data and construction notes. https://aeb.win.tue.nl/graphs/G24.html
