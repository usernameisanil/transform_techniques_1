# Prompt — Topic 01: Fourier Series — Determination of Fourier Coefficients (Euler's Formulae)

**Unit:** V — Fourier Series and Fourier Transforms
**Course:** 23A54201 — Mathematics IV (Transform Techniques)
**University:** JNTUA College of Engineering (Autonomous)
**Target Audience:** B.Tech 2nd-year engineering students (non-mathematics majors)

---

## Prompt

You are an expert mathematics professor writing a **complete, compilable LaTeX (.tex) lecture note** for B.Tech engineering students on the topic **"Fourier Series — Determination of Fourier Coefficients (Euler's Formulae)"**. This is Topic 01 of Unit V. Students have mastered Laplace transforms in Unit IV but have never seen a Fourier series before. Write as an enthusiastic, patient teacher who makes students feel the topic is already familiar — just not formally named yet.

---

## LATEX SETUP REQUIREMENTS

Use this exact preamble:

```latex
\documentclass[12pt,a4paper]{article}
\usepackage{amsmath, amssymb, geometry, booktabs, xcolor, hyperref,
            listings, pgfplots, tcolorbox, enumitem, fancyhdr, tikz, array}
\geometry{margin=2.5cm}
\pgfplotsset{compat=1.18}
\tcbuselibrary{skins, breakable}
```

Define these four tcolorbox environments in the preamble:
- `\newtcolorbox{curiositybox}` — colback=yellow!10, colframe=orange!80
- `\newtcolorbox{infobox}` — colback=blue!5, colframe=blue!60
- `\newtcolorbox{mistakebox}` — colback=red!5, colframe=red!60
- `\newtcolorbox{learnbox}` — colback=green!5, colframe=green!60

fancyhdr:
- `\lhead{Topic 01: Fourier Coefficients (Euler's)}`
- `\rhead{Unit V — Fourier Series \& Transforms}`
- `\cfoot{\thepage}`

lstlisting Python config: basicstyle=\ttfamily\small, keywordstyle=\color{blue}, commentstyle=\color{gray}, stringstyle=\color{orange}, numbers=left, numberstyle=\tiny, breaklines=true, frame=single.

Title: `\title{Topic 01: Fourier Series — Euler's Coefficients \\ \large Unit V — Fourier Series \& Fourier Transforms}`, `\maketitle`, `\tableofcontents`, `\newpage`.

---

## AUDIENCE AND TONE

Intelligent but underconfident B.Tech 2nd-year students. Enthusiastic, conversational, patient teaching voice. Short paragraphs, varied sentence length. Every explanation must feel like a conversation, not a textbook dump.

---

## OPENING HOOK (MANDATORY)

Place inside `\begin{curiositybox}[Hook]`: A violin string vibrating at 440 Hz also vibrates at 880 Hz, 1320 Hz, and other harmonics — all at the same time. The rich, warm sound of a violin versus the thin tone of a flute playing the same note comes down to which harmonics are present and how strong they are. Fourier series is the mathematical tool that tells you exactly how much of each harmonic is hidden inside any periodic signal — from music to electrical waveforms to heat flow in an engine.

---

## REQUIRED SECTIONS

### 1. Why This Topic Exists
"Before we begin, here is the honest answer to why you are reading this..." Explain that any periodic signal in engineering (AC voltage, vibrations, digital clock signals, heat cycles) can be decomposed into a sum of pure sine and cosine waves. Knowing the strength (coefficient) of each frequency component is the basis of signal processing, communications, and structural analysis. Two-column booktabs table:
- "Skipping the orthogonality derivation" | "Unable to explain why the integration formulas for coefficients work"
- "Memorising $a_0$, $a_n$, $b_n$ formulae without understanding" | "Applying wrong limits or wrong period in exam problems"
- "Confusing period 2π with arbitrary period 2L" | "Getting incorrect coefficients for non-standard intervals"
End with a learnbox.

