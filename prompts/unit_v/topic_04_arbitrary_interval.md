# Prompt — Topic 04: Fourier Series in an Arbitrary Interval

**Unit:** V — Fourier Series and Fourier Transforms
**Course:** 23A54201 — Mathematics IV (Transform Techniques)
**University:** JNTUA College of Engineering (Autonomous)
**Target Audience:** B.Tech 2nd-year engineering students (non-mathematics majors)

---

## Prompt

You are an expert mathematics professor writing a **complete, compilable LaTeX (.tex) lecture note** for B.Tech engineering students on the topic **"Fourier Series in an Arbitrary Interval"**. This is Topic 04 of Unit V. Students have mastered Fourier series on $(-\pi,\pi)$; now they generalise to ANY period $2L$ — because real engineering signals have periods in seconds, metres, or volts, not in radians. Write as an enthusiastic, patient teacher who makes students feel the topic is already familiar — just not formally named yet.

---

## LATEX SETUP REQUIREMENTS

Same preamble structure as previous topics (four tcolorbox environments, pgfplots, listings).

fancyhdr:
- `\lhead{Topic 04: Fourier Series — Arbitrary Interval}`
- `\rhead{Unit V — Fourier Series \& Transforms}`
- `\cfoot{\thepage}`

Title: `\title{Topic 04: Fourier Series in an Arbitrary Interval \\ \large Unit V — Fourier Series \& Fourier Transforms}`, `\maketitle`, `\tableofcontents`, `\newpage`.

---

## AUDIENCE AND TONE

Same conversational, enthusiastic tone.

---

## OPENING HOOK (MANDATORY)

`\begin{curiositybox}[Hook]`: An electrical circuit oscillates with a period of 0.02 seconds (50 Hz mains frequency in India). Your Fourier series formula uses $\int_{-\pi}^{\pi}$ — but 0.02 seconds is nowhere near $\pi$ seconds. Does the formula break down? Absolutely not. All we need is one simple change of variable: replace $\pi$ with the actual half-period $L$. One substitution and the entire theory from Topics 01–03 carries over perfectly to any real-world period.

---

## REQUIRED SECTIONS

### 1. Why This Topic Exists
"Before we begin, here is the honest answer to why you are reading this..." Explain that $2\pi$-periodic functions are a special case; in practice, signals have arbitrary periods $2L$ (e.g., 0.02s, 1m, 2ms). This topic extends the theory directly. Two-column booktabs table:
- "Always assuming period is $2\pi$" | "Getting wrong coefficients for signals with non-$2\pi$ periods"
- "Forgetting to replace $\pi$ with $L$ throughout" | "Mixing up the two forms, especially in the $\cos(n\pi x/L)$ argument"
- "Using interval $(0,2L)$ vs $(-L,L)$ carelessly" | "Getting different-looking but equivalent series and being confused"
End with learnbox.

### 2. You Already Know This (Intuition First)
Compare to a ruler: the same measurement can be expressed in centimetres or inches by applying a scale factor. Extending Fourier series from period $2\pi$ to period $2L$ is exactly a scaling: substitute $x \to \pi x / L$ to stretch or shrink the standard interval to match any real period.

### 3. Fourier Series on $(-L, L)$ — General Formulae
`infobox`: For f(x) with period $2L$:
$$f(x) = \frac{a_0}{2} + \sum_{n=1}^{\infty}\left[a_n\cos\frac{n\pi x}{L} + b_n\sin\frac{n\pi x}{L}\right]$$
$$a_0 = \frac{1}{L}\int_{-L}^{L}f(x)\,dx$$
$$a_n = \frac{1}{L}\int_{-L}^{L}f(x)\cos\frac{n\pi x}{L}\,dx$$
$$b_n = \frac{1}{L}\int_{-L}^{L}f(x)\sin\frac{n\pi x}{L}\,dx$$
Derive by substituting $t = \pi x/L$ into the standard $(-\pi,\pi)$ formulas to show these follow naturally.

### 4. Alternative: Fourier Series on $(0, 2L)$
Note that for practical one-sided signals (e.g., starting at $t=0$), it is sometimes convenient to integrate over $(0,2L)$ instead of $(-L,L)$. Show the same formulas apply with limits changed to $(0,2L)$:
$$a_n = \frac{1}{L}\int_{0}^{2L}f(x)\cos\frac{n\pi x}{L}\,dx, \quad b_n = \frac{1}{L}\int_{0}^{2L}f(x)\sin\frac{n\pi x}{L}\,dx$$
Booktabs table comparing $(-L,L)$ vs $(0,2L)$ limits: when to prefer each, what the "period" looks like on each interval.

### 5. Even and Odd Symmetry on $(-L,L)$
`infobox` summary:
- Even on $(-L,L)$: $b_n=0$, $a_n = \frac{2}{L}\int_0^L f(x)\cos\frac{n\pi x}{L}dx$
- Odd on $(-L,L)$: $a_n=0$, $b_n = \frac{2}{L}\int_0^L f(x)\sin\frac{n\pi x}{L}dx$

