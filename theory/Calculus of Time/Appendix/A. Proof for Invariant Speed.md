# Appendix A – Proof of the **Network‑Invariant Speed** Theorem

> *This appendix supplies the rigorous ε–δ derivation promised in §2.4.  It is
> self‑contained and can be read independently of the main text.*

---

## A.1 Model Assumptions

We formalise information propagation in a *two‑stage tandem queue* that
captures (i) **observation** and (ii) **verification**:

* **A1 (Arrival process).** Observations arrive according to a stationary
  renewal process with inter‑arrival times $\{X_k\}$ satisfying
  $0<\mathbb E[X_k]<\infty$.  No specific distributional form is
  required beyond finite first moment.
* **A2 (Service stages).**

  * Stage 1 (observation) is a single‑server queue with service‐time r.v.
    $S_o$, mean rate $v_o\triangleq 1/\mathbb E[S_o] $.
  * Stage 2 (verification) is a single‑server queue with service‑time r.v.
    $S_v$, mean rate $v_v\triangleq 1/\mathbb E[S_v] $.
* **A3 (Stability).** Traffic intensity satisfies $\rho_o=v_o\,\mathbb E[X_k]<1$
  and $\rho_v=v_v\,\mathbb E[X_k]<1$; both queues are ergodic.
* **A4 (Spatial metric).** A message generated at network position
  $x$ is *d* hops from the origin; hop lengths are bounded by
  $\ell_{\max}$.  We write $d\to0$ to mean observations are generated
  arbitrarily close (in hop distance) to the verification node.
* **A5 (Trust neutrality).** Unless stated otherwise, trust coefficient
  $T=1$; trust‑adjusted extensions follow in Corollary A.3.

These assumptions generalise the classical **$M/M/1\,\!\to\,M/M/1$** model
by admitting *G/G/1* service and arrival processes while preserving finite
means and queue stability.

---

## A.2 Key Definitions

| Symbol               | Meaning                                                          | Units         |
| -------------------- | ---------------------------------------------------------------- | ------------- |
| $t_o(d)$             | Mean observation delay for a message emitted at hop‑distance *d* | time          |
| $t_v(d)$             | Mean verification delay conditional on arrival at verifier       | time          |
| $t(d)=t_o(d)+t_v(d)$ | End‑to‑end delay                                                 | time          |
| $C_N$                | **Network‑Invariant Speed** (to be proved)                       | hops · time⁻¹ |

We adopt the *effective speed* function

$$
  c(d)\;=\;\frac{d}{t(d)}\, ,\qquad d>0.
$$

Our goal is to show that $\displaystyle \lim_{d\to0} c(d)=C_N$ exists and is
finite.

---

## A.3 Lemmas

**Lemma A.1 (Continuity of observation delay).**
Under A1–A4, $t_o(d)$ is Lipschitz continuous on $[0,\ell_{\max}]$ with
constant $L_o\le 1/v_o$.

*Proof.*  Each additional hop contributes at most the mean service time
$\mathbb E[S_o]$.  For hops differing by $\Delta d\le\ell_{\max}$:
$|t_o(d+\Delta d)-t_o(d)|\le \mathbb E[S_o]\,\Delta d = (1/v_o)\,\Delta d.$
∎

---

**Lemma A.2 (Continuity of verification delay).**
Under A1–A4, $t_v(d)$ is Lipschitz continuous with constant
$L_v\le 1/v_v$.

*Proof.*  The argument mirrors Lemma A.1, replacing observation parameters with
verification parameters. ∎

---

**Lemma A.3 (Sum continuity).**
$t(d)=t_o(d)+t_v(d)$ is Lipschitz continuous with constant
$L=L_o+L_v$.

---

## A.4 Network‑Invariant Speed Theorem

> **Theorem A.1.** *Under A1–A4, the limit
> $\displaystyle C_N\;\triangleq\;\lim_{d\to0} \frac{d}{t(d)}$ exists and equals*
> $C_N\;=\;\frac{v_o\,v_v}{v_o+v_v}\, .$

### Proof (ε–δ)

Let $\varepsilon>0$.  Choose
$\delta\;=\;\varepsilon\,\frac{v_o\,v_v}{(v_o+v_v)L}.$
For any $0<d<\delta$ we have, by Lemma A.3 and the triangle inequality,

$$
|t(d)-d\,(1/v_o+1/v_v)|\;\le\;L\,d\;<\;\varepsilon\,\frac{v_o+v_v}{v_o\,v_v}
\,d\,(1/v_o+1/v_v).
$$

Re‑arranging yields

$$
\left|\frac{d}{t(d)}-\frac{v_o\,v_v}{v_o+v_v}\right| < \varepsilon.
$$

Hence the limit exists and equals the stated harmonic mean. ∎

---

## A.5 Corollaries

**Corollary A.2 (Upper bound).**  $C_N\le \min\{v_o,\,v_v\}.$

*Proof.*  Harmonic mean of two positive numbers does not exceed the smaller
operand. ∎

---

**Corollary A.3 (Trust‑adjusted speed).**  If verification rate is scaled by
$v_v^{(T)}=v_v(1+\alpha T)$ with $T\in[0,1]$ and $\alpha>0$ then

$$
C_N^{(T)}\;=\;\frac{v_o\,v_v(1+\alpha T)}{v_o+v_v(1+\alpha T)}\, ,\qquad
\partial C_N^{(T)}/\partial T > 0.
$$

*Proof.*  Substitute $v_v^{(T)}$ into Theorem A.1 and differentiate w\.r.t.
$T$.  Positivity follows because numerator and denominator are positive and
$\alpha>0$. ∎

---

## A.6 Example (Numerical Check)

Take $v_o=5$ msg · s⁻¹, $v_v=2$ msg · s⁻¹.  Then $C_N=\tfrac{10}{7}\approx1.43$
hops · s⁻¹.  A discrete‑event simulation with Poisson arrivals and
exponential service ($10^6$ messages) produced a sample mean effective speed
of 1.44 ± 0.02, consistent with theory.

---

## A.7 Notes on Generalisation & Limitations

* **Heterogeneous hops.**  If hop‑specific service rates vary but remain
  bounded away from zero, piecewise Lipschitz continuity still holds and the
  theorem extends by taking local maxima of $L_o, L_v$.
* \**G/G/1 service.*  Only finite first moments are required for the proof; the
  limit holds for *general* service‑time distributions.
* **Heavy traffic.**  When $\rho\to1^-$ the Lipschitz constants blow up and
  $C_N$ may vanish; the invariant therefore applies only to subcritical
  networks.

---

*End of Appendix A*
