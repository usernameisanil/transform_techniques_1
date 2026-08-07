# Prompt — Topic 06: Fourier Integral Theorem, Sine & Cosine Integrals, Complex Form

**Unit:** V — Fourier Series and Fourier Transforms
**Course:** 23A54201 — Mathematics IV (Transform Techniques)
**University:** JNTUA College of Engineering (Autonomous)
**Target Audience:** B.Tech 2nd-year engineering students (non-mathematics majors)

---

## Prompt

You are an expert mathematics professor writing a **complete, compilable LaTeX (.tex) lecture note** for B.Tech engineering students on the topic **"Fourier Integral Theorem — Sine & Cosine Integrals — Complex Form"**. This is Topic 06 of Unit V and the bridge from Fourier SERIES (periodic functions) to Fourier TRANSFORMS (non-periodic functions). Students have mastered Fourier series; now they ask: what if the period goes to infinity? Write as an enthusiastic, patient teacher who makes students feel the topic is already familiar — just not formally named yet.

---

## LATEX SETUP REQUIREMENTS

Same preamble structure as previous topics (four tcolorbox environments, pgfplots, listings).

fancyhdr:
- `\lhead{Topic 06: Fourier Integral Theorem}`
- `\rhead{Unit V — Fourier Series \& Transforms}`
- `\cfoot{\thepage}`

Title: `\title{Topic 06: Fourier Integral Theorem, Sine \& Cosine Integrals, Complex Form \\ \large Unit V — Fourier Series \& Fourier Transforms}`, `\maketitle`, `\tableofcontents`, `\newpage`.

---

## AUDIENCE AND TONE

Same conversational, enthusiastic tone.

---

## OPENING HOOK (MANDATORY)

`\begin{curiositybox}[Hook]`: Fourier series works beautifully for periodic signals. But a single pulse of voltage that fires once and never repeats — like a radar ping or a door-slam — is not periodic at all. Its period is effectively infinite. What happens to the Fourier series when we let $L \to \infty$? The sum over discrete harmonics $n$ becomes an integral over a continuous frequency variable $\lambda$. This passage from sum to integral is the Fourier Integral Theorem, and it unlocks the analysis of ALL signals, periodic or not.

---

## REQUIRED SECTIONS

### 1. Why This Topic Exists
"Before we begin, here is the honest answer to why you are reading this..." Explain that periodic functions are a special case; most real-world signals (radar pulses, transients, speech) are non-periodic and require a continuous-frequency representation. Two-column booktabs table:
- "Trying to apply Fourier series to a non-periodic function" | "Getting no valid result at all"
- "Skipping the limiting argument" | "Not understanding where the Fourier integral formula comes from"
- "Confusing Fourier integral with Fourier transform" | "Treating them as unrelated formulas when the transform is simply a compact notation for the integral"
End with learnbox.

### 2. You Already Know This (Intuition First)
Compare to zooming in on a number line: Fourier series places harmonics at discrete points $n/L$ on the frequency axis (like a comb). As $L\to\infty$, the spacing $1/L$ between comb teeth shrinks to zero, and the comb becomes a continuous curve — the Fourier integral. The same logic applies as discrete sums becoming Riemann integrals.

### 3. The Fourier Integral Theorem (Statement Without Proof)
`infobox`:
$$f(x) = \int_0^\infty\left[A(\lambda)\cos(\lambda x) + B(\lambda)\sin(\lambda x)\right]d\lambda$$
where:
$$A(\lambda) = \frac{1}{\pi}\int_{-\infty}^{\infty}f(t)\cos(\lambda t)\,dt, \qquad B(\lambda) = \frac{1}{\pi}\int_{-\infty}^{\infty}f(t)\sin(\lambda t)\,dt$$
State validity condition: f(x) is absolutely integrable on $(-\infty,\infty)$, i.e., $\int_{-\infty}^{\infty}|f(x)|dx < \infty$, and piecewise smooth. Note: proof not required; intuition via $L\to\infty$ argument given as motivation in Section 2.

### 4. Fourier Cosine Integral (for Even Functions)
`infobox`: If f(x) is even on $(-\infty,\infty)$ (or defined only on $(0,\infty)$ and extended evenly), then $B(\lambda)=0$ and:
$$f(x) = \frac{2}{\pi}\int_0^\infty A_c(\lambda)\cos(\lambda x)\,d\lambda, \quad \text{where } A_c(\lambda) = \int_0^\infty f(t)\cos(\lambda t)\,dt$$

### 5. Fourier Sine Integral (for Odd Functions)
`infobox`: If f(x) is odd (or defined only on $(0,\infty)$ and extended oddly), then $A(\lambda)=0$ and:
$$f(x) = \frac{2}{\pi}\int_0^\infty B_s(\lambda)\sin(\lambda x)\,d\lambda, \quad \text{where } B_s(\lambda) = \int_0^\infty f(t)\sin(\lambda t)\,dt$$

### 6. Complex Form of the Fourier Integral
`infobox`: Combining sine and cosine using $e^{i\lambda x} = \cos(\lambda x)+i\sin(\lambda x)$:
$$f(x) = \frac{1}{2\pi}\int_{-\infty}^{\infty}\left[\int_{-\infty}^{\infty}f(t)e^{-i\lambda t}dt\right]e^{i\lambda x}\,d\lambda$$
Note the inner bracket is the Fourier Transform $F(\lambda)$ and the outer integral is the inverse transform — preview of Topic 07.

