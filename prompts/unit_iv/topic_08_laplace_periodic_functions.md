# Prompt — Topic 08: Laplace Transform of Periodic Functions

**Unit:** IV — Laplace Transforms
**Course:** 23A54201 — Mathematics IV (Transform Techniques)
**University:** JNTUA College of Engineering (Autonomous)
**Target Audience:** B.Tech 2nd-year engineering students (non-mathematics majors)

---

## Prompt

You are an expert mathematics professor writing a **complete, compilable LaTeX (.tex) lecture note** for B.Tech engineering students on the topic **"Laplace Transform of Periodic Functions"**. This is Topic 08, the final topic of Unit IV. Students have mastered shifting theorems and convolution; now they learn a specialized formula for periodic signals like square waves and sawtooth waves — common in electronics and signal processing. Write as an enthusiastic, patient teacher who makes students feel the topic is already familiar — just not formally named yet.

---

## LATEX SETUP REQUIREMENTS

Same exact preamble structure as previous topics (four tcolorbox environments, pgfplots, listings config).

Set up fancyhdr with:
- `\lhead{Topic 08: Periodic Function Transforms}`
- `\rhead{Unit IV — Laplace Transforms}`
- `\cfoot{\thepage}`

Title page: `\title{Topic 08: Laplace Transform of Periodic Functions \\ \large Unit IV — Laplace Transforms}`, `\maketitle`, `\tableofcontents`, `\newpage`.

---

## AUDIENCE AND TONE

Same conversational, enthusiastic tone as previous topics.

---

## OPENING HOOK (MANDATORY)

Place inside `\begin{curiositybox}[Hook]`: A power supply circuit outputs a square wave that switches between 0V and 5V every millisecond, forever. Integrating $e^{-st}$ times this wave from 0 to infinity sounds like an infinite nightmare of piecewise integration — unless you notice something beautiful: the wave repeats EXACTLY every period. That repetition means we only ever need to integrate over ONE period, then let a simple geometric series formula handle the rest of eternity for us.

---

## REQUIRED SECTIONS

### 1. Why This Topic Exists
"Before we begin, here is the honest answer to why you are reading this..." Explain that periodic signals (square waves, sawtooth waves, rectified sine waves) are everywhere in electrical and mechanical engineering, and computing their transform directly via infinite piecewise integration is impractical without this shortcut formula. Two-column booktabs table:
- "Attempting direct infinite-interval integration" | "Getting stuck in an infinite sum without a closed form"
- "Forgetting the $(1-e^{-sT})$ denominator" | "Getting only the first-period contribution, missing all repeats"
- "Using wrong period T from the graph" | "Completely wrong formula substitution"
End with a learnbox.

### 2. You Already Know This (Intuition First)
Compare to a geometric series / EMI loan repayment: if you know the effect of ONE repeating installment and the discount factor between installments, the total effect of infinitely many repeated installments is just the single-installment effect divided by (1 minus the discount factor). Periodic Laplace transforms follow exactly the same geometric series logic, with $e^{-sT}$ playing the role of the "discount factor" per period.

### 3. Definition of a Periodic Function
`infobox`: f(t) is periodic with period T if $f(t+T) = f(t)$ for all $t\ge 0$.
**pgfplots graph (MANDATORY):** Plot a square wave with period T=2 (value 1 on [0,1), value 0 on [1,2), repeating) over $t\in[0,6]$, clearly showing 3 full periods. Grid=major, labeled axes.

### 4. The Periodic Function Theorem
`infobox`:
$$\mathcal{L}\{f(t)\} = \frac{1}{1-e^{-sT}}\int_0^T e^{-st}f(t)\,dt$$
where T is the period of f(t).

### 5. Proof of the Theorem
Derive step by step: split $\int_0^\infty = \sum_{n=0}^\infty \int_{nT}^{(n+1)T}$, substitute $\tau=t-nT$ in each piece using periodicity $f(t)=f(\tau)$, factor out $e^{-nsT}$ from each term, and recognize the resulting infinite sum as a geometric series with ratio $e^{-sT}$ (converges since $s>0\Rightarrow e^{-sT}<1$). Sum the geometric series to get the final closed form.

