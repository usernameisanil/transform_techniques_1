# Unit V — Fourier Series and Fourier Transforms

**Course:** 23A54201 — Mathematics IV (Transform Techniques)  
**University:** JNTUA College of Engineering (Autonomous)  

---

## Overview

Unit V covers two major tools in signal analysis and engineering mathematics. **Fourier Series** represents periodic functions as infinite sums of sines and cosines. **Fourier Transforms** extend this idea to non-periodic functions, providing frequency-domain representations used in signal processing, communications, and PDE solutions.

> **Restructured (v2):** Fourier coefficients and Dirichlet conditions combined as the foundational entry point — students need both together before computing any series. Half-range expansions grouped with the arbitrary interval topic. On the transform side: Integral theorem, sine/cosine integrals, and complex form grouped as theory; then transforms and properties as application; finally inverse transforms and convolution as the culmination.

---

## Topic List (in teaching order)

| Topic No. | Topic Name | Prompt File |
|-----------|-----------|-------------|
| 09 | Fourier Coefficients (Euler's) & Dirichlet Conditions | `prompts/unit_v/topic_09_fourier_coefficients_dirichlet.md` |
| 10 | Fourier Series of Even and Odd Functions | `prompts/unit_v/topic_10_fourier_even_odd_functions.md` |
| 11 | Fourier Series in Arbitrary Interval & Half-Range Expansions | `prompts/unit_v/topic_11_fourier_arbitrary_halfrange.md` |
| 12 | Fourier Integral Theorem & Sine/Cosine Integrals | `prompts/unit_v/topic_12_fourier_integral_sine_cosine.md` |
| 13 | Complex Fourier Integral & Fourier Transform | `prompts/unit_v/topic_13_complex_fourier_integral_transform.md` |
| 14 | Fourier Sine and Cosine Transforms | `prompts/unit_v/topic_14_fourier_sine_cosine_transforms.md` |
| 15 | Properties of Fourier Transforms | `prompts/unit_v/topic_15_fourier_transform_properties.md` |
| 16 | Inverse Fourier Transforms & Convolution Theorem | `prompts/unit_v/topic_16_inverse_fourier_convolution.md` |

> **Note on numbering:** Unit IV topics are numbered 01–08; Unit V topics continue as 09–16 for a unified 16-topic course structure.

---

## Topic Descriptions

### Topic 09 — Fourier Coefficients (Euler's) & Dirichlet Conditions

Establishes the complete framework for computing Fourier series. Covers:
- **Trigonometric series:** f(x) = a₀/2 + Σ[aₙcos(nx) + bₙsin(nx)]
- **Euler's formulas** for Fourier coefficients:
  - a₀ = (1/π) ∫₋π^π f(x) dx
  - aₙ = (1/π) ∫₋π^π f(x) cos(nx) dx
  - bₙ = (1/π) ∫₋π^π f(x) sin(nx) dx
- **Dirichlet conditions** — sufficient conditions for Fourier series convergence:
  1. f(x) is periodic
  2. f(x) is piecewise continuous on one period
  3. f(x) has a finite number of maxima, minima, and discontinuities
- Convergence at points of continuity and at jump discontinuities (converges to average)
- Worked examples: expanding simple piecewise functions in (−π, π)

**Why combined:** Dirichlet conditions are the validity check for Euler's formulas — students must understand when the process applies before computing coefficients.

---

### Topic 10 — Fourier Series of Even and Odd Functions

Exploits function symmetry to simplify Fourier coefficient computation. Covers:
- **Even function:** f(−x) = f(x) ⟹ all bₙ = 0 (pure cosine series)
- **Odd function:** f(−x) = −f(x) ⟹ a₀ = 0 and all aₙ = 0 (pure sine series)
- Simplified formulas using symmetry:
  - Even: a₀ = (2/π)∫₀^π f(x) dx; aₙ = (2/π)∫₀^π f(x)cos(nx) dx
  - Odd: bₙ = (2/π)∫₀^π f(x)sin(nx) dx
- Testing a function for even/odd symmetry
- Worked examples: |x|, x², x, x³ type functions
- Parseval's theorem as a useful verification tool

---

### Topic 11 — Fourier Series in Arbitrary Interval & Half-Range Expansions

Extends Fourier series beyond (−π, π) to general intervals. Covers:
- **Fourier series on (−L, L):**
  - aₙ = (1/L) ∫₋L^L f(x) cos(nπx/L) dx
  - bₙ = (1/L) ∫₋L^L f(x) sin(nπx/L) dx
- **Half-range expansions on (0, L):**
  - **Cosine series** (even extension): only cosine terms
  - **Sine series** (odd extension): only sine terms
- Choosing between sine and cosine half-range expansions based on boundary conditions
- Applications to heat equation boundary conditions
- Worked examples with non-π intervals (e.g., (0, 2), (−1, 1))

**Why combined:** Half-range expansions are a direct application of the arbitrary interval formulas applied to one-sided intervals — natural to teach together.

---

### Topic 12 — Fourier Integral Theorem & Sine/Cosine Integrals

Bridges Fourier series (periodic) to Fourier transforms (non-periodic). Covers:
- **Motivation:** What happens to Fourier series as period T → ∞?
- **Fourier Integral Theorem (without proof):**
  f(x) = (1/π) ∫₀^∞ [∫₋∞^∞ f(t) cos λ(t−x) dt] dλ
- **Fourier sine integral:** for odd (or one-sided) functions
  f(x) = (2/π) ∫₀^∞ sin(λx) [∫₀^∞ f(t) sin(λt) dt] dλ
- **Fourier cosine integral:** for even (or one-sided) functions
  f(x) = (2/π) ∫₀^∞ cos(λx) [∫₀^∞ f(t) cos(λt) dt] dλ
- Conditions for validity (similar to Dirichlet)
- Worked examples evaluating Fourier integrals for standard functions

---

### Topic 13 — Complex Fourier Integral & Fourier Transform

Introduces the compact complex notation and the formal definition of the Fourier Transform. Covers:
- **Complex form of Fourier integral:**
  f(x) = (1/2π) ∫₋∞^∞ [∫₋∞^∞ f(t) e^(iλ(x−t)) dt] dλ
- **Fourier Transform definition:**
  F(λ) = F{f(x)} = ∫₋∞^∞ f(x) e^(−iλx) dx
- **Inverse Fourier Transform:**
  f(x) = (1/2π) ∫₋∞^∞ F(λ) e^(iλx) dλ
- Physical interpretation: F(λ) gives the **frequency spectrum** of f(x)
- Transforms of standard functions: rectangular pulse, Gaussian, exponential decay
- Relationship between Fourier Transform and Laplace Transform

**Why combined:** The complex Fourier integral is the natural derivation path leading directly to the Fourier Transform definition — splitting creates an abrupt gap.

---

### Topic 14 — Fourier Sine and Cosine Transforms

Real-valued alternatives to the complex Fourier Transform, useful for functions defined on (0, ∞). Covers:
- **Fourier Sine Transform:**
  Fₛ(λ) = Fₛ{f(x)} = ∫₀^∞ f(x) sin(λx) dx
- **Inverse Sine Transform:**
  f(x) = (2/π) ∫₀^∞ Fₛ(λ) sin(λx) dλ
- **Fourier Cosine Transform:**
  Fₒ(λ) = Fₒ{f(x)} = ∫₀^∞ f(x) cos(λx) dx
- **Inverse Cosine Transform:**
  f(x) = (2/π) ∫₀^∞ Fₒ(λ) cos(λx) dλ
- When to use sine vs. cosine transform (boundary condition type)
- Relationship to half-range Fourier expansions
- Transforms of standard functions (e^(−ax), 1/(1+x²), etc.)
- Worked examples

---

### Topic 15 — Properties of Fourier Transforms

Builds the operational toolkit for working with Fourier transforms efficiently. Covers:
- **Linearity:** F{af + bg} = aF{f} + bF{g}
- **Shifting (Time shift):** F{f(x−a)} = e^(−iλa) F(λ)
- **Frequency shift (Modulation):** F{eⁱᵃˣ f(x)} = F(λ−a)
- **Scaling:** F{f(ax)} = (1/|a|) F(λ/a)
- **Differentiation in frequency domain:** F{xⁿf(x)} = iⁿ F⁽ⁿ⁾(λ)
- **Transform of derivative:** F{f⁽ⁿ⁾(x)} = (iλ)ⁿ F(λ)
- **Parseval's theorem:** ∫₋∞^∞ |f(x)|² dx = (1/2π) ∫₋∞^∞ |F(λ)|² dλ
- Worked examples applying properties to avoid direct integration

---

### Topic 16 — Inverse Fourier Transforms & Convolution Theorem

Completes the Fourier transform toolkit with inversion methods and the convolution result. Covers:
- **Inverse transform methods:** using tables, partial fractions, and symmetry
- **Self-reciprocal functions** under Fourier transform (e.g., Gaussian e^(−x²/2))
- **Convolution in time domain:** (f * g)(x) = ∫₋∞^∞ f(t) g(x−t) dt
- **Convolution theorem:** F{f * g} = F(λ)·G(λ)
- **Parseval's identity** as a special case of convolution theorem
- Applications to solving integral equations and PDEs
- Worked examples combining inversion and convolution

---

## Syllabus Coverage Map

| Syllabus Item | Covered In |
|---|---|
| Fourier coefficients (Euler's formulas) | Topic 09 |
| Dirichlet conditions | Topic 09 |
| Fourier series of even and odd functions | Topic 10 |
| Fourier series in arbitrary interval | Topic 11 |
| Half-range Fourier sine and cosine expansions | Topic 11 |
| Fourier integral theorem (without proof) | Topic 12 |
| Fourier sine and cosine integrals | Topic 12 |
| Complex form of Fourier integral | Topic 13 |
| Fourier transform | Topic 13 |
| Fourier sine and cosine transforms | Topic 14 |
| Properties of Fourier transforms | Topic 15 |
| Inverse Fourier transforms | Topic 16 |
| Convolution theorem (Fourier) | Topic 16 |

---

## Prerequisites Needed

- Unit IV: Laplace Transforms (integral transform concept)
- Calculus: improper integrals, integration by parts
- Trigonometric identities and Euler's formula: eⁱˣ = cos x + i sin x
- Basic complex numbers (modulus, argument, complex exponentials)
- Concept of odd and even functions
