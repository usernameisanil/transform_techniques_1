# Prompt — Topic 07: Fourier Transform, Sine & Cosine Transforms, Properties

**Unit:** V — Fourier Series and Fourier Transforms
**Course:** 23A54201 — Mathematics IV (Transform Techniques)
**University:** JNTUA College of Engineering (Autonomous)
**Target Audience:** B.Tech 2nd-year engineering students (non-mathematics majors)

---

## Prompt

You are an expert mathematics professor writing a **complete, compilable LaTeX (.tex) lecture note** for B.Tech engineering students on the topic **"Fourier Transform, Fourier Sine & Cosine Transforms, and Properties of Fourier Transforms"**. This is Topic 07 of Unit V, covering the Fourier transform proper plus its specialised variants and key operational properties. Write as an enthusiastic, patient teacher who makes students feel the topic is already familiar — just not formally named yet.

---

## LATEX SETUP REQUIREMENTS

Same preamble structure as previous topics (four tcolorbox environments, pgfplots, listings).

fancyhdr:
- `\lhead{Topic 07: Fourier Transform \& Properties}`
- `\rhead{Unit V — Fourier Series \& Transforms}`
- `\cfoot{\thepage}`

Title: `\title{Topic 07: Fourier Transform, Sine \& Cosine Transforms, and Properties \\ \large Unit V — Fourier Series \& Fourier Transforms}`, `\maketitle`, `\tableofcontents`, `\newpage`.

---

## AUDIENCE AND TONE

Same conversational, enthusiastic tone.

---

## OPENING HOOK (MANDATORY)

`\begin{curiositybox}[Hook]`: A Shazam-like music recognition app must identify a song within 3 seconds of listening to ambient audio. It does this by computing the Fourier Transform of the recorded snippet and comparing its frequency fingerprint against millions of stored transforms. The entire billion-dollar technology of audio fingerprinting, spectral analysis, MRI scanning, and digital communications rests on one elegant formula: $F(\omega) = \int_{-\infty}^{\infty}f(t)e^{-i\omega t}dt$. You are about to understand that formula completely.

---

## REQUIRED SECTIONS

### 1. Why This Topic Exists
"Before we begin, here is the honest answer to why you are reading this..." Explain that the Fourier Transform is the most important transform in science and engineering: it converts any time-domain signal into its frequency spectrum, enabling filtering, compression, and analysis. Two-column booktabs table:
- "Confusing Fourier transform with Laplace transform" | "Applying wrong domain (real frequency vs complex s) to the problem"
- "Forgetting the minus sign in $e^{-i\omega t}$" | "Getting the conjugate of the correct answer"
- "Confusing $F_s$ (sine transform) with the full Fourier transform" | "Using a real-valued formula where a complex one is needed"
End with learnbox.

### 2. You Already Know This (Intuition First)
Compare to a prism splitting white light: the Fourier Transform is a mathematical prism that splits any signal $f(t)$ into its pure frequency components $F(\omega)$. Just as white light contains all colours simultaneously, a complex signal contains all frequencies simultaneously — and $|F(\omega)|$ tells you exactly how much of each frequency is present.

### 3. Definition: Fourier Transform and Inverse Fourier Transform
`infobox`:
$$F(\omega) = \mathcal{F}\{f(t)\} = \int_{-\infty}^{\infty}f(t)e^{-i\omega t}\,dt$$
$$f(t) = \mathcal{F}^{-1}\{F(\omega)\} = \frac{1}{2\pi}\int_{-\infty}^{\infty}F(\omega)e^{i\omega t}\,d\omega$$
Explain: $F(\omega)$ is generally complex-valued; $|F(\omega)|$ = amplitude spectrum, $\angle F(\omega)$ = phase spectrum. Note the asymmetric $1/2\pi$ convention — warn students that some textbooks put $1/\sqrt{2\pi}$ on both, and they must check which convention is used.

### 4. Fourier Cosine Transform
`infobox`: For functions defined on $[0,\infty)$ extended evenly:
$$F_c(\omega) = \sqrt{\frac{2}{\pi}}\int_0^\infty f(t)\cos(\omega t)\,dt$$
$$f(t) = \sqrt{\frac{2}{\pi}}\int_0^\infty F_c(\omega)\cos(\omega t)\,d\omega$$
(Symmetric convention; some books use $2/\pi$ prefactor on one and 1 on the other — note the convention used.)