### 6. Worked Examples

**Example 1 (Square wave):** Find $\mathcal{L}\{f(t)\}$ for the square wave $f(t)=1$ on $[0,1)$, $f(t)=0$ on $[1,2)$, period T=2. Compute the one-period integral explicitly, then apply the theorem.
**Example 2 (Sawtooth wave):** Find $\mathcal{L}\{f(t)\}$ for the sawtooth wave $f(t)=t$ on $[0,T)$, repeating with period T. Compute $\int_0^T e^{-st}t\,dt$ using integration by parts, then apply the theorem.
**Example 3 (Triangular wave):** Find $\mathcal{L}\{f(t)\}$ for a triangular wave rising linearly from 0 to 1 on $[0,1)$ then falling back to 0 on $[1,2)$, period T=2. Set up the piecewise one-period integral and apply the theorem.

All examples inside `infobox`. End each with learnbox.

### 7. Comparison: Direct vs. Periodic Formula Approach
Booktabs table (5+ rows) comparing effort/steps of: writing the function using infinite sums of unit step functions (Topic 06 approach) vs. using the periodic function theorem directly — show the periodic formula is dramatically shorter.

### 8. Excel Example (MANDATORY)
Numerically verify Example 1 (square wave) at s=1:
- Columns: n (period index) | Start of period nT | $e^{-s\cdot nT}$ | Contribution to sum
Sum the first 10 terms of the geometric series numerically and compare to the exact closed-form value from the theorem.
End with learnbox.

### 9. Python Example (MANDATORY)
Python script using `sympy` that:
- Symbolically computes the one-period integral for the square wave and sawtooth wave examples
- Applies the periodic formula and simplifies to closed form
- Cross-checks numerically using `scipy.integrate.quad` over many periods with a cutoff, comparing to the closed-form answer
Include expected printed output as comments. End with learnbox.

### 10. Viva-Style Oral Questions (8 questions with answers)
Cover: definition of periodic function, statement of the theorem, why the geometric series converges for s>0, key proof step (splitting into period intervals), difference in effort vs. unit-step approach, real-world periodic signal examples, what T represents in the formula, why the one-period integral is enough.

### 11. Descriptive Questions (5 exam-style questions)
Derive the periodic function theorem fully; find the transform of a full-wave rectified sine wave; find transform of a general sawtooth with amplitude A and period T; explain the geometric series convergence condition; compare unit-step-based and periodic-formula-based derivations for the same square wave.

### 12. Practice Problems (6 problems with answer hints)
Cover square wave with different period/amplitude, sawtooth, triangular wave, half-wave rectified sine, and one function requiring piecewise setup within one period.

### 13. MCQs (5 questions)
5 MCQs, bold correct answer, one-line explanation. Cover: theorem formula recognition, period identification from a graph, convergence condition, one-period integral setup.

### 14. Common Mistakes Box
`mistakebox` tabular (5 rows): Mistake | What Students Do | Correct Approach.
- Using the wrong period T read from the graph
- Forgetting the $(1-e^{-sT})$ denominator entirely
- Incorrectly setting up the one-period integral limits
- Sign errors in the geometric series summation step
- Confusing periodic function transform with an ordinary unit-step piecewise transform

### 15. Quick Recap
`learnbox` with 6–8 bullets: periodic function definition, theorem formula, proof idea (geometric series), key examples (square, sawtooth, triangular wave), convergence condition, advantage over direct piecewise integration.

---

## MANDATORY QUALITY CHECKLIST

- [ ] Opening hook present in `curiositybox`
- [ ] At least 1 pgfplots graph with axis labels, legend, grid
- [ ] At least 1 booktabs table with 5+ data rows
- [ ] At least 1 Excel column-by-column example with cell formulas shown
- [ ] At least 1 Python lstlisting with verbatim output shown
- [ ] Every major example ends with a `learnbox` "What Did We Learn?"
- [ ] All four tcolorbox environments used at least once
- [ ] `\end{document}` present at the very end
- [ ] No undefined LaTeX macros
- [ ] Tone is conversational and encouraging throughout
- [ ] All formulae in correct LaTeX syntax
- [ ] No section references a figure that is not defined
