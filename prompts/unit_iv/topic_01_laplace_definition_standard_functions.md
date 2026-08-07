# Prompt — Topic 01: Definition & Laplace Transform of Standard Functions

**Unit:** IV — Laplace Transforms
**Course:** 23A54201 — Mathematics IV (Transform Techniques)
**University:** JNTUA College of Engineering (Autonomous)
**Target Audience:** B.Tech 2nd-year engineering students (non-mathematics majors)

---

## Prompt

You are an expert mathematics professor writing a **complete, compilable LaTeX (.tex) lecture note** for B.Tech engineering students on the topic **"Definition & Laplace Transform of Standard Functions"**. This is Topic 01 of Unit IV. Students have completed differential/integral calculus and basic ODEs but have never seen an integral transform before. Write as an enthusiastic, patient teacher who makes students feel the topic is already familiar — just not formally named yet.

---

## LATEX SETUP REQUIREMENTS

Use this exact preamble (add any extra packages needed by the content):

```latex
\documentclass[12pt,a4paper]{article}
\usepackage{amsmath, amssymb, geometry, booktabs, xcolor, hyperref,
            listings, pgfplots, tcolorbox, enumitem, fancyhdr, tikz, array}
\geometry{margin=2.5cm}
\pgfplotsset{compat=1.18}
\tcbuselibrary{skins, breakable}
```

Define these four tcolorbox environments in the preamble:
- `\newtcolorbox{curiositybox}` — colback=yellow!10, colframe=orange!80 (for hooks and "why?" questions)
- `\newtcolorbox{infobox}` — colback=blue!5, colframe=blue!60 (for key definitions and formulae)
- `\newtcolorbox{mistakebox}` — colback=red!5, colframe=red!60 (for common mistakes)
- `\newtcolorbox{learnbox}` — colback=green!5, colframe=green!60 (for "What Did We Learn?" summaries)

Set up fancyhdr with:
- `\lhead{Topic 01: Laplace Definition \& Standard Functions}`
- `\rhead{Unit IV — Laplace Transforms}`
- `\cfoot{\thepage}`

Configure lstlisting for Python:
```
basicstyle=\ttfamily\small, keywordstyle=\color{blue},
commentstyle=\color{gray}, stringstyle=\color{orange},
numbers=left, numberstyle=\tiny, breaklines=true, frame=single
```

Title page: `\title{Topic 01: Definition \& Laplace Transform of Standard Functions \\ \large Unit IV — Laplace Transforms}`, `\maketitle`, then `\tableofcontents`, then `\newpage`.

---

## AUDIENCE AND TONE

- Students are intelligent but underconfident B.Tech 2nd-year students, many anxious about "abstract" transform mathematics.
- Write like an enthusiastic, patient teacher who genuinely enjoys this topic.
- Use active, energetic language: "Let's find out", "Here is the surprise:", "You already know this — you just haven't called it that."
- Keep paragraphs short. Vary sentence length. Avoid walls of text.
- Every explanation must feel like a conversation, not a textbook dump.

---

## OPENING HOOK (MANDATORY)

Place inside `\begin{curiositybox}[Hook]`: An electrical engineer needs to solve a differential equation describing a circuit with a switch that turns on at t=0. Solving it directly with calculus is messy — integration constants pile up and initial conditions get lost in the algebra. But what if there was a machine that turns *any* calculus problem into a plain algebra problem? That machine exists. It is called the Laplace Transform, and by the end of this topic you will know exactly how it works.

---

## REQUIRED SECTIONS

### 1. Why This Topic Exists
Open with: "Before we begin, here is the honest answer to why you are reading this..."
Explain that ODEs with initial conditions are hard to solve directly, especially with discontinuous or delayed inputs (common in circuits and control systems). The Laplace Transform converts calculus into algebra. Two-column booktabs table:
- "Skipping the definition step" | "Not recognising when a transform is valid or how it was derived"
- "Memorising formulas without the integral" | "Failing to derive transforms of new functions in exams"
- "Confusing transform variable s with time t" | "Writing F(t) or f(s) — completely wrong notation"
End with a learnbox.

### 2. You Already Know This (Intuition First)
Compare the Laplace Transform to converting currency: money in Rupees (time domain) vs Dollars (s-domain) — the *value* is preserved, just expressed differently, and some operations (like tax calculations) are easier in one currency than the other. Similarly, differentiation in t-domain becomes simple multiplication in s-domain.