### 7. Visualising Frequency Spectrum
**pgfplots graph (MANDATORY):** Plot the rectangular pulse $f(x)=1$ for $|x|<1$, $f(x)=0$ otherwise, alongside its Fourier integral amplitude $A(\lambda) = \frac{2\sin\lambda}{\pi\lambda}$ (a sinc function) as a function of $\lambda$. Two subplots: top = time domain f(x), bottom = frequency domain $A(\lambda)$. Grid=major, labeled axes, legends.

### 8. Worked Examples

**Example 1:** Find the Fourier integral representation of $f(x) = e^{-|x|}$. Compute $A(\lambda)$ and $B(\lambda)$. Note that f is even, so $B(\lambda)=0$. Evaluate $A(\lambda) = \frac{2}{\pi(1+\lambda^2)}$. Deduce: $\int_0^\infty\frac{\cos(\lambda x)}{1+\lambda^2}d\lambda = \frac{\pi}{2}e^{-|x|}$.

**Example 2:** Find the Fourier sine integral of $f(x) = e^{-ax}$ for $x>0$ ($a>0$). Compute $B_s(\lambda) = \int_0^\infty e^{-at}\sin(\lambda t)dt = \frac{\lambda}{a^2+\lambda^2}$. Hence represent $e^{-ax}$ as a sine integral.

**Example 3:** Find the Fourier cosine integral of the rectangular pulse $f(x)=1$ for $0<x<1$, $f(x)=0$ for $x>1$. Compute $A_c(\lambda)$ and write the full representation.

All examples in `infobox`. End each with learnbox.

### 9. Excel Example (MANDATORY)
Numerically verify Example 1 at $x=0$: show that $\frac{2}{\pi}\int_0^\infty \frac{d\lambda}{1+\lambda^2} = 1 = e^0$ using a Riemann sum:
- Columns: $\lambda_i$ (0 to 10, step 0.1) | $\frac{2/\pi}{1+\lambda_i^2}$ | Cumulative Riemann sum
Show the sum converges to 1.000.
End with learnbox.

### 10. Python Example (MANDATORY)
Python script using `sympy`:
- Computes $A(\lambda)$ for $f(x)=e^{-|x|}$ symbolically
- Verifies the Fourier integral representation by computing the inverse integral back to f(x) at a sample x value
- Plots (describe in comments) the frequency spectrum $A(\lambda)$ showing the Lorentzian shape
Include expected printed output as comments. End with learnbox.

### 11. Viva-Style Oral Questions (8 questions with answers)
Cover: statement of Fourier integral theorem, validity condition (absolute integrability), how it's derived from Fourier series in the limit $L\to\infty$, what $A(\lambda)$ and $B(\lambda)$ represent physically, when to use sine vs cosine integral, what the complex form achieves, connection to Fourier transform (Topic 07 preview), what happens to the Fourier integral at a jump discontinuity.

### 12. Descriptive Questions (5 exam-style questions)
State and motivate the Fourier integral theorem (without formal proof); find the Fourier cosine integral of $e^{-ax}$; find the Fourier integral of the rectangular pulse and deduce a value of $\int_0^\infty (\sin\lambda)/\lambda\,d\lambda$; explain the transition from Fourier series (discrete) to Fourier integral (continuous); derive the complex form from the real form.

### 13. Practice Problems (6 problems)
$f(x)=e^{-2|x|}$; $f(x)=xe^{-x}$ for $x>0$; $f(x)=\cos(ax)$ for $|x|<b$ (rectangular window); $f(x)=1/(1+x^2)$; triangular pulse; $f(x)=e^{-x}\sin(x)$ for $x>0$.

### 14. MCQs (5 questions)
Cover: theorem validity condition, $A(\lambda)$ formula, sine vs cosine integral choice, complex form structure, connection to Fourier transform.

### 15. Common Mistakes Box
`mistakebox` tabular (5 rows):
- Applying Fourier integral to a function that is NOT absolutely integrable
- Confusing $A(\lambda)$ with $F(\lambda)$ (Fourier transform) — they differ by a factor of $\pi$
- Using sine integral for an even function (should use cosine)
- Forgetting the $1/\pi$ factor in $A(\lambda)$ and $B(\lambda)$
- Treating the complex form as a different theorem rather than a reformulation

### 16. Quick Recap
`learnbox` 6–8 bullets: Fourier integral theorem statement, validity condition, sine integral, cosine integral, complex form, spectrum visualisation, connection to Fourier transform (Topic 07).

---

## MANDATORY QUALITY CHECKLIST

- [ ] Opening hook in `curiositybox`
- [ ] pgfplots dual-panel graph (time domain + frequency spectrum)
- [ ] Booktabs table contrasting series vs integral approach
- [ ] Excel Riemann sum numerical verification
- [ ] Python symbolic A(lambda) computation
- [ ] Every major example ends with `learnbox`
- [ ] All four tcolorbox environments used
- [ ] `\end{document}` at end
- [ ] Conversational tone throughout
