# Prompt — Topic 04: First Shifting Theorem

**Unit:** IV — Laplace Transforms
**Course:** 23A54201 — Mathematics IV (Transform Techniques)
**University:** JNTUA College of Engineering (Autonomous)
**Target Audience:** B.Tech 2nd-year engineering students (non-mathematics majors)

---

## Prompt

You are an expert mathematics professor writing a **complete, compilable LaTeX (.tex) lecture note** for B.Tech engineering students on the topic **"First Shifting Theorem"**. This is Topic 04 of Unit IV. Students can find standard transforms and their inverses; now they learn a shortcut theorem that instantly handles ANY function multiplied by an exponential — without repeating a full integral derivation each time. Write as an enthusiastic, patient teacher who makes students feel the topic is already familiar — just not formally named yet.

---

## LATEX SETUP REQUIREMENTS

Same exact preamble structure as previous topics.

Set up fancyhdr with:
- `\lhead{Topic 04: First Shifting Theorem}`
- `\rhead{Unit IV — Laplace Transforms}`
- `\cfoot{\thepage}`

Title page: `\title{Topic 04: First Shifting Theorem \\ \large Unit IV — Laplace Transforms}`, `\maketitle`, `\tableofcontents`, `\newpage`.

---

## AUDIENCE AND TONE

Same conversational, enthusiastic tone as previous topics.

---

## OPENING HOOK (MANDATORY)

Place inside `\begin{curiositybox}[Hook]`: You already know $\mathcal{L}\{\sin(3t)\}$ from the table. But what about $\mathcal{L}\{e^{5t}\sin(3t)\}$ — an exponentially growing oscillation, common in unstable circuits and resonance problems? Do you need to redo the entire integral from scratch? Absolutely not. There is a one-line shortcut: just shift s by 5. That's the whole theorem. Let's see why it works and how powerful it really is.

---

## REQUIRED SECTIONS

### 1. Why This Topic Exists
"Before we begin, here is the honest answer to why you are reading this..." Explain that many practical signals are pure functions (sin, cos, t^n) multiplied by an exponential envelope (decay or growth) — re-deriving each from the integral is wasteful when a shift rule handles all of them instantly. Two-column booktabs table:
- "Re-deriving transform from scratch for e^{at}f(t)" | "Wasting exam time on integration that a one-line shift avoids"
- "Shifting s in the wrong direction" | "Getting F(s+a) instead of F(s-a) or vice versa"
- "Forgetting the theorem applies to inverse transforms too" | "Being unable to invert F(s-a) forms"
End with a learnbox.

### 2. You Already Know This (Intuition First)
Compare to adjusting a thermostat: shifting the entire temperature scale by a constant amount doesn't change the *shape* of the temperature graph, just its reference point. Multiplying f(t) by $e^{at}$ in the time domain has the exact parallel effect of simply shifting the s-axis reference point in the transform domain — same shape function F, evaluated at $(s-a)$ instead of $s$.

### 3. Statement of the First Shifting Theorem
`infobox`:
$$\text{If } \mathcal{L}\{f(t)\}=F(s), \text{ then } \mathcal{L}\{e^{at}f(t)\} = F(s-a)$$
Inverse form: $\mathcal{L}^{-1}\{F(s-a)\} = e^{at}f(t)$.

### 4. Proof of the Theorem
Derive directly from the definition:
$$\mathcal{L}\{e^{at}f(t)\} = \int_0^\infty e^{-st}e^{at}f(t)\,dt = \int_0^\infty e^{-(s-a)t}f(t)\,dt = F(s-a)$$
Show every algebraic step explicitly — emphasize this is literally combining the two exponentials into one before recognizing the standard definition pattern with s replaced by (s-a).

