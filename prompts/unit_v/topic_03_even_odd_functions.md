# Prompt — Topic 03: Fourier Series of Even and Odd Functions

**Unit:** V — Fourier Series and Fourier Transforms
**Course:** 23A54201 — Mathematics IV (Transform Techniques)
**University:** JNTUA College of Engineering (Autonomous)
**Target Audience:** B.Tech 2nd-year engineering students (non-mathematics majors)

---

## Prompt

You are an expert mathematics professor writing a **complete, compilable LaTeX (.tex) lecture note** for B.Tech engineering students on the topic **"Fourier Series of Even and Odd Functions"**. This is Topic 03 of Unit V. Students can compute general Fourier coefficients; now they learn a powerful symmetry shortcut that cuts computation in half for symmetric functions — which happen to be the most common functions in engineering. Write as an enthusiastic, patient teacher who makes students feel the topic is already familiar — just not formally named yet.

---

## LATEX SETUP REQUIREMENTS

Same preamble structure as previous topics (four tcolorbox environments, pgfplots, listings).

fancyhdr:
- `\lhead{Topic 03: Even and Odd Functions}`
- `\rhead{Unit V — Fourier Series \& Transforms}`
- `\cfoot{\thepage}`

Title: `\title{Topic 03: Fourier Series of Even and Odd Functions \\ \large Unit V — Fourier Series \& Fourier Transforms}`, `\maketitle`, `\tableofcontents`, `\newpage`.

---

## AUDIENCE AND TONE

Same conversational, enthusiastic tone.

---

## OPENING HOOK (MANDATORY)

`\begin{curiositybox}[Hook]`: When you compute the Fourier series of $f(x)=x^2$ on $(-\pi,\pi)$, you spend 15 minutes integrating to find $b_n$ — and they ALL turn out to be zero. Every single one. Was that time wasted? Yes, completely — and it didn't have to be. If you had noticed that $x^2$ is an EVEN function (symmetric about the y-axis), you could have declared $b_n=0$ in three seconds without touching a single integral. That's the power of symmetry.

---

## REQUIRED SECTIONS

### 1. Why This Topic Exists
"Before we begin, here is the honest answer to why you are reading this..." Explain that recognising even/odd symmetry before integrating halves the computation effort and eliminates entire sets of coefficients immediately. Two-column booktabs table:
- "Computing all coefficients without checking symmetry" | "Wasting exam time on integrals that are provably zero"
- "Confusing even/odd function definition" | "Wrongly declaring all $a_n=0$ for an even function"
- "Forgetting symmetry only applies to symmetric intervals" | "Applying even/odd shortcuts on non-symmetric domains"
End with a learnbox.

### 2. You Already Know This (Intuition First)
Compare to balancing a see-saw: an even function is perfectly symmetric about the y-axis (like a see-saw perfectly balanced) — all its Fourier "weight" sits on the cosine (symmetric) side; none on the sine (antisymmetric) side. An odd function is the exact opposite: it tilts one way on the left and the opposite way on the right — all weight on the sine side.

### 3. Definitions: Even and Odd Functions
`infobox`:
- **Even function:** $f(-x)=f(x)$ for all $x$. Graph is symmetric about the y-axis. Examples: $\cos(x)$, $x^2$, $|x|$.
- **Odd function:** $f(-x)=-f(x)$ for all $x$. Graph has 180° rotational symmetry about the origin. Examples: $\sin(x)$, $x$, $x^3$.
- Key integral property: $\int_{-a}^{a}(\text{odd})\,dx = 0$; $\int_{-a}^{a}(\text{even})\,dx = 2\int_0^a (\text{even})\,dx$.

**pgfplots graph (MANDATORY):** Two subplots side by side — left: plot of $f(x)=x^2$ (even, symmetric) and $f(x)=x$ (odd, antisymmetric) on $[-\pi,\pi]$. Label each clearly. Grid=major, labeled axes.

### 4. Fourier Series of Even Functions
Derive in `infobox`: if f(x) is even on $(-\pi,\pi)$, then:
- $b_n = 0$ for all $n$ (because $f(x)\sin(nx)$ is odd $\times$ odd = even... wait, actually odd: even $\times$ odd = odd — show this explicitly, integral of odd over symmetric interval = 0)
- $a_n = \frac{2}{\pi}\int_0^{\pi}f(x)\cos(nx)\,dx$
- $a_0 = \frac{2}{\pi}\int_0^{\pi}f(x)\,dx$
So the Fourier series of an even function is a **pure cosine series**: $f(x) = \frac{a_0}{2} + \sum_{n=1}^\infty a_n\cos(nx)$.

### 5. Fourier Series of Odd Functions
Derive analogously: if f(x) is odd on $(-\pi,\pi)$, then:
- $a_n = 0$ for all $n$ (including $a_0$) — because $f(x)\cos(nx)$ = odd $\times$ even = odd
- $b_n = \frac{2}{\pi}\int_0^{\pi}f(x)\sin(nx)\,dx$
So the Fourier series of an odd function is a **pure sine series**: $f(x) = \sum_{n=1}^\infty b_n\sin(nx)$.

