# Prompt — Topic 08: Convolution Theorem for Fourier Transforms

**Unit:** V — Fourier Series and Fourier Transforms
**Course:** 23A54201 — Mathematics IV (Transform Techniques)
**University:** JNTUA College of Engineering (Autonomous)
**Target Audience:** B.Tech 2nd-year engineering students (non-mathematics majors)

---

## Prompt

You are an expert mathematics professor writing a **complete, compilable LaTeX (.tex) lecture note** for B.Tech engineering students on the topic **"Convolution Theorem for Fourier Transforms"**. This is Topic 08 (the final topic) of Unit V. Students have just mastered the Fourier transform, its sine/cosine variants, properties, and inverse transforms (Topic 07); now they learn the single most powerful property that makes the Fourier transform indispensable in signal processing and systems theory. Write as an enthusiastic, patient teacher who makes students feel the topic is already familiar — just not formally named yet.

---

## LATEX SETUP REQUIREMENTS

Same preamble structure as previous topics (four tcolorbox environments, pgfplots, listings).

fancyhdr:
- `\lhead{Topic 08: Convolution Theorem (FT)}`
- `\rhead{Unit V — Fourier Series \& Transforms}`
- `\cfoot{\thepage}`

Title: `\title{Topic 08: Convolution Theorem for Fourier Transforms \\ \large Unit V — Fourier Series \& Fourier Transforms}`, `\maketitle`, `\tableofcontents`, `\newpage`.

---

## AUDIENCE AND TONE

Same conversational, enthusiastic tone as all prior topics.

---

## OPENING HOOK (MANDATORY)

`\begin{curiositybox}[Hook]`: An audio engineer wants to add studio-quality reverb to a dry vocal recording. Doing this directly means sliding the recording against a "room response" signal and summing overlapping products at every time shift — a slow, expensive operation called convolution. But there is a shortcut: transform both signals into the frequency domain, multiply them point-by-point (instant), and transform back. This one shortcut — the Convolution Theorem — is why every digital reverb, equalizer, and image-blur filter on your phone runs in real time instead of taking minutes.

---

## REQUIRED SECTIONS

### 1. Why This Topic Exists
"Before we begin, here is the honest answer to why you are reading this..." Explain that convolution in the time domain — combining two signals or solving linear systems with arbitrary inputs — is computationally expensive as a direct integral, but becomes simple multiplication in the frequency domain. This is the single biggest reason engineers move to the frequency domain at all. Two-column booktabs table:
- "Confusing Fourier convolution with Laplace convolution" | "Using the one-sided $[0,\infty)$ formula for a problem defined on $(-\infty,\infty)$"
- "Forgetting the $\sqrt{2\pi}$ or $2\pi$ normalisation factor" | "Getting an answer off by a constant multiple"
- "Treating convolution as ordinary multiplication of functions" | "Computing $f(t)g(t)$ instead of the sliding integral $\int f(\tau)g(t-\tau)d\tau$"
End with learnbox.

### 2. You Already Know This (Intuition First)
Compare convolution to blending two ink drops spreading through water: at each instant, the resulting shade at any point is a weighted sum of all the ways the two drops' influences overlap as one "slides past" the other. Just like the Laplace convolution theorem converted a hard integral into simple multiplication in the s-domain, the Fourier convolution theorem does the same in the $\omega$-domain — but now for two-sided, non-causal signals.

### 3. Definition: Convolution of Two Functions
`infobox`:
$$(f * g)(t) = \int_{-\infty}^{\infty} f(\tau)\,g(t-\tau)\,d\tau$$
Explain the sliding/flipping interpretation geometrically: flip $g$, slide it across $f$, and at each shift $t$ compute the overlap area. Contrast explicitly with the Laplace convolution $\int_0^t f(\tau)g(t-\tau)d\tau$ (one-sided, causal) — emphasise the different limits of integration and when each applies.

### 4. Statement of the Convolution Theorem
`infobox`:
$$\mathcal{F}\{f*g\}(\omega) = F(\omega)\cdot G(\omega)$$
And its dual (multiplication theorem):
$$\mathcal{F}\{f(t)\cdot g(t)\}(\omega) = \frac{1}{2\pi}(F*G)(\omega)$$
State clearly: convolution in time domain = multiplication in frequency domain, and vice versa (up to the $1/2\pi$ factor). Note that the exact constant depends on which FT normalisation convention is used — flag this explicitly since Topic 07 already warned about convention differences.

### 5. Proof of the Convolution Theorem
Give a full, step-by-step proof starting from $\mathcal{F}\{f*g\}(\omega) = \int_{-\infty}^\infty\left[\int_{-\infty}^\infty f(\tau)g(t-\tau)d\tau\right]e^{-i\omega t}dt$, swap order of integration (justify briefly via Fubini/absolute integrability), substitute $u = t-\tau$, and separate into the product $F(\omega)G(\omega)$. Place in `infobox`, numbered steps.

### 6. Convolution Theorem for Fourier Sine and Cosine Transforms
Briefly state the analogous (more intricate) convolution results for $F_s$ and $F_c$ using the "cosine/sine convolution" identities, in a booktabs summary table: transform type | convolution definition | theorem statement. Keep this concise — main depth is on the full Fourier transform case.

### 7. Why This Matters: Filtering and Systems
Explain the linear time-invariant (LTI) systems connection: if $y(t) = (h*x)(t)$ is a system's output for input $x(t)$ and impulse response $h(t)$, then $Y(\omega) = H(\omega)X(\omega)$ — this is literally how every digital filter, equalizer, and image blur operates. `infobox` with a simple block diagram description (input → system $H(\omega)$ → output, shown as multiplication in frequency domain vs convolution in time domain).

### 8. Visualising Convolution
**pgfplots graph (MANDATORY):** Two-panel or three-panel figure showing (a) two simple pulse functions $f(t)$ and $g(t)$, (b) their convolution $(f*g)(t)$ as a resulting smoothed/broadened shape, illustrating the "smearing" effect of convolution. Grid=major, labeled axes, legend.

### 9. Worked Examples

**Example 1:** Verify the convolution theorem for $f(t) = e^{-a|t|}$ and $g(t) = e^{-b|t|}$ ($a,b>0$, $a\neq b$). Compute $F(\omega)$, $G(\omega)$ from known standard transforms (Topic 07 table), multiply them, and state the result as the transform of $(f*g)(t)$ without evaluating the convolution integral directly.

**Example 2:** Directly compute $(f*g)(t)$ for two rectangular pulses $f(t)=\Pi_1(t)$ and $g(t)=\Pi_1(t)$ (each of width 2 centred at 0) using the sliding integral, showing the result is a triangular pulse. Then verify via the convolution theorem that $\mathcal{F}\{f*g\} = F(\omega)^2$ using the known sinc transform.

**Example 3:** Use the convolution theorem to solve for the output of a simple LTI system: given input $x(t) = e^{-t}u(t)$ and impulse response $h(t) = e^{-2t}u(t)$, find $Y(\omega) = X(\omega)H(\omega)$ and then find $y(t)$ using partial fractions and inverse Fourier transform.

All examples in `infobox`. End each with learnbox.

### 10. Excel Example (MANDATORY)
Numerically compute the discrete convolution of two short sampled sequences (e.g., $f = [1,1,1,0,0]$, $g=[1,1,1,0,0]$ representing sampled rectangular pulses) using the sliding-sum method:
- Columns: shift $k$ | overlap terms | $\sum f(\tau)g(k-\tau)$ (convolution value)
Compare the resulting triangular-shaped sequence to the continuous-case triangular pulse result from Example 2.
End with learnbox.

### 11. Python Example (MANDATORY)
Python script using `numpy` and `scipy.signal.fftconvolve` (or `numpy.convolve`) plus `numpy.fft`:
- Generates two rectangular pulse arrays
- Computes their convolution directly using `np.convolve`
- Computes the same result via FFT: `ifft(fft(f)*fft(g))`
- Compares both results numerically to demonstrate the convolution theorem computationally
Include expected output descriptions as comments (e.g., matching triangular arrays). End with learnbox.

### 12. Viva-Style Oral Questions (8 questions with answers)
Cover: definition of convolution, statement of the convolution theorem, difference between Fourier and Laplace convolution (limits of integration, causality), the dual multiplication theorem, why the FFT-based convolution is faster than direct convolution for long signals, physical meaning of impulse response $h(t)$, what convolution theorem tells us about filtering, whether convolution is commutative and associative (yes — briefly justify).

### 13. Descriptive Questions (5 exam-style questions)
State and prove the convolution theorem for Fourier transforms; verify the convolution theorem for a specific pair of exponential functions; explain the LTI systems interpretation of the convolution theorem with a worked example; derive the multiplication (dual) theorem from the convolution theorem using duality; compare Fourier and Laplace convolution theorems highlighting differences in domain and normalisation.

### 14. Practice Problems (6 problems)
Include problems on: verifying the theorem for two different exponential decay functions; computing a convolution directly and via the theorem for rectangular pulses of different widths; finding a system output given input and impulse response using the theorem; verifying the sine/cosine transform convolution result; a numerical/Excel-style problem computing discrete convolution; a Python-based problem confirming FFT convolution matches direct convolution.

### 15. MCQs (5 questions)
Cover: theorem statement, which factor appears in the dual multiplication theorem ($1/2\pi$), difference from Laplace convolution, LTI systems interpretation, correctness-check style question on convolution integral limits. Provide four options each with correct answer marked.

### 16. Common Mistakes Box
`mistakebox` covering: confusing Fourier and Laplace convolution formulas/limits; forgetting the $2\pi$ normalisation constant in the dual theorem; treating convolution as pointwise multiplication; sign errors in the $g(t-\tau)$ flip-and-slide substitution; applying the one-sided theorem to a two-sided (non-causal) signal.

### 17. Quick Recap
`learnbox` with 6-8 bullets: definition of convolution, convolution theorem statement, dual multiplication theorem, proof idea (order-of-integration swap + substitution), LTI systems connection, difference from Laplace convolution, numerical/Excel verification, Python FFT-based verification.

---

## MANDATORY QUALITY CHECKLIST

- [ ] Opening hook in `curiositybox`
- [ ] pgfplots 2-3 panel graph showing convolution of two pulses
- [ ] Booktabs table contrasting Fourier vs Laplace convolution
- [ ] Booktabs summary table for sine/cosine transform convolution results
- [ ] Excel numerical discrete convolution computation
- [ ] Python script using both direct convolution and FFT-based convolution
- [ ] Full step-by-step proof of the convolution theorem included
- [ ] Every major example ends with `learnbox`
- [ ] All four tcolorbox environments used at least once
- [ ] `\end{document}` present at the very end
- [ ] No undefined LaTeX macros
- [ ] Tone is conversational and encouraging throughout
- [ ] All formulae in correct LaTeX syntax
- [ ] No section references a figure that is not defined