### 6. Visualising the Change of Period
**pgfplots graph (MANDATORY):** Plot the square wave on $(-1,1)$ (period $2L=2$, $L=1$) and its partial sums $S_1$, $S_3$, $S_7$ using the general formulas. Grid=major, legend, labeled axes. The graph should look identical in shape to the $(-\pi,\pi)$ graph but with x-axis scaled to $[-1,1]$.

### 7. Worked Examples

**Example 1:** Find the Fourier series of $f(x)=x$ on $(-L,L)$, period $2L$. Identify symmetry (odd). Compute $b_n$ only, expressing the answer in terms of $L$. As a check, setting $L=\pi$ should recover the standard result from Topic 03.

**Example 2:** Find the Fourier series of $f(x) = x^2$ on $(-1,1)$ (so $L=1$). Compute $a_0$ and $a_n$ using the general formulas (even function, $b_n=0$). Compare to the $L=\pi$ result: same structure, different coefficient values.

**Example 3 (Engineering-flavoured):** A sawtooth voltage wave has period $T=0.02$ s ($L=0.01$) and is defined as $V(t)=100t/0.01$ for $0 \le t < 0.01$ (rising linearly from 0 to 100V), then immediately drops back to 0. Find the Fourier series of $V(t)$ in the form with period $0.02$ s. Express the answer in terms of actual physical units (Hz, volts) to show the real-world applicability.

All examples in `infobox`. End each with learnbox.

### 8. Excel Example (MANDATORY)
For Example 2 ($f(x)=x^2$ on $(-1,1)$), numerically compute $a_n$ for $n=1,2,3,4$ using the trapezoidal rule with 20 sub-intervals:
- Columns: $x_i$ | $x_i^2$ | $x_i^2\cos(n\pi x_i)$ for n=1,2,3,4
Compare to exact values. Show cell formulas.
End with learnbox.

### 9. Python Example (MANDATORY)
Python script using `sympy`:
- Defines a general L parameter
- Computes $a_0$, $a_n$, $b_n$ symbolically for $f(x)=x^2$ on $(-L,L)$
- Verifies that setting $L=\pi$ recovers the standard $(-\pi,\pi)$ result from Topic 03
- Constructs and prints the partial sum $S_5(x)$ in simplified form
Include expected printed output as comments. End with learnbox.

### 10. Viva-Style Oral Questions (8 questions with answers)
Cover: formula for $a_n$ in terms of $L$, how to derive general formulas from standard ones (substitution), what $L$ represents, why the cosine argument is $n\pi x/L$ not $nx$, relationship between $L$ and the physical period, $(-L,L)$ vs $(0,2L)$ convention, how even/odd simplifications carry over, what happens in the limit $L\to\pi$.

### 11. Descriptive Questions (5 exam-style questions)
Derive the general Fourier coefficient formulas via substitution from the standard form; find the Fourier series of a piecewise function on $(-2,2)$; find the Fourier series of $f(x)=|x|$ on $(-L,L)$; show the even/odd simplification formulas for arbitrary $L$; demonstrate a real-world sawtooth wave example with actual period and amplitude.

### 12. Practice Problems (6 problems)
$f(x)=x$ on $(-2,2)$; $f(x)=x^2$ on $(-3,3)$; piecewise on $(-1,1)$; sawtooth on $(0,4)$; triangular wave on $(-L,L)$; exponential on $(-1,1)$.

### 13. MCQs (5 questions)
Cover: coefficient formula with $L$, cosine argument identification, period from $L$, formula for even function on $(-L,L)$.

### 14. Common Mistakes Box
`mistakebox` tabular (5 rows):
- Using $1/\pi$ factor instead of $1/L$ in the coefficient formula
- Writing $\cos(nx)$ instead of $\cos(n\pi x/L)$
- Confusing L with the full period (full period is $2L$, not $L$)
- Forgetting to update the even/odd shortcut formula prefactor from $2/\pi$ to $2/L$
- Mixing $(-L,L)$ and $(0,2L)$ limits in the same problem

### 15. Quick Recap
`learnbox` 6–8 bullets: general Fourier formulas for period $2L$, substitution derivation, $(-L,L)$ and $(0,2L)$ alternatives, even/odd simplifications, real-world $L$ meaning, reduction check to $L=\pi$.

---

## MANDATORY QUALITY CHECKLIST

- [ ] Opening hook in `curiositybox`
- [ ] pgfplots graph showing partial sums on $(-1,1)$ or similar non-$\pi$ interval
- [ ] Booktabs comparison table ($(-L,L)$ vs $(0,2L)$)
- [ ] Excel numerical coefficient computation for arbitrary $L$
- [ ] Python symbolic derivation with $L$ parameter
- [ ] Every major example ends with `learnbox`
- [ ] All four tcolorbox environments used
- [ ] `\end{document}` at end
- [ ] Conversational tone throughout