### 2. You Already Know This (Intuition First)
Compare Fourier series to mixing paint: any colour can be made by mixing specific amounts of red, green, and blue. Fourier series decomposes any periodic function into specific amounts of $\cos(nx)$ and $\sin(nx)$ — pure frequency "colours". The Euler formulae tell you exactly how much of each colour to use.

### 3. The Fourier Series Representation
`infobox`: For a function f(x) of period $2\pi$:
$$f(x) = \frac{a_0}{2} + \sum_{n=1}^{\infty}\left[a_n\cos(nx) + b_n\sin(nx)\right]$$
Explain: $a_0/2$ is the average (DC) value; $a_n\cos(nx)$ and $b_n\sin(nx)$ are the nth harmonic components. The series converges to f(x) at points of continuity.

### 4. Orthogonality of Sine and Cosine (The Key Insight)
Derive and present in `infobox` the three orthogonality integrals over $[-\pi,\pi]$:
$$\int_{-\pi}^{\pi}\cos(mx)\cos(nx)\,dx = \begin{cases}0 & m\ne n\\ \pi & m=n\end{cases}$$
$$\int_{-\pi}^{\pi}\sin(mx)\sin(nx)\,dx = \begin{cases}0 & m\ne n\\ \pi & m=n\end{cases}$$
$$\int_{-\pi}^{\pi}\sin(mx)\cos(nx)\,dx = 0 \text{ for all }m,n$$
Explain intuitively: sine and cosine functions at different frequencies are "perpendicular" to each other in the same way that the x- and y-axes are perpendicular in geometry. This perpendicularity is what lets us isolate each coefficient independently.

### 5. Euler's Formulae — Derivation
Derive all three coefficient formulae by multiplying both sides of the Fourier series by $\cos(mx)$ (or $\sin(mx)$ or 1) and integrating over $[-\pi,\pi]$, using the orthogonality results to eliminate all terms except one:
$$a_0 = \frac{1}{\pi}\int_{-\pi}^{\pi}f(x)\,dx$$
$$a_n = \frac{1}{\pi}\int_{-\pi}^{\pi}f(x)\cos(nx)\,dx, \quad n=1,2,3,\ldots$$
$$b_n = \frac{1}{\pi}\int_{-\pi}^{\pi}f(x)\sin(nx)\,dx, \quad n=1,2,3,\ldots$$
Present the full derivation for $a_n$ step by step (the others follow the same pattern). Place in `infobox`.

### 6. Visualising Convergence
**pgfplots graph (MANDATORY):** Plot the square wave $f(x)=1$ for $0<x<\pi$, $f(x)=-1$ for $-\pi<x<0$ alongside its Fourier partial sums $S_1$, $S_3$, $S_5$ (1, 3, 5 terms) on the same axes over $[-\pi,\pi]$. Show visually how each added harmonic brings the sum closer to the square wave, including the Gibbs overshoot at the jump discontinuity. Grid=major, legend, labeled axes.

### 7. Worked Examples

**Example 1:** Find the Fourier series of $f(x) = x$ on $(-\pi, \pi)$, period $2\pi$. Compute $a_0$, $a_n$, $b_n$ using integration by parts where needed. Show the final series and interpret which coefficients vanish and why (odd function — only $b_n$ survive).

