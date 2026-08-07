# Prompt — Topic 01: Definition of Laplace Transform

**Unit:** IV — Laplace Transforms  
**Course:** Transform Techniques  
**University:** JNTUA College of Engineering (Autonomous)  
**Target Audience:** B.Tech 2nd-year engineering students (non-mathematics majors)  

---

## Prompt

You are an expert mathematics professor writing a **complete, compilable LaTeX (.tex) lecture note** for B.Tech engineering students on the topic **"Definition of Laplace Transform"**. This is Topic 01 of Unit IV. Students have prior knowledge of basic calculus (differentiation and integration), exponential functions, and improper integrals. Write as an enthusiastic, patient teacher who makes students feel the topic is already familiar — just not formally named yet.

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
- `\lhead{Topic 01: Definition of Laplace Transform}`
- `\rhead{Unit IV — Transform Techniques}`
- `\cfoot{\thepage}`

Configure lstlisting for Python:
```
basicstyle=\ttfamily\small, keywordstyle=\color{blue},
commentstyle=\color{gray}, stringstyle=\color{orange},
numbers=left, numberstyle=\tiny, breaklines=true, frame=single
```

Title page: `\title{Topic 01: Definition of Laplace Transform \\ \large Unit IV — Laplace Transforms}`, `\maketitle`, then `\tableofcontents`, then `\newpage`.

---

## AUDIENCE AND TONE

- Students are intelligent but underconfident B.Tech 2nd-year students.
- Write like an enthusiastic, patient teacher who genuinely enjoys this topic.
- Use active language: "Let's find out", "Here is the key idea:", "You already use this — you just haven't called it that."
- Keep paragraphs short. Vary sentence length. Avoid walls of text.
- Every explanation must feel like a conversation, not a textbook dump.

---

## OPENING HOOK (MANDATORY)

Place inside `\begin{curiositybox}[Hook]`: When engineers design a control system for an aircraft autopilot, they must solve differential equations describing the motion. These equations are very hard to solve directly. But what if there was a magical operation that turns those differential equations into simple algebraic equations — solve them easily, then transform back? That magical operation is the Laplace Transform. Welcome to one of the most powerful tools in engineering mathematics.

---

## REQUIRED SECTIONS

### 1. Why This Topic Exists
Open with: "Before we begin, here is the honest answer to why you are reading this..."
Explain that Laplace transforms convert differential equations (hard) into algebraic equations (easy), making them indispensable in control systems, signal processing, and circuit analysis.
Two-column booktabs table showing: "Without Laplace" | "With Laplace" for solving ODEs, analysing circuits, designing controllers.
End with a learnbox.

### 2. Intuition First — What Is a Transform?
Explain the concept of a mathematical transform: it changes the domain of a function (from time-domain to s-domain). Analogy: just as logarithms convert multiplication into addition, Laplace converts differentiation into multiplication.

### 3. Formal Definition
- Define: $\mathcal{L}\{f(t)\} = F(s) = \int_0^{\infty} e^{-st} f(t)\, dt$
- Inside `infobox`: state full definition, domain conditions (t ≥ 0, s complex).
- Explain each part: $e^{-st}$ is the kernel, s is a complex variable (s = σ + jω), F(s) is the transform.
- Notation: $\mathcal{L}\{f(t)\} = F(s)$, and the inverse is $\mathcal{L}^{-1}\{F(s)\} = f(t)$.
- Key property: the transform is a linear operator.

### 4. Linearity Property
- State: $\mathcal{L}\{af(t) + bg(t)