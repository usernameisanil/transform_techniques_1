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
│   ├── topic_01_laplace_definition.md
│   ├── topic_02_laplace_standard_functions.md
│   ├── topic_03_laplace_existence.md
│   ├── topic_04_inverse_laplace.md
│   ├── topic_05_first_shifting_theorem.md
│   ├── topic_06_transforms_derivatives_integrals.md
│   ├── topic_07_unit_step_function.md
│   ├── topic_08_second_shifting_theorem.md
│   ├── topic_09_convolution_theorem_laplace.md
│   └── topic_10_laplace_periodic_functions.md
└── unit_v/
    ├── topic_11_fourier_series_coefficients.md
    ├── topic_12_dirichlet_conditions_even_odd.md
    ├── topic_13_fourier_series_arbitrary_half_range.md
    ├── topic_14_fourier_integral_complex_form.md
    └── topic_15_fourier_transforms_properties_convolution.md
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
| 01 | Definition of Laplace Transform | IV | `unit_iv/topic_01_laplace_definition.md` |
| 02 | Laplace Transform of Standard Functions | IV | `unit_iv/topic_02_laplace_standard_functions.md` |
| 03 | Existence of Laplace Transform | IV | `unit_iv/topic_03_laplace_existence.md` |
| 04 | Inverse Laplace Transform | IV | `unit_iv/topic_04_inverse_laplace.md` |
| 05 | First Shifting Theorem | IV | `unit_iv/topic_05_first_shifting_theorem.md` |
| 06 | Transforms of Derivatives and Integrals | IV | `unit_iv/topic_06_transforms_derivatives_integrals.md` |
| 07 | Unit Step Function | IV | `unit_iv/topic_07_unit_step_function.md` |
| 08 | Second Shifting Theorem | IV | `unit_iv/topic_08_second_shifting_theorem.md` |
| 09 | Convolution Theorem (Laplace) | IV | `unit_iv/topic_09_convolution_theorem_laplace.md` |
| 10 | Laplace Transform of Periodic Functions | IV | `unit_iv/topic_10_laplace_periodic_functions.md` |
| 11 | Fourier Series: Coefficients (Euler's) & Dirichlet Conditions | V | `unit_v/topic_11_fourier_series_coefficients.md` |
| 12 | Fourier Series: Even/Odd Functions & Dirichlet Conditions | V | `unit_v/topic_12_dirichlet_conditions_even_odd.md` |
| 13 | Fourier Series in Arbitrary Interval & Half-Range Expansions | V | `unit_v/topic_13_fourier_series_arbitrary_half_range.md` |
| 14 | Fourier Integral Theorem & Complex Form | V | `unit_v/topic_14_fourier_integral_complex_form.md` |
| 15 | Fourier Transforms: Properties, Inverse & Convolution | V | `unit_v/topic_15_fourier_transforms_properties_convolution.md` |