**Example 2:** Find the Fourier series of $f(x) = x^2$ on $(-\pi, \pi)$. Compute all three sets of coefficients fully. Use the result to deduce the famous sum $\sum_{n=1}^{\infty}\frac{1}{n^2} = \frac{\pi^2}{6}$ (Parseval's / special value argument — stated briefly, explained as a bonus insight).

**Example 3:** Find the Fourier series of the square wave $f(x)=1$ for $0<x<\pi$, $f(x)=-1$ for $-\pi<x<0$. Identify which coefficients vanish and connect back to the pgfplots graph in Section 6.

All examples inside `infobox`. End each with learnbox.

### 8. Excel Example (MANDATORY)
Numerically compute and verify the first 5 Fourier coefficients of $f(x)=x$ on $(-\pi,\pi)$ using the trapezoidal rule:
- Columns: $x_i$ (from $-\pi$ to $\pi$ in steps of $\pi/10$) | $f(x_i)$ | $f(x_i)\cos(x_i)$ | $f(x_i)\sin(x_i)$ | Cumulative sum
Compare numerical $b_1$ to the exact $b_1=2$ from the derivation. Show cell formulas explicitly.
End with learnbox.

### 9. Python Example (MANDATORY)
Python script using `sympy` and `matplotlib` (described via lstlisting — no actual plot output needed, just the code):
- Symbolically computes $a_0$, $a_n$, $b_n$ for $f(x)=x^2$ using `sympy.integrate`
- Constructs the partial sum $S_N(x)$ for N=1,5,10
- Describes plotting $f(x)$ and $S_N(x)$ using matplotlib to visualise convergence
Include expected printed coefficient values as comments. End with learnbox.

### 10. Viva-Style Oral Questions (8 questions with answers)
Cover: purpose of Fourier series, what $a_0/2$ represents, why orthogonality is the key to deriving the coefficient formulas, statement of Euler's formulas, what happens at a point of discontinuity (Gibbs phenomenon, brief), why some $a_n$ or $b_n$ may be zero for a given function, relationship between period and the integration limits, how Fourier series relates to Laplace transforms (both are integral transforms — different kernels).

### 11. Descriptive Questions (5 exam-style questions)
Derive Euler's formula for $a_n$ from first principles using orthogonality; find the complete Fourier series of a given piecewise function; show that for an odd function all $a_n=0$; deduce a famous series sum using a specific Fourier series result; explain and illustrate the Gibbs phenomenon.

### 12. Practice Problems (6 problems with answer hints)
$f(x)=|x|$, $f(x)=e^x$ on $(-\pi,\pi)$, $f(x)=\pi-x$ for $0<x<2\pi$, a piecewise constant function with two values, $f(x)=x(\pi-x)$, $f(x)=\cos(x/2)$ on $(-\pi,\pi)$.

### 13. MCQs (5 questions)
5 MCQs, bold correct answer, one-line explanation each. Cover: formula for $a_0$, orthogonality result, which coefficient is the average value, period recognition, coefficient of $\cos(2x)$ in a given simple series.

### 14. Common Mistakes Box
`mistakebox` tabular (5 rows): Mistake | What Students Do | Correct Approach.
- Forgetting the $1/\pi$ factor in the coefficient formulas
- Using wrong integration limits (0 to $2\pi$ vs $-\pi$ to $\pi$ — both valid but must be consistent)
- Not using integration by parts when needed for polynomial $\times$ trig integrals
- Assuming $a_n=0$ without checking whether the function is actually even
- Confusing $a_0$ with $a_0/2$ in the series representation

### 15. Quick Recap
`learnbox` with 6–8 bullets: Fourier series representation, Euler's three formulas, orthogonality as the key tool, convergence at continuity/discontinuity points, which coefficients vanish for even/odd functions (preview), connection to harmonics in engineering signals.

---

## MANDATORY QUALITY CHECKLIST

- [ ] Opening hook in `curiositybox`
- [ ] At least 1 pgfplots graph (partial sums convergence) with axis labels, legend, grid
- [ ] At least 1 booktabs table with 5+ rows
- [ ] At least 1 Excel column-by-column numerical example
- [ ] At least 1 Python lstlisting with expected output shown
- [ ] Every major example ends with `learnbox`
- [ ] All four tcolorbox environments used
- [ ] `\end{document}` at end
- [ ] No undefined macros
- [ ] Conversational tone throughout
- [ ] All formulae in correct LaTeX
