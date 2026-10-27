# Replicable online learning

Two research manuscripts by Jitendra Prajapati, with their original PDF exports and complete LaTeX sources.

Both papers study full-information experts with costs in $[0,1]^n$. Regret is worst-case expected regret on each deterministic input, against one fixed expert, averaging over the learner's entire random tape. Replication requires equality of the **entire expert-index path** on two independent input streams sharing that tape. A product law may vary with time, but is fixed independently of the learner's randomness and inputs.

## Near-square-root regret

[Read the 16-page paper](near-square-root/replicable-experts-near-square-root.pdf) · [LaTeX source](near-square-root/main.tex) · October 22, 2026

For every fixed finite $n$ and fixed $\rho\in(0,1)$, the paper constructs a causal learner with product-law replication failure at most $\rho$ and regret

$$O_{n,\rho}\!\left(\sqrt{T}\log^{7/2}(2T)\right).$$

Theorems 2.1–2.2 give finite bounds. For $n\ge2$, $T\ge2$ and $N=2^{\lceil\log_2n\rceil}$, the bound is $(\log_2N)B(T,\rho/N^2)$. The dependence on $n$ and $\rho$ is poor; this is a fixed-parameter horizon result, not a uniform near-square-root guarantee for growing $n$.

<details>
<summary>Exact parameter dependence from Section 2</summary>

For a base replication parameter $q\in(0,1)$, set

$$K=2\lceil\log_2(T+1)\rceil+2,\quad J=1+\lfloor\log_2(T-1)\rfloor,\quad \gamma=\sqrt{8\ln(2T)},$$
$$\beta=q/4,\quad \lambda=\beta/(1-\beta),\quad r=q/2,\quad \alpha=\lambda/120,\quad \epsilon=\lambda/[80(K+1)],\quad \eta=\sqrt{2T\ln(16T/r)},$$
$$H(T,q)=\max\left\{\epsilon^{-1},\;\gamma\sqrt{(K+1)T},\;\frac{128J\eta}{\alpha\epsilon^2r}\right\},\qquad B(T,q)=10H(T,q)+\frac q8(\sqrt T+1).$$

The tournament uses $q=\rho/N^2$. The paper separately covers $n=1$ and $T=1$.

</details>

This improves the horizon exponent of the bound stated in Theorem 4.1 of [Ahmadi, Bhandari and Blum (2025)](https://proceedings.neurips.cc/paper_files/paper/2025/hash/da8abfd153886b745278b40b5df0be93-Abstract-Conference.html), for fixed $n,\rho$. The manuscript credits Cover's classical fair-future prediction formula. Its released bound has logarithmic power **7/2**. It does not establish strict $O(\sqrt T)$ regret or resolve the literal strict-square-root alternative in that paper's Section 6.

The algorithm knows the horizon. The implementation description uses exact real arithmetic, with a naive $O(nT^3)$ arithmetic bound. No finite-precision, practical-runtime, seedwise-regret, high-probability-regret, or adaptive-input-law guarantee is claimed.

## IID versus time-varying product replication

[Read the 8-page paper](iid-product-separation/replicable-iid-product-separation.pdf) · [LaTeX source](iid-product-separation/main.tex) · October 26, 2026

Theorem 1 gives a product-replicable regret lower bound for $n=2^m$, $T=mL$. At fixed $\rho$, its order is $\Omega_\rho(\min\{T,\sqrt T\,m^{3/2}\})$. Theorem 2 supplies a self-contained IID-replicable upper bound of

$$O\!\left(\min\left\{T,\rho^{-2}\sqrt T\log(2n)[1+\log\log(2T)]^2\right\}\right).$$

For fixed $\rho$, Corollary 3 compares the same regret criterion under the two replication requirements:

- At $T=m^3$, $n=2^m$, product-law replication forces linear regret while IID replication permits sublinear regret.
- At $T=m2^m$, $n=2^m<T$, the ratio of product-replicable to IID-replicable minimax regret diverges.

These are growing-expert-count separations. They do not show a fixed-$n$ impossibility of no-regret learning or determine the optimal general rate. The IID upper bound is included to prove the comparison, without a claim that it is the best IID rate. The discussion distinguishes prior sequential-composition and coin-estimation results from the required causal, entire-path regret statement.

## Sources and validation

The PDFs and five TeX files are unchanged copies of the dated manuscripts. Existing validation consists of internal mathematical checks, source/attribution checks, and successful LaTeX compilation and visual inspection. They are not formally verified or peer-reviewed publications. Independent human correctness review and exhaustive priority have not been established. The collection makes no claim of empirical improvement or external endorsement.

To rebuild either paper with a standard LaTeX installation, run `pdflatex main.tex` twice inside its subdirectory. The near-square-root paper also needs the included `reward.tex`, `replication.tex`, and `tournament.tex`. The bibliographies are embedded in the sources. The included PDFs were not rebuilt for this release. [SHA256SUMS](SHA256SUMS) records the manuscript file hashes.
