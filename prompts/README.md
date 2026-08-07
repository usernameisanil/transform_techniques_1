# Prompts Directory

**Course:** Transform Techniques  
**University:** JNTUA College of Engineering (Autonomous)  

---

## Purpose

This directory contains **AI content-generation prompts** for each topic in Units IV and V. Each prompt is designed to generate a complete, lecture-quality explanation of the topic — covering theory, formulae, worked examples, and exam-oriented problem sets.

---

## Structure

```
prompts/
├── README.md                          ← This file
├── prompt_to_generate_response.txt    ← Instructions for AI response generation
├── unit_iv/
│   ├── topic_01_laplace_definition_standard_functions.md
│   ├── topic_02_laplace_existence.md
│   ├── topic_03_inverse_laplace.md
│   ├── topic_04_first_shifting_theorem.md
│   ├── topic_05_transforms_derivatives_integrals.md
│   ├── topic_06_unit_step_second_shifting.md
│   ├── topic_07_convolution_theorem.md
│   └── topic_08_laplace_periodic_functions.md
└── unit_v/
    ├── topic_01_fourier_coefficients.md
    ├── topic_02_dirichlet_conditions.md
    ├── topic_03_even_odd_functions.md
    ├── topic_04_arbitrary_interval.md
    ├── topic_05_half_range_expansions.md
    ├── topic_06_fourier_integral_theorem.md
    ├── topic_07_fourier_transform.md
    └── topic_08_convolution_theorem.md
```

---

## Prompt Design Guidelines

Each prompt follows a consistent structure:

1. **Role / Audience** — Define the AI's role and the target student profile
2. **Topic Overview** — What the topic covers and why it matters
3. **Content Sections** — Specific sections the output must include
4. **Formula Requirements** — Key formulae to be covered with proper notation
5. **Worked Examples** — Number and type of solved problems required
6. **Tone & Style** — Teaching style, language level, formatting conventions
7. **Output Format** — Required structure of the response

---

## Responses

Generated responses for each prompt are stored in the `responses/` directory (sibling to `prompts/`), mirroring the same `unit_iv/` and `unit_v/` folder structure.

---

## Topic Index

| Topic No. | Title | Unit | Prompt File |
|-----------|-------|------|-------------|
| 01 | Definition & Laplace Transform of Standard Functions | IV | `unit_iv/topic_01_laplace_definition_standard_functions.md` |
| 02 | Existence of Laplace Transform | IV | `unit_iv/topic_02_laplace_existence.md` |
| 03 | Inverse Laplace Transform | IV | `unit_iv/topic_03_inverse_laplace.md` |
| 04 | First Shifting Theorem | IV | `unit_iv/topic_04_first_shifting_theorem.md` |
| 05 | Transforms of Derivatives and Integrals | IV | `unit_iv/topic_05_transforms_derivatives_integrals.md` |
| 06 | Unit Step Function & Second Shifting Theorem | IV | `unit_iv/topic_06_unit_step_second_shifting.md` |
| 07 | Convolution Theorem (Laplace) | IV | `unit_iv/topic_07_convolution_theorem.md` |
| 08 | Laplace Transform of Periodic Functions | IV | `unit_iv/topic_08_laplace_periodic_functions.md` |
| 01 | Fourier Series: Determination of Fourier Coefficients (Euler's) | V | `unit_v/topic_01_fourier_coefficients.md` |
| 02 | Dirichlet Conditions for the Existence of Fourier Series | V | `unit_v/topic_02_dirichlet_conditions.md` |
| 03 | Fourier Series of Even and Odd Functions | V | `unit_v/topic_03_even_odd_functions.md` |
| 04 | Fourier Series in an Arbitrary Interval | V | `unit_v/topic_04_arbitrary_interval.md` |
| 05 | Half-Range Fourier Sine and Cosine Expansions | V | `unit_v/topic_05_half_range_expansions.md` |
| 06 | Fourier Integral Theorem, Sine & Cosine Integrals, Complex Form | V | `unit_v/topic_06_fourier_integral_theorem.md` |
| 07 | Fourier Transform, Sine & Cosine Transforms, Properties | V | `unit_v/topic_07_fourier_transform.md` |
| 08 | Convolution Theorem for Fourier Transforms | V | `unit_v/topic_08_convolution_theorem.md` |