### 5. Building New Transforms Using the Theorem
Derive using the theorem (not from scratch):
- $\mathcal{L}\{e^{at}t^n\} = n!/(s-a)^{n+1}$
- $\mathcal{L}\{e^{at}\sin(bt)\} = b/((s-a)^2+b^2)$
- $\mathcal{L}\{e^{at}\cos(bt)\} = (s-a)/((s-a)^2+b^2)$
Booktabs table (5+ rows) consolidating these shifted forms alongside their unshifted originals from Topic 01.

### 6. Visualizing the Shift
**pgfplots graph (MANDATORY):** Plot $f(t)=\sin(3t)$ and $g(t)=e^{2t}\sin(3t)$ on the same time-domain axes over $t\in[0,3]$, showing how the exponential envelope amplifies the oscillation. Grid=major, legend distinguishing the two curves, labeled axes.

### 7. Worked Examples

**Example 1 (forward):** Find $\mathcal{L}\{e^{3t}\cos(4t)\}$ using the shifting theorem directly, substituting into the table entry.
**Example 2 (forward, polynomial):** Find $\mathcal{L}\{t^2e^{-2t}\}$ using the theorem applied to $\mathcal{L}\{t^2\}=2/s^3$.
**Example 3 (inverse application):** Find $\mathcal{L}^{-1}\left\{\frac{s+2}{(s+2)^2+9}\right\}$, recognizing this as a shifted cosine form (connect back to completing-the-square skill from Topic 03).

All examples inside `infobox`. End each with learnbox.

### 8. Excel Example (MANDATORY)
Numerically verify Example 1 by computing the transform integral $\int_0^{T} e^{-st}e^{3t}\cos(4t)\,dt$ using trapezoidal approximation at a fixed large s and comparing to the closed-form theorem result:
- Columns: t | Integrand value | Cumulative trapezoid area
End with learnbox.

### 9. Python Example (MANDATORY)
Python script using `sympy` that:
- Symbolically verifies $\mathcal{L}\{e^{at}f(t)\}=F(s-a)$ for $f(t)=t^2$ and $f(t)=\sin(3t)$ using `sympy.laplace_transform`
- Compares the symbolic result to manually substituting $(s-a)$ into $F(s)$
Include expected printed output as comments. End with learnbox.

### 10. Viva-Style Oral Questions (8 questions with answers)
Cover: statement of the theorem, one-line proof idea, why it's called "first" shifting (contrast implied with second shifting later), direction of shift (s-a not s+a), how it builds new table entries, its inverse form, example of when it's used in circuit analysis (exponentially damped oscillation), relationship to completing the square in Topic 03.

### 11. Descriptive Questions (5 exam-style questions)
Derive and prove the theorem from the definition; derive $\mathcal{L}\{e^{at}t^n\}$ using the theorem; solve an inverse problem requiring completing the square and shift recognition; explain physical meaning of exponential shift in engineering signals; compare direct-integral derivation effort vs. theorem-based derivation for the same function.

### 12. Practice Problems (6 problems with answer hints)
Forward transforms of $e^{2t}t^3$, $e^{-t}\sin(2t)$, $e^{4t}\cosh(t)$; inverse transforms of two shifted rational forms; one combined forward+inverse round-trip problem.

### 13. MCQs (5 questions)
5 MCQs, bold correct answer, one-line explanation. Cover: theorem statement recognition, correct shift direction, table entry identification, inverse-application recognition.

### 14. Common Mistakes Box
`mistakebox` tabular (5 rows): Mistake | What Students Do | Correct Approach.
- Shifting in wrong direction (using s+a instead of s-a)
- Forgetting theorem applies to inverse transforms as well
- Not completing the square before applying inverse shift recognition
- Confusing this theorem with the second shifting theorem (Topic 06)
- Applying the theorem to a function that isn't purely $e^{at}f(t)$ form

### 15. Quick Recap
`learnbox` with 6–8 bullets: theorem statement, proof idea, forward table extensions, inverse application, direction of shift, distinction from second shifting theorem (preview).

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
