# Prompt — Topic 05: Half-Range Fourier Sine and Cosine Expansions

**Unit:** V — Fourier Series and Fourier Transforms
**Course:** 23A54201 — Mathematics IV (Transform Techniques)
**University:** JNTUA College of Engineering (Autonomous)
**Target Audience:** B.Tech 2nd-year engineering students (non-mathematics majors)

---

## Prompt

You are an expert mathematics professor writing a **complete, compilable LaTeX (.tex) lecture note** for B.Tech engineering students on the topic **"Half-Range Fourier Sine and Cosine Expansions"**. This is Topic 05 of Unit V — the final Fourier Series topic. Students know full-range series; now they learn how to represent a function defined only on $(0,L)$ using EITHER a pure sine series OR a pure cosine series, by artificially extending the function to the full range. Write as an enthusiastic, patient teacher who makes students feel the topic is already familiar — just not formally named yet.

---

## LATEX SETUP REQUIREMENTS

Same preamble structure as previous topics (four tcolorbox environments, pgfplots, listings).

fancyhdr:
- `\lhead{Topic 05: Half-Range Expansions}`
- `\rhead{Unit V — Fourier Series \& Transforms}`
- `\cfoot{\thepage}`

Title: `\title{Topic 05: Half-Range Fourier Sine \& Cosine Expansions \\ \large Unit V — Fourier Series \& Fourier Transforms}`, `\maketitle`, `\tableofcontents`, `\newpage`.

---

## AUDIENCE AND TONE

Same conversational, enthusiastic tone.

---

## OPENING HOOK (MANDATORY)

`\begin{curiositybox}[Hook]`: A civil engineer is analysing heat flow along a rod from $x=0$ to $x=L$. The temperature function $f(x)$ is only defined on $[0,L]$ — it doesn't exist for negative $x$. Yet the Fourier series formulas need a symmetric interval. The trick? Artificially extend the function to $[-L,0]$ by either reflecting it (even extension, giving a cosine series) or flipping it (odd extension, giving a sine series). You choose which extension to use based on the boundary conditions of your problem. One choice, two completely different-looking series — both equally valid representations of the same original function.

---

## REQUIRED SECTIONS

### 1. Why This Topic Exists
"Before we begin, here is the honest answer to why you are reading this..." Explain that in physical problems (heat equation, wave equation, vibrating string with fixed or free ends), the function is naturally defined only on $(0,L)$ and the boundary conditions (e.g., zero displacement at both ends = sine series; zero slope at both ends = cosine series) determine which half-range expansion to use. Two-column booktabs table:
- "Applying a full-range series to a half-range problem" | "Introducing fictitious behaviour on $(-L,0)$ that contradicts the physical problem"
- "Confusing which extension gives sine vs cosine" | "Getting the wrong series type for the given boundary conditions"
- "Forgetting to double the integration range prefactor" | "Getting coefficients twice too large or too small"
End with learnbox.

### 2. You Already Know This (Intuition First)
Compare to a mirror: an even extension places a mirror at $x=0$ and reflects the function to the left — giving an even function, hence only cosines. An odd extension places an anti-mirror (rotating 180°) — giving an odd function, hence only sines. You choose the mirror type based on the boundary conditions, not on any property of f itself.

### 3. Half-Range Cosine Series (Even Extension)
`infobox`: For $f(x)$ defined on $(0,L)$, the half-range cosine expansion is:
$$f(x) = \frac{a_0}{2} + \sum_{n=1}^{\infty}a_n\cos\frac{n\pi x}{L}, \quad 0 < x < L$$
where:
$$a_0 = \frac{2}{L}\int_0^L f(x)\,dx, \qquad a_n = \frac{2}{L}\int_0^L f(x)\cos\frac{n\pi x}{L}\,dx$$
Derive: extend f to an even function on $(-L,L)$ by defining $f(-x)=f(x)$; apply the even-function Fourier series formulas from Topic 03.

### 4. Half-Range Sine Series (Odd Extension)
`infobox`: For $f(x)$ defined on $(0,L)$, the half-range sine expansion is:
$$f(x) = \sum_{n=1}^{\infty}b_n\sin\frac{n\pi x}{L}, \quad 0 < x < L$$
where:
$$b_n = \frac{2}{L}\int_0^L f(x)\sin\frac{n\pi x}{L}\,dx$$
Derive: extend f to an odd function on $(-L,L)$ by defining $f(-x)=-f(x)$; apply the odd-function Fourier series formulas.

### 5. Visualising Both Extensions
**pgfplots graph (MANDATORY):** Three panels for $f(x)=x$ on $(0,1)$:
- Panel 1: original f(x) on $(0,1)$ only
- Panel 2: even extension on $(-1,1)$ (showing the "V" shape of $|x|$)
- Panel 3: odd extension on $(-1,1)$ (showing the straight line through origin)
All three panels on the same figure, using subplots or stacked pgfplots. Grid=major, labeled axes, legend.