### 5. Fourier Sine Transform
`infobox`: For functions defined on $[0,\infty)$ extended oddly:
$$F_s(\omega) = \sqrt{\frac{2}{\pi}}\int_0^\infty f(t)\sin(\omega t)\,dt$$
$$f(t) = \sqrt{\frac{2}{\pi}}\int_0^\infty F_s(\omega)\sin(\omega t)\,d\omega$$

### 6. Properties of Fourier Transforms
Present each property in a `infobox` row within a booktabs table (10+ properties). For each: name, mathematical statement, one-line proof idea, physical interpretation.
1. **Linearity:** $\mathcal{F}\{af+bg\} = aF+bG$
2. **Time Shifting:** $\mathcal{F}\{f(t-a)\} = e^{-i\omega a}F(\omega)$
3. **Frequency Shifting:** $\mathcal{F}\{e^{i\omega_0 t}f(t)\} = F(\omega-\omega_0)$
4. **Time Scaling:** $\mathcal{F}\{f(at)\} = \frac{1}{|a|}F(\omega/a)$
5. **Time Reversal:** $\mathcal{F}\{f(-t)\} = F(-\omega) = \overline{F(\omega)}$ (if f is real)
6. **Differentiation in Time:** $\mathcal{F}\{f'(t)\} = i\omega F(\omega)$ (converts differentiation to multiplication)
7. **Differentiation in Frequency:** $\mathcal{F}\{-it\cdot f(t)\} = F'(\omega)$
8. **Integration:** $\mathcal{F}\left\{\int_{-\infty}^t f(\tau)d\tau\right\} = \frac{F(\omega)}{i\omega}$
9. **Duality / Symmetry:** $\mathcal{F}\{F(t)\} = 2\pi f(-\omega)$
10. **Modulation:** $\mathcal{F}\{f(t)\cos(\omega_0 t)\} = \frac{1}{2}[F(\omega-\omega_0)+F(\omega+\omega_0)]$

### 7. Standard Transform Pairs Table
Booktabs table (8+ rows): $f(t)$ | $F(\omega)$ | Notes.
- $e^{-at}u(t)$ | $\frac{1}{a+i\omega}$ | $a>0$
- $e^{-a|t|}$ | $\frac{2a}{a^2+\omega^2}$ | even, Lorentzian
- Rectangular pulse $\Pi_a(t)$ | $\frac{2\sin(a\omega)}{\omega}$ | sinc function
- $\delta(t)$ (Dirac delta) | $1$ | all frequencies equal
- $1$ | $2\pi\delta(\omega)$ | duality of above
- $e^{-at^2}$ (Gaussian) | $\sqrt{\pi/a}\,e^{-\omega^2/(4a)}$ | Gaussian transforms to Gaussian
- $\cos(\omega_0 t)$ | $\pi[\delta(\omega-\omega_0)+\delta(\omega+\omega_0)]$
- $\sin(\omega_0 t)$ | $-i\pi[\delta(\omega-\omega_0)-\delta(\omega+\omega_0)]$

### 8. Visualising the Frequency Domain
**pgfplots graph (MANDATORY):** Plot the rectangular pulse $f(t)=1$ for $|t|<1$ in the time domain and its Fourier transform magnitude $|F(\omega)|=|2\sin\omega/\omega|$ (sinc shape) in the frequency domain. Two-panel figure. Grid=major, labeled axes, legend.

### 9. Worked Examples

**Example 1:** Find the Fourier transform of $f(t) = e^{-at}u(t)$ ($a>0$, where $u(t)$ is the unit step). Show full computation. Identify real part ($a/(a^2+\omega^2)$) and imaginary part ($-\omega/(a^2+\omega^2)$). Compute $|F(\omega)|$.

**Example 2:** Use the time-shifting property to find $\mathcal{F}\{e^{-a(t-2)}u(t-2)\}$ directly from Example 1 without repeating the integral computation.

**Example 3:** Find the Fourier cosine transform of $f(x) = e^{-ax}$ ($a>0$, $x>0$). Compute $F_c(\omega) = \sqrt{2/\pi}\cdot a/(a^2+\omega^2)$.

**Example 4:** Use the differentiation property to find $\mathcal{F}\{f'(t)\}$ if $f(t)=e^{-|t|}$, given that $F(\omega) = 2/(1+\omega^2)$. Show the result directly from $i\omega F(\omega)$.

All examples in `infobox`. End each with learnbox.

### 10. Excel Example (MANDATORY)
Numerically approximate the Fourier transform of the rectangular pulse $f(t)=1$ for $|t|<1$ at $\omega=0.5, 1.0, 1.5, 2.0$ using Riemann sum:
- Columns: $t_i$ | $f(t_i)$ | $f(t_i)\cos(\omega t_i)$ | $f(t_i)\sin(\omega t_i)$ | Running $\text{Re}(F)$ | Running $\text{Im}(F)$
Compare to exact $F(\omega) = 2\sin(\omega)/\omega$.
End with learnbox.

### 11. Python Example (MANDATORY)
Python script using `numpy.fft`:
- Generates the rectangular pulse signal sampled at $N=512$ points
- Computes its DFT using `np.fft.fft` and shifts with `np.fft.fftshift`
- Describes plotting the magnitude spectrum showing the sinc shape
- Comments explain the relationship between the continuous Fourier transform and the discrete FFT
Include expected output descriptions as comments. End with learnbox.

### 12. Viva-Style Oral Questions (8 questions with answers)
Cover: definition of FT and IFT, why $e^{-i\omega t}$ instead of $e^{i\omega t}$, what $|F(\omega)|$ represents physically, condition for FT to exist (absolute integrability), difference between FT and Fourier series, how the differentiation property saves effort in solving ODEs, Parseval's theorem for FT (preview), what the Fourier cosine/sine transforms are used for.

### 13. Descriptive Questions (5 exam-style questions)
Derive the Fourier transform of $e^{-a|t|}$ from the definition; state and prove the time-shifting property; state and prove the differentiation property; find the FT of a triangular pulse using the differentiation property; compare FT, Laplace transform, and Fourier series in a tabular format.

### 14. Practice Problems (6 problems)
$f(t)=e^{-2t}u(t)$; $f(t)=te^{-t}u(t)$ (use differentiation in frequency); $f(t)=e^{-t}\cos(2t)u(t)$; Fourier cosine transform of $x^{n-1}e^{-ax}$; Fourier sine transform of $e^{-ax}/x$ (stated, result involves $\arctan$); FT of Gaussian $e^{-t^2}$.

### 15. MCQs (5 questions)
Cover: FT of $e^{-a|t|}$, time-shifting property, condition for FT existence, what differentiation property does to the transform, FT of $\delta(t)$.

### 16. Common Mistakes Box
`mistakebox` tabular (5 rows):
- Forgetting the $1/2\pi$ factor in the inverse FT
- Writing $e^{+i\omega t}$ in the forward transform (wrong sign)
- Confusing $\omega$ (angular frequency, rad/s) with $f$ (frequency in Hz): $\omega=2\pi f$
- Applying time-shifting without the $e^{-i\omega a}$ phase factor
- Confusing Fourier cosine/sine transform with the full complex FT

### 17. Quick Recap
`learnbox` 6–8 bullets: FT definition and IFT, sine/cosine transform variants, 10 key properties, standard pairs, spectrum interpretation, connection to Laplace (s replaced by $i\omega$ on imaginary axis), FFT as practical computational tool.

---

## MANDATORY QUALITY CHECKLIST

- [ ] Opening hook in `curiositybox`
- [ ] pgfplots dual-panel graph (rectangular pulse and its sinc FT)
- [ ] Booktabs properties table (10+ rows)
- [ ] Booktabs standard pairs table (8+ rows)
- [ ] Excel numerical FT computation
- [ ] Python FFT script with `numpy.fft`
- [ ] Every major example ends with `learnbox`
- [ ] All four tcolorbox environments used
- [ ] `\end{document}` at end
- [ ] Conversational tone throughout