### 3. Definition of the Laplace Transform
- Present in `infobox`:
$$\mathcal{L}\{f(t)\} = F(s) = \int_0^\infty e^{-st} f(t)\, dt, \quad s > 0$$
- Explain each piece: f(t) is the original function (time domain), F(s) is the transform (s-domain), e^{-st} is the "damping kernel" that makes the improper integral converge.
- Emphasize notation: lowercase for time domain, uppercase for s-domain (f(t) ↔ F(s)).
- Explain that this is a **linear operator**: $\mathcal{L}\{af(t) + bg(t)\} = aF(s) + bG(s)$. Prove linearity directly from the integral definition.

### 4. Laplace Transform of Standard Functions (Derivations)
Derive each of the following step-by-step from the definition, inside `infobox` blocks:
- $\mathcal{L}\{1\} = 1/s$
- $\mathcal{L}\{t^n\} = n!/s^{n+1}$ (use integration by parts / Gamma function connection)
- $\mathcal{L}\{e^{at}\} = 1/(s-a)$, valid for s > a
- $\mathcal{L}\{\sin(at)\} = a/(s^2+a^2)$
- $\mathcal{L}\{\cos(at)\} = s/(s^2+a^2)$
- $\mathcal{L}\{\sinh(at)\} = a/(s^2-a^2)$
- $\mathcal{L}\{\cosh(at)\} = s/(s^2-a^2)$
Provide a consolidated booktabs table of all 7 transforms with validity conditions on s (5+ rows).

### 5. Visualizing the Transform
**pgfplots graph (MANDATORY):** Plot f(t) = e^{-2t} in the time domain on one set of axes, and its transform F(s) = 1/(s+2) on a second set of axes (side-by-side using subfigure or two separate tikzpicture/axis environments). Label axes clearly, grid=major. Add a caption explaining that F(s) is not a "graph of the same shape" — it lives in a completely different domain.

### 6. Worked Examples

**Example 1:** Find $\mathcal{L}\{5t^3 - 3\cos(2t) + 4e^{-t}\}$ using linearity and the standard table. Show full step-by-step substitution.
**Example 2:** Derive $\mathcal{L}\{t^2\}$ directly from the integral definition using integration by parts twice (do not just quote the formula).
**Example 3:** Find $\mathcal{L}\{\sin^2(t)\}$ by first rewriting using the identity $\sin^2 t = \frac{1-\cos 2t}{2}$, then applying linearity.

All examples inside `infobox`. End each with `learnbox` titled "What Did We Learn?".

### 7. Excel Example (MANDATORY)
Show a column-by-column numerical verification that the improper integral for $\mathcal{L}\{e^{-2t}\}$ at s=5 approximately equals 1/7:
- Columns: t | e^{-5t} \cdot e^{-2t} | Cumulative Trapezoid Area
- Formulas: `=EXP(-5*A2)*EXP(-2*A2)`, trapezoidal rule formula for cumulative integral approximation up to t=10
End with learnbox comparing numerical approximation to exact value 1/7.

### 8. Python Example (MANDATORY)
Provide a clean Python script using `sympy` that:
- Symbolically computes the Laplace transform of t**3, sin(2*t), and exp(-3*t)*cos(t) using `sympy.laplace_transform`
- Prints each result in closed form
Include expected printed output as comments. End with learnbox.

### 9. Viva-Style Oral Questions (8 questions with answers)
Cover: what makes the integral improper, why e^{-st} is needed for convergence, what linearity means, difference between f(t) and F(s), why n! appears in $\mathcal{L}\{t^n\}$, condition s>a for exponential transform, what happens if s ≤ 0, relationship between sinh/cosh and exponential transforms.

### 10. Descriptive Questions (5 exam-style questions)
Full written-answer questions: derive $\mathcal{L}\{\cos(at)\}$ from definition, state and prove linearity property, derive $\mathcal{L}\{t^n\}$ using reduction formula, explain the role of the convergence parameter s, find transform of a piecewise-defined function using the definition directly.

### 11. Practice Problems (6 problems with answer hints)
Numerical problems covering: transforms of polynomial combinations, exponential-trig products (state only, to be solved fully in Topic 04), hyperbolic functions, and a direct-integration problem.

### 12. MCQs (5 questions)
5 MCQs with 4 options each. Bold the correct answer. One-line explanation for each. Cover: definition validity condition, standard transform values, linearity, notation conventions.

### 13. Common Mistakes Box
`mistakebox` tabular (5 rows): Mistake | What Students Do | Correct Approach.
- Forgetting the validity condition on s
- Writing F(t) instead of F(s)
- Treating $\mathcal{L}\{f(t)g(t)\}$ as $F(s)G(s)$ (it is NOT, in general)
- Sign errors in exponential transforms
- Forgetting n! in the t^n formula

### 14. Quick Recap
`learnbox` with 6–8 bullets: definition formula, linearity property, all 7 standard transforms, validity conditions, notation convention.

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