### 6. Which Extension to Use? (Engineering Decision Guide)
Booktabs table (5+ rows): Boundary Condition | Physical Meaning | Extension to Use | Series Type.
- $f(0)=0$ and $f(L)=0$ (fixed ends) | Displacement zero at both ends (vibrating string) | Odd | Sine series
- $f'(0)=0$ and $f'(L)=0$ (free ends) | Slope zero at both ends (insulated rod ends) | Even | Cosine series
- $f(0)=0$ only | One fixed end | Odd | Sine series
- $f'(0)=0$ only | One insulated end | Even | Cosine series
- No boundary condition specified | Choice is free | Either | Depends on simplicity

### 7. Parseval's Identity (Brief Introduction)
`infobox`: For the half-range cosine series:
$$\frac{1}{L}\int_0^L [f(x)]^2\,dx = \frac{a_0^2}{4} + \frac{1}{2}\sum_{n=1}^\infty a_n^2$$
And analogously for the sine series with $b_n$. Explain briefly: this relates the "energy" of f(x) over $(0,L)$ to the sum of squares of its Fourier coefficients. Useful for checking results numerically.

### 8. Worked Examples

**Example 1:** Find both the half-range sine AND cosine series of $f(x)=x$ on $(0,\pi)$ (so $L=\pi$). Compute coefficients for each series fully. Plot conceptually: explain the sine series converges to the odd extension (straight line), the cosine series to the even extension (V-shape = $|x|$).

**Example 2:** Find the half-range sine series of $f(x) = x(\pi-x)$ on $(0,\pi)$. Compute $b_n$ using integration by parts twice. Note which $b_n$ vanish and which survive.

**Example 3 (Engineering application):** A string of length $L$ is given an initial displacement $f(x) = \begin{cases}x, & 0\le x \le L/2 \\ L-x, & L/2\le x\le L\end{cases}$ (triangular pluck). The boundary conditions require $f(0)=f(L)=0$. Find the appropriate half-range series. Comment on the physical meaning of each harmonic term (fundamental frequency, overtones).

All examples in `infobox`. End each with learnbox.

### 9. Excel Example (MANDATORY)
For Example 1, numerically compute $b_n$ for $n=1,2,3,4,5$ using the trapezoidal rule with $L=\pi$, 20 sub-intervals:
- Columns: $x_i$ | $f(x_i)=x_i$ | $f(x_i)\sin(x_i)$ | $f(x_i)\sin(2x_i)$ | $f(x_i)\sin(3x_i)$ ...
Compare to exact $b_n = \frac{2(-1)^{n+1}}{n}$.
End with learnbox.

### 10. Python Example (MANDATORY)
Python script using `sympy`:
- Computes both half-range sine and cosine coefficients for $f(x)=x$ on $(0,\pi)$ symbolically
- Prints both series as expressions
- Verifies Parseval's identity numerically for both series (sum of $b_n^2/2$ compared to $\frac{1}{\pi}\int_0^\pi x^2 dx$)
Include expected printed output as comments. End with learnbox.

### 11. Viva-Style Oral Questions (8 questions with answers)
Cover: definition of half-range expansion, how even extension gives cosine series, how odd extension gives sine series, the $2/L$ prefactor origin, which series to use for which boundary condition (fixed vs free ends), Parseval's identity statement, why two different-looking series can represent the same function on $(0,L)$, physical meaning of sine vs cosine series in vibration problems.

### 12. Descriptive Questions (5 exam-style questions)
Derive the half-range cosine formula from the even extension argument; find the half-range sine series of $\cos(x)$ on $(0,\pi)$; find the half-range cosine series of $\sin(x)$ on $(0,\pi)$; solve a heat/wave equation boundary value problem setup (finding the appropriate series type from BCs); verify Parseval's identity for a specific example.

### 13. Practice Problems (6 problems)
Half-range sine of $f(x)=1$ on $(0,L)$; half-range cosine of $f(x)=x^2$ on $(0,L)$; half-range sine of $f(x)=\cos(\pi x/L)$; triangular wave half-range both; exponential $e^x$ on $(0,1)$ both sine and cosine.

### 14. MCQs (5 questions)
Cover: which extension gives cosine series, coefficient formula for $b_n$, which boundary condition requires sine series, Parseval's identity form, prefactor identification.

### 15. Common Mistakes Box
`mistakebox` tabular (5 rows):
- Using $1/L$ instead of $2/L$ in the half-range formulas
- Choosing cosine series when boundary conditions require sine (or vice versa)
- Extending the function to $(-L,L)$ incorrectly (forgetting the sign flip for odd extension)
- Confusing half-range ($0$ to $L$) integral limits with full-range ($-L$ to $L$)
- Applying half-range formulas outside $(0,L)$ without acknowledging the periodic extension

### 16. Quick Recap
`learnbox` 6–8 bullets: motivation (functions defined only on $(0,L)$), even extension $\to$ cosine series, odd extension $\to$ sine series, coefficient formulas with $2/L$, boundary condition decision guide, Parseval's identity, applications in PDEs.

---

## MANDATORY QUALITY CHECKLIST

- [ ] Opening hook in `curiositybox`
- [ ] pgfplots 3-panel graph (original, even extension, odd extension)
- [ ] Booktabs boundary condition decision guide table
- [ ] Excel numerical coefficient verification
- [ ] Python symbolic coefficients + Parseval verification
- [ ] Every major example ends with `learnbox`
- [ ] All four tcolorbox environments used
- [ ] `\end{document}` at end
- [ ] Conversational tone throughout
