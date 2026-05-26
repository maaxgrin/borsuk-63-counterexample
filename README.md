# Borsuk_63_note

This note records the part added to the existing \(G_2(4)\) construction. The \(G_2(4)\) strongly regular graph is the one described by Brouwer [[BroG24](#BroG24)] and used in Bondarenko's \(65\)-dimensional counterexample [[Bon2014](#Bon2014)]. Its Euclidean two-distance representation is the standard representation used in those constructions [[Bon2014](#Bon2014), [BroG24](#BroG24)]. The previous best bound \(C_{28}\le 64\) comes from the Jenrich--Brouwer refinement [[JB2014](#JB2014)].

The new point is to extract a \(320\)-point subset lying in a codimension-\(2\) subspace and add one carefully scaled projected point. This gives \(321\) points in \(\mathbb R^{63}\), while preserving the clique obstruction that forces at least \(65\) smaller-diameter parts.

## Inputs from the literature

We use the \(G_2(4)\) strongly regular graph [[BroG24](#BroG24), [Bon2014](#Bon2014)]

$$
\Gamma\simeq \operatorname{srg}(416,100,36,20),
$$

with its standard Euclidean representation by vectors [[Bon2014](#Bon2014), [BroG24](#BroG24)]

$$
x_v\in\mathbb R^{65}\qquad (v\in V(\Gamma))
$$

satisfying

$$
\langle x_u,x_v\rangle=
\begin{cases}
90, & u=v,\\
18, & u\sim v,\\
-6, & u\not\sim v.
\end{cases}
$$

Equivalently, the Gram matrix is the usual positive-eigenvalue Gram matrix for this strongly regular graph [[Bon2014](#Bon2014), [BroG24](#BroG24)]:

$$
G=96I+24A-6J,
$$

where \(A\) is the adjacency matrix of \(\Gamma\). This is positive semidefinite of rank \(65\), using the eigenvalues of the \(G_2(4)\) graph [[BroG24](#BroG24)].

Thus

$$
\|x_u-x_v\|^2=
\begin{cases}
144, & u\sim v,\\
192, & u\not\sim v.
\end{cases}
$$

We also use the known clique obstruction for this graph, which is the obstruction behind Bondarenko's two-distance counterexample [[Bon2014](#Bon2014)]. The script verifies it again independently:

$$
\omega(\Gamma)=5.
$$

For the Borsuk argument, the essential part is that \(\Gamma\) has no \(6\)-clique.

## New finite verification

Fix an isotropic point \(q_0\) in the projective model of \(G_2(4)\) described by Brouwer [[BroG24](#BroG24)]. Let \(B\) be the set of vertices containing a non-isotropic point orthogonal to \(q_0\), and put

$$
C=V(\Gamma)\setminus B.
$$

The following partition and degree data are the new finite checks in this note. The verification script checks:

$$
|B|=96,\qquad |C|=320,
$$

and the induced subgraph on \(B\) has three connected components

$$
B_1,B_2,B_3
$$

of size \(32\).

The same exact computation gives the following degrees:

$$
\begin{aligned}
&|N(u)\cap B_i|=20 &&(u\in B_i),\\
&|N(u)\cap B_j|=0 &&(u\in B_i,\ i\ne j),\\
&|N(u)\cap C|=80 &&(u\in B),\\
&|N(c)\cap B_i|=8 &&(c\in C,\ i=1,2,3),\\
&|N(c)\cap C|=76 &&(c\in C).
\end{aligned}
$$

These are the additional finite facts used below.

## The \(320\)-point set lies in dimension \(63\)

For \(i=1,2,3\), define, inside the Euclidean representation quoted above [[Bon2014](#Bon2014), [BroG24](#BroG24)],

$$
S_i=\sum_{y\in B_i}x_y.
$$

If \(c\in C\), then \(c\) has \(8\) neighbors and \(24\) non-neighbors in \(B_i\). Therefore

$$
\langle x_c,S_i\rangle
=8\cdot18+24\cdot(-6)
=0.
$$

So every \(x_c\), \(c\in C\), is orthogonal to \(S_1,S_2,S_3\).

The newly verified degrees also give

$$
\langle S_i,S_i\rangle
=32(90+20\cdot18+11\cdot(-6))
=12288,
$$

and, for \(i\ne j\),

$$
\langle S_i,S_j\rangle
=32^2(-6)
=-6144.
$$

Hence the Gram matrix of \(S_1,S_2,S_3\) has diagonal entries \(12288\) and off-diagonal entries \(-6144\), so it has rank \(2\). Since the quoted \(G_2(4)\) representation has rank \(65\) [[Bon2014](#Bon2014), [BroG24](#BroG24)], the orthogonal complement

$$
\langle S_1,S_2,S_3\rangle^\perp
$$

has dimension \(63\), and all \(x_c\), \(c\in C\), lie in it.

## Adding one more point

Choose \(b\in B_1\). The following projected point is the new modification. Set

$$
z_b=x_b-\frac1{32}S_1.
$$

Using the same newly verified degree data,

$$
\langle z_b,S_i\rangle=0\qquad (i=1,2,3),
$$

so \(z_b\) is also in the same \(63\)-dimensional subspace.

Moreover,

$$
\|z_b\|^2
=90-\frac{2}{32}\cdot384+\frac{1}{32^2}\cdot12288
=78.
$$

For \(c\in C\), since \(\langle S_1,x_c\rangle=0\),

$$
\langle z_b,x_c\rangle=\langle x_b,x_c\rangle
=
\begin{cases}
18, & b\sim c,\\
-6, & b\not\sim c.
\end{cases}
$$

Now define

$$
t=\frac{\sqrt{222}-1}{13},
\qquad
p=tz_b.
$$

This value of \(t\) is chosen so that

$$
78t^2+12t=102.
$$

Finally set

$$
X=\{x_c:c\in C\}\cup\{p\}.
$$

Then

$$
X\subset\mathbb R^{63},
\qquad
|X|=321.
$$

## Diameter computation

For \(c,c'\in C\), the distance formula comes from the quoted two-distance representation [[Bon2014](#Bon2014), [BroG24](#BroG24)]:

$$
\|x_c-x_{c'}\|^2=
\begin{cases}
144, & c\sim c',\\
192, & c\not\sim c'.
\end{cases}
$$

For the new point \(p\), using \(\|p\|^2=78t^2\), we get

$$
\|p-x_c\|^2=
\begin{cases}
192-48t, & b\sim c,\\
192, & b\not\sim c.
\end{cases}
$$

Thus

$$
\operatorname{diam}(X)^2=192.
$$

## Smaller-diameter subsets

Let \(Y\subset X\) have diameter strictly smaller than \(\operatorname{diam}(X)\).

If \(p\notin Y\), then the corresponding vertices in \(C\) must be pairwise adjacent, because non-adjacent pairs have squared distance \(192\) by the quoted representation [[Bon2014](#Bon2014), [BroG24](#BroG24)]. Hence they form a clique in \(\Gamma\). Since the no-\(K_6\) obstruction is verified by the script, \(|Y|\le 5\).

If \(p\in Y\), then every other point must be some \(x_c\) with \(b\sim c\). These \(c\)'s must also be pairwise adjacent. Therefore

$$
\{b\}\cup\{c\in C:x_c\in Y\setminus\{p\}\}
$$

is a clique in \(\Gamma\). Using the same no-\(K_6\) obstruction, this clique has size at most \(5\), and therefore \(|Y|\le 5\).

So every smaller-diameter subset of \(X\) has at most \(5\) points.

## Conclusion

Any partition of \(X\) into subsets of strictly smaller diameter needs at least

$$
\left\lceil \frac{321}{5}\right\rceil=65
$$

parts. In dimension \(63\), Borsuk's conjecture would allow only

$$
63+1=64
$$

parts. Since \(65>64\), this improves the previous \(64\)-dimensional counterexample of Jenrich--Brouwer [[JB2014](#JB2014)] by one dimension. Hence

$$
C_{28}\le 63.
$$

## Verification script

The verification script in this repository checks the finite facts used above:

```bash
python verify_borsuk63.py
```

Its verified output includes:

```text
projective points 273
isotropic 65 nonisotropic 208
vertices 416
degrees [100] edges 20800
lambda [36] mu [20]
B size 96 C size 320
B component sizes [32, 32, 32]
B1 internal [20]
B1 to B2 [0]
B1 to B3 [0]
B1 to C [80]
B2 internal [20]
B2 to B1 [0]
B2 to B3 [0]
B2 to C [80]
B3 internal [20]
B3 to B1 [0]
B3 to B2 [0]
B3 to C [80]
C to B1 [8]
C to B2 [8]
C to B3 [8]
C internal [76]
K5 full witness [0, 122, 126, 130, 134]
has K6 full False
has K6 on C False
b 0 NbC size 80 has K5 on NbC False
all exact verification checks passed
```

## References

- <a id="Bon2014"></a>**[Bon2014]** A. V. Bondarenko, *On Borsuk's conjecture for two-distance sets*, Discrete & Computational Geometry 51 (2014), 509--515. Preprint: https://arxiv.org/abs/1305.2584
- <a id="JB2014"></a>**[JB2014]** T. Jenrich and A. E. Brouwer, *A 64-dimensional counterexample to Borsuk's conjecture*, Electronic Journal of Combinatorics 21(4), P4.29 (2014). PDF: https://www.combinatorics.org/ojs/index.php/eljc/article/view/v21i4p29/pdf
- <a id="BroG24"></a>**[BroG24]** A. E. Brouwer, *The \(G_2(4)\) graph*, graph data and construction notes. https://aeb.win.tue.nl/graphs/G24.html
