# Prompt — Topic 06: Unit Step Function & Second Shifting Theorem

**Unit:** IV — Laplace Transforms
**Course:** 23A54201 — Mathematics IV (Transform Techniques)
**University:** JNTUA College of Engineering (Autonomous)
**Target Audience:** B.Tech 2nd-year engineering students (non-mathematics majors)

---

## Prompt

You are an expert mathematics professor writing a **complete, compilable LaTeX (.tex) lecture note** for B.Tech engineering students on the topic **"Unit Step Function & Second Shifting Theorem"**. This is Topic 06 of Unit IV. Students can transform derivatives and solve basic ODEs; now they learn how to handle switched, delayed, or piecewise inputs — essential for real circuits with switches and control systems with delayed triggers. Write as an enthusiastic, patient teacher who makes students feel the topic is already familiar — just not formally named yet.

---

## LATEX SETUP REQUIREMENTS

Same exact preamble structure as previous topics.

Set up fancyhdr with:
- `\lhead{Topic 06: Unit Step \& Second Shifting}`
- `\rhead{Unit IV — Laplace Transforms}`
- `\cfoot{\thepage}`

Title page: `\title{Topic 06: Unit Step Function \& Second Shifting Theorem \\ \large Unit IV — Laplace Transforms}`, `\maketitle`, `\tableofcontents`, `\newpage`.

---

## AUDIENCE AND TONE

Same conversational, enthusiastic tone as previous topics.

---

## OPENING HOOK (MANDATORY)

Place inside `\begin{curiositybox}[Hook]`: Imagine a light switch that stays OFF until exactly t=5 seconds, then suddenly turns ON and stays on forever. How do you even write this function mathematically without drawing a picture? Enter the unit step function — a mathematical "switch" that turns terms on and off at will. And once you can write delayed functions, the Second Shifting Theorem tells you exactly how to transform them, no re-derivation needed.

---

## REQUIRED SECTIONS

### 1. Why This Topic Exists
"Before we begin, here is the honest answer to why you are reading this..." Explain that real engineering signals often switch on/off or get delayed (circuit switches, delayed control signals, impulse triggers) and ordinary functions cannot express this behaviour compactly without the unit step function. Two-column booktabs table:
- "Writing piecewise functions the long way" | "Struggling to find their Laplace transform at all"
- "Confusing u(t-a) with u(t)-a" | "Getting the delay condition completely wrong"
- "Forgetting to shift f(t) itself, not just u(t-a)" | "Applying the second shifting theorem incorrectly"
End with a learnbox.

### 2. You Already Know This (Intuition First)
Compare to a stage light that stays off, then a stagehand flips a switch at a scheduled cue time and the light turns on and stays on. The unit step function u(t-a) is exactly that switch, scheduled to flip at time t=a.

### 3. The Unit Step (Heaviside) Function
`infobox` definition:
$$u(t-a) = \begin{cases}0, & t<a\\1,& t\ge a\end{cases}$$
**pgfplots graph (MANDATORY):** Plot u(t-3) over $t\in[0,6]$ clearly showing the jump from 0 to 1 at t=3 with an open/filled circle convention noted. Grid=major, labeled axes.

### 4. Laplace Transform of the Unit Step Function
Derive directly from the definition:
$$\mathcal{L}\{u(t-a)\} = \int_a^\infty e^{-st}\,dt = \frac{e^{-as}}{s}$$
Show the integral limits change to start at a (since u(t-a)=0 before a) and the direct evaluation.

### 5. Writing Piecewise Functions Using Unit Steps
Show the technique: any piecewise function can be written as a sum of terms multiplied by unit steps that "turn on" the right piece at the right time. Worked demonstration: express $f(t) = \begin{cases}t^2, & 0\le t<2\\5, & t\ge 2\end{cases}$ as $f(t) = t^2 + (5-t^2)u(t-2)$, verifying by checking both regions.

### 6. Second Shifting Theorem
`infobox`:
$$\text{If }\mathcal{L}\{f(t)\}=F(s), \text{ then } \mathcal{L}\{f(t-a)u(t-a)\} = e^{-as}F(s)$$
Inverse form: $\mathcal{L}^{-1}\{e^{-as}F(s)\} = f(t-a)u(t-a)$.