### 6. Quick-Identification Table
Booktabs table (7+ rows): Function | Even/Odd/Neither | Which coefficients vanish | Resulting series type.
Include: $x$, $x^2$, $x^3$, $|x|$, $\cos(x)$, $\sin(x)$, $e^x$, a piecewise square wave.

### 7. Products of Even/Odd Functions
`infobox` mini-table:
- Even $\times$ Even = Even
- Odd $\times$ Odd = Even
- Even $\times$ Odd = Odd
Explain why this matters: this is exactly the rule used to determine which integrals vanish in the coefficient formulas.

### 8. Worked Examples

**Example 1:** Find the Fourier series of $f(x)=x^2$ on $(-\pi,\pi)$. First identify symmetry (even) — declare $b_n=0$ immediately. Compute only $a_0$ and $a_n$ using the simplified even-function formula. Show the full series and use it to derive $\sum 1/n^2 = \pi^2/6$ (putting $x=\pi$).

**Example 2:** Find the Fourier series of $f(x)=x$ on $(-\pi,\pi)$. Identify symmetry (odd) — declare $a_0=a_n=0$ immediately. Compute only $b_n$. Show the result $f(x)=2\sum_{n=1}^\infty \frac{(-1)^{n+1}}{n}\sin(nx)$.

**Example 3:** Determine whether $f(x) = x + x^2$ is even, odd, or neither on $(-\pi,\pi)$. Show it is neither, split it as (even part) + (odd part), and use linearity to write the full Fourier series from Examples 1 and 2 combined.

All examples in `infobox`. End each with learnbox.

### 9. Excel Example (MANDATORY)
Verify that $b_n=0$ for $f(x)=x^2$ numerically by computing $\frac{1}{\pi}\int_{-\pi}^{\pi}x^2\sin(nx)dx$ using trapezoidal rule for n=1,2,3,4:
- Columns: $x_i$ | $x_i^2$ | $x_i^2\sin(x_i)$ | $x_i^2\sin(2x_i)$ | ...
Show all values are (approximately) zero, confirming the symmetry rule.
End with learnbox.

### 10. Python Example (MANDATORY)
Python script using `sympy`:
- Checks whether given functions are even or odd using `sympy.simplify(f(-x) - f(x))` and `sympy.simplify(f(-x) + f(x))`
- Computes Fourier series for $f(x)=x^2$ and $f(x)=x$ symbolically
- Prints which coefficients are zero and which are nonzero
Include expected printed output as comments. End with learnbox.

### 11. Viva-Style Oral Questions (8 questions with answers)
Cover: definitions of even and odd functions, which coefficients vanish for each, why (even $\times$ odd = odd integral = 0), the product rules, what happens for a function that is neither even nor odd, how to split any function into even+odd parts ($f_e = (f(x)+f(-x))/2$, $f_o = (f(x)-f(-x))/2$), physical interpretation of pure cosine vs pure sine series.

### 12. Descriptive Questions (5 exam-style questions)
Derive that $b_n=0$ for even functions; find the Fourier cosine series of $|x|$; find the Fourier sine series of $x^3$; split $e^x$ into even+odd parts and write the Fourier series using cosh/sinh forms; explain the physical significance of a pure cosine vs pure sine series for a mechanical vibration.

### 13. Practice Problems (6 problems)
$f(x)=|\sin(x)|$ (even), $f(x)=x|x|$ (odd), $f(x)=x^4-x^2$, $f(x)=e^{|x|}$, a piecewise symmetric function, a piecewise antisymmetric function.

### 14. MCQs (5 questions)
Cover: even/odd identification, which coefficients vanish, product rule, correct formula simplification for even function.

### 15. Common Mistakes Box
`mistakebox` tabular (5 rows):
- Computing $b_n$ integrals for a clearly even function
- Applying even/odd shortcuts to non-symmetric interval $[0,2\pi]$
- Confusing "even function" with "even-indexed $n$"
- Forgetting $a_0=0$ for odd functions
- Claiming $f(x)=x+1$ is odd because $x$ is odd

### 16. Quick Recap
`learnbox` 6–8 bullets: even/odd definitions, key integral properties, Fourier series of even = pure cosine, Fourier series of odd = pure sine, product rules, even+odd decomposition of any function, computational savings.

---

## MANDATORY QUALITY CHECKLIST

- [ ] Opening hook in `curiositybox`
- [ ] pgfplots comparing even vs odd function graphs
- [ ] Booktabs identification table (7+ rows)
- [ ] Excel numerical verification of zero $b_n$ for even function
- [ ] Python symmetry-checking and coefficient script
- [ ] Every major example ends with `learnbox`
- [ ] All four tcolorbox environments used
- [ ] `\end{document}` at end
- [ ] Conversational tone throughout
