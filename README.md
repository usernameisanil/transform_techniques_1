# Transform Techniques — Units IV & V

**Course:** 23A54201 — Mathematics IV (Transform Techniques)  
**University:** JNTUA College of Engineering (Autonomous), Ananthapuramu  
**Department:** Civil Engineering | II B.Tech II Semester (R23)  

---

## About This Repository

This repository contains structured learning materials for **Units IV and V** of the Transform Techniques course — covering Laplace Transforms and Fourier Series & Fourier Transforms.

It mirrors the structure of [statistical_methods_1](https://github.com/usernameisanil/statistical_methods_1), with beginner-friendly, LaTeX-based topic notes.

---

## Repository Structure

```
transform_techniques_1/
├── README.md                    ← This file
├── topics.txt                   ← All unit-wise topics in order
├── topics/                      ← Topic overview markdown files (unit-wise)
│   ├── unit_iv_topics.md
│   └── unit_v_topics.md
├── prompts/                     ← One detailed prompt per topic (01–18)
│   ├── unit_iv/
│   │   ├── topic_01_laplace_definition_standard_functions.md
│   │   ├── ... (10 total)
│   └── unit_v/
│       ├── topic_11_fourier_series_coefficients_dirichlet.md
│       ├── ... (8 total)
└── responses/                   ← Placeholder .tex + .pdf for each topic
    ├── unit_iv/
    └── unit_v/
```

---

## Units Covered

### Unit IV — Laplace Transforms
| # | Topic |
|---|-------|
| 01 | Definition & Laplace Transform of Standard Functions |
| 02 | Existence of Laplace Transform |
| 03 | Inverse Laplace Transform |
| 04 | First Shifting Theorem |
| 05 | Transforms of Derivatives and Integrals |
| 06 | Unit Step Function & Second Shifting Theorem |
| 07 | Convolution Theorem |
| 08 | Laplace Transform of Periodic Functions |

### Unit V — Fourier Series and Fourier Transforms
| # | Topic |
|---|-------|
| 09 | Fourier Coefficients (Euler's) & Dirichlet Conditions |
| 10 | Fourier Series of Even and Odd Functions |
| 11 | Fourier Series in Arbitrary Interval & Half-Range Expansions |
| 12 | Fourier Integral Theorem & Sine/Cosine Integrals |
| 13 | Complex Form of Fourier Integral & Fourier Transform |
| 14 | Fourier Sine and Cosine Transforms |
| 15 | Properties of Fourier Transforms |
| 16 | Inverse Fourier Transforms & Convolution Theorem |

---

## How to Use

1. Navigate to `prompts/` and open any `topic_NN_name.md`
2. Copy the prompt block inside the triple-backtick block
3. Paste into an AI model (e.g., Claude, GPT-4) to generate the LaTeX response
4. Save the output as the corresponding `.tex` file in `responses/`
5. Compile with `pdflatex` to get the final PDF

---

## Textbooks Referenced

1. B.S. Grewal — *Higher Engineering Mathematics*, Khanna Publishers, 44th Edition
2. Erwin Kreyszig — *Advanced Engineering Mathematics*, 10th Edition, Wiley
3. A.R. Vasistha & R.K. Gupta — *Integral Transforms*, Krishna Prakashan Media

---

## Online Resources

- https://nptel.ac.in/courses/111104074
- https://onlinecourses.nptel.ac.in/noc20_ma02/preview
- https://nptel.ac.in/courses/111107090