### 7. Proof of the Second Shifting Theorem
Derive from the definition: $\int_0^\infty e^{-st}f(t-a)u(t-a)\,dt = \int_a^\infty e^{-st}f(t-a)\,dt$ (since u(t-a)=0 before a), then substitute $\tau=t-a$, giving $\int_0^\infty e^{-s(\tau+a)}f(\tau)\,d\tau = e^{-as}\int_0^\infty e^{-s\tau}f(\tau)\,d\tau = e^{-as}F(s)$.

### 8. Contrast: First vs. Second Shifting Theorem
Booktabs table (5+ rows) comparing: what is shifted (s-domain vs t-domain), the formula, the multiplying factor, typical use case, example function — for First Shifting Theorem (Topic 04) vs Second Shifting Theorem (this topic).

### 9. Worked Examples

**Example 1 (forward, direct application):** Find $\mathcal{L}\{(t-2)^2u(t-2)\}$ using the second shifting theorem directly.
**Example 2 (forward, requires rewriting):** Find $\mathcal{L}\{t^2u(t-2)\}$ — note this is NOT directly in $f(t-a)$ form, so rewrite $t^2$ in terms of $(t-2)$ first: $t^2 = ((t-2)+2)^2$, expand, then apply the theorem term by term.
**Example 3 (inverse application):** Find $\mathcal{L}^{-1}\left\{\frac{e^{-3s}}{s^2+4}\right\}$ using the inverse form of the theorem.
**Example 4 (switched circuit ODE):** Solve $y'+y = u(t-1)$, $y(0)=0$, modeling a switch that activates at t=1, using the full Laplace method combined with the second shifting theorem for the final inverse step.

All examples inside `infobox`. End each with learnbox.

### 10. Excel Example (MANDATORY)
Numerically verify Example 1 by tabulating $f(t-2)u(t-2)$ values for t=0 to 6 and confirming the function is 0 before t=2 and matches $(t-2)^2$ after:
- Columns: t | u(t-2) | (t-2)^2 | f(t)=(t-2)^2\cdot u(t-2)
End with learnbox.

### 11. Python Example (MANDATORY)
Python script using `sympy` that:
- Defines a piecewise function using `sympy.Heaviside` and `sympy.Piecewise`
- Computes its Laplace transform using `sympy.laplace_transform` and compares to the manual second-shifting-theorem result
Include expected printed output as comments. End with learnbox.

### 12. Viva-Style Oral Questions (8 questions with answers)
Cover: definition of u(t-a), Laplace transform of u(t-a), statement of second shifting theorem, why f(t) must be rewritten in terms of (t-a) before applying the theorem, difference from first shifting theorem, how piecewise functions are compactly written, physical meaning in switched circuits, inverse application recognition (spotting $e^{-as}$ factor).

### 13. Descriptive Questions (5 exam-style questions)
Derive the Laplace transform of u(t-a) from definition; prove the second shifting theorem; solve a piecewise-function transform problem requiring rewriting in (t-a) form; solve an ODE with a switched forcing function fully; explain the difference between first and second shifting theorems with an example each.

### 14. Practice Problems (6 problems with answer hints)
Two direct forward applications, two requiring function rewriting in (t-a) form, two inverse applications recognizing $e^{-as}$ factors.

### 15. MCQs (5 questions)
5 MCQs, bold correct answer, one-line explanation. Cover: u(t-a) definition, transform formula, second shifting theorem recognition, distinguishing from first shifting theorem.

### 16. Common Mistakes Box
`mistakebox` tabular (5 rows): Mistake | What Students Do | Correct Approach.
- Applying the theorem to f(t) directly without rewriting in terms of (t-a)
- Confusing u(t-a) with u(t)−a
- Forgetting the $e^{-as}$ factor when transforming a delayed function
- Mixing up first and second shifting theorems
- Sign errors in the substitution $\tau=t-a$

### 17. Quick Recap
`learnbox` with 6–8 bullets: unit step definition and transform, second shifting theorem statement and inverse form, technique for rewriting functions before applying it, contrast with first shifting theorem, use in switched-system ODEs.

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
