# Unit V — Fourier Series and Fourier Transforms

**Course:** 23A54201 — Mathematics IV (Transform Techniques)  
**University:** JNTUA College of Engineering (Autonomous)  

---

## Overview

Unit V covers two major tools in signal analysis and engineering mathematics. **Fourier Series** represents periodic functions as infinite sums of sines and cosines. **Fourier Transforms** extend this idea to non-periodic functions, providing frequency-domain representations used in signal processing, communications, and PDE solutions.

---

## Topic List (in teaching order)

| Topic No. | Topic Name | Prompt File |
|-----------|-----------|-------------|
| 01 | Fourier Series — Determination of Fourier Coefficients (Euler's Formulae) | `prompts/unit_v/topic_01_fourier_coefficients.md` |
| 02 | Dirichlet Conditions for the Existence of Fourier Series | `prompts/unit_v/topic_02_dirichlet_conditions.md` |
| 03 | Fourier Series of Even and Odd Functions | `prompts/unit_v/topic_03_even_odd_functions.md` |
| 04 | Fourier Series in an Arbitrary Interval | `prompts/unit_v/topic_04_arbitrary_interval.md` |
| 05 | Half-Range Fourier Sine and Cosine Expansions | `prompts/unit_v/topic_05_half_range_expansions.md` |
| 06 | Fourier Integral Theorem, Sine & Cosine Integrals, Complex Form | `prompts/unit_v/topic_06_fourier_integral_theorem.md` |
| 07 | Fourier Transform, Sine & Cosine Transforms, Properties | `prompts/unit_v/topic_07_fourier_transform.md` |
| 08 | Convolution Theorem for Fourier Transforms | `prompts/unit_v/topic_08_convolution_theorem.md` |

> **Note on numbering:** Unit IV topics are numbered 01–08; Unit V topics are independently numbered 01–08 (16 total topics across both units, with matching prefixes reset per unit).

---

## Topic Descriptions

### Topic 01 — Fourier Series: Determination of Fourier Coefficients (Euler's Formulae)

Establishes the complete framework for computing Fourier series. Covers:
- **Trigonometric series:** f(x) = a₀/2 + Σ[aₙcos(nx) + bₙsin(nx)]
- **Euler's formulas** for Fourier coefficients:
  - a₀ = (1/π) ∫₋π^π f(x) dx
  - aₙ = (1/π) ∫₋π^π f(x) cos(nx) dx
  - bₙ = (1/π) ∫₋π^π f(x) sin(nx) dx
- Worked examples: expanding simple piecewise functions in (−π, π)

---

### Topic 02 — Dirichlet Conditions for the Existence of Fourier Series

States the sufficient conditions under which a Fourier series converges to a given function. Covers:
- **Dirichlet conditions:**
  1. f(x) is periodic
  2. f(x) is piecewise continuous on one period
  3. f(x) has a finite number of maxima, minima, and discontinuities
- Convergence at points of continuity and at jump discontinuities (converges to the average of left/right limits)
- Why these conditions are a validity check before applying Euler's formulas from Topic 01

---

### Topic 03 — Fourier Series of Even and Odd Functions

Exploits function symmetry to simplify Fourier coefficient computation. Covers:
- **Even function:** f(−x) = f(x) ⟹ all bₙ = 0 (pure cosine series)
- **Odd function:** f(−x) = −f(x) ⟹ a₀ = 0 and all aₙ = 0 (pure sine series)
- Simplified formulas using symmetry:
  - Even: a₀ = (2/π)∫₀^π f(x) dx; aₙ = (2/π)∫₀^π f(x)cos(nx) dx
  - Odd: bₙ = (2/π)∫₀^π f(x)sin(nx) dx
- Testing a function for even/odd symmetry
- Worked examples: |x|, x², x, x³ type functions

---

### Topic 04 — Fourier Series in an Arbitrary Interval

Extends Fourier series beyond (−π, π) to general intervals. Covers:
- **Fourier series on (−L, L):**
  - aₙ = (1/L) ∫₋L^L f(x) cos(nπx/L) dx
  - bₙ = (1/L) ∫₋L^L f(x) sin(nπx/L) dx
- Change of interval from (−π, π) to (−L, L) and to (0, 2L)
- Worked examples with non-π intervals (e.g., (0, 2), (−1, 1))

---

### Topic 05 — Half-Range Fourier Sine and Cosine Expansions

Applies the arbitrary-interval formulas from Topic 04 to one-sided intervals. Covers:
- **Half-range expansions on (0, L):**
  - **Cosine series** (even extension): only cosine terms
  - **Sine series** (odd extension): only sine terms
- Choosing between sine and cosine half-range expansions based on boundary conditions
- Applications to heat equation / PDE boundary conditions

---

### Topic 06 — Fourier Integral Theorem, Sine & Cosine Integrals, Complex Form

Bridges Fourier series (periodic) to Fourier transforms (non-periodic). Covers:
- **Motivation:** What happens to Fourier series as the period T → ∞?
- **Fourier Integral Theorem (without proof):**
  f(x) = (1/π) ∫₀^∞ [∫₋∞^∞ f(t) cos λ(t−x) dt] dλ
- **Fourier sine integral:** for odd (or one-sided) functions
  f(x) = (2/π) ∫₀^∞ sin(λx) [∫₀^∞ f(t) sin(λt) dt] dλ
- **Fourier cosine integral:** for even (or one-sided) functions
  f(x) = (2/π) ∫₀^∞ cos(λx) [∫₀^∞ f(t) cos(λt) dt] dλ
- **Complex form of the Fourier integral**, derived from the real sine/cosine form

---

### Topic 07 — Fourier Transform, Sine & Cosine Transforms, Properties

Defines the Fourier transform proper plus its specialised variants and key operational properties. Covers:
- **Fourier transform and inverse:**
  F(ω) = ∫₋∞^∞ f(t) e^(−iωt) dt ; f(t) = (1/2π) ∫₋∞^∞ F(ω) e^(iωt) dω
- **Fourier cosine transform** and **Fourier sine transform** (for functions on [0, ∞))
- **Properties of Fourier transforms:** linearity, time/frequency shifting, time scaling, time reversal, differentiation, integration, duality, modulation (10+ properties)
- Standard transform pairs table

---

### Topic 08 — Convolution Theorem for Fourier Transforms

The culminating result connecting time-domain convolution to frequency-domain multiplication. Covers:
- **Definition of convolution:** (f * g)(t) = ∫₋∞^∞ f(τ) g(t−τ) dτ
- **Convolution theorem:** F{f * g}(ω) = F(ω) · G(ω), and its dual (multiplication theorem)
- Full proof via order-of-integration swap and substitution
- Contrast with the Laplace convolution theorem (different limits, causality)
- LTI systems / filtering interpretation: Y(ω) = H(ω)X(ω)

---

## Textbooks Referenced

1. B.S. Grewal — *Higher Engineering Mathematics*, Khanna Publishers, 44th Edition
2. Erwin Kreyszig — *Advanced Engineering Mathematics*, 10th Edition, Wiley
3. A.R. Vasistha & R.K. Gupta — *Integral Transforms*, Krishna Prakashan Media
