# Media Literacy HMM — Manuscript and Code

This repository contains the complete LaTeX source of the manuscript and the fully reproducible Python implementation of the numerical case study.

## Manuscript

**Title:** *Spectral Analysis and Optimal Control of Hidden Markov Models for Media Literacy*

**File:** `RPJ.Alfabetizacion.Sep.17.2026.V3.tex`

**Abstract:** We introduce the first Hidden Markov Model (HMM) with three cognitive states (credulous, passive skeptic, active verifier) for media literacy dynamics, and formulate an optimal control problem for intervention design. We derive spectral properties of the transition matrix, sharp estimates for the expected mean return time to the verifier state, and prove existence and uniqueness of the optimal intervention under resource constraints. A sensitivity bound establishes monotonicity of the probability of reaching the verifier state with respect to upward transition probabilities. The theoretical results are validated with a fully reproducible numerical case study on a synthetic dataset of fifty students over twenty weeks.

**Compilation:** `pdflatex → biber → pdflatex × 2` (requires the `randpunkt` document class and `rpj-bibliography-alfabetizacion.bib`).

## Repository contents

| File | Description |
|------|-------------|
| `RPJ.Alfabetizacion.Sep.17.2026.V3.tex` | LaTeX source of the manuscript |
| `alfabetizacion.py` | Main pipeline (HMM fitting, Monte Carlo, optimal control, bootstrap, robustness, monotonicity) |
| `test_alfabetizacion.py` | 64 unit and integration tests |
| `conftest.py` | pytest fixtures and configuration |
| `generar_datos_sinteticos.py` | Synthetic dataset generator |
| `datos_entrada.csv` | Synthetic dataset (50 students × 20 weeks = 1,000 observations) |
| `requirements.txt` | Python dependencies |
| `figuras/` | Figures 1, 2, and 3 of the manuscript |
| `resultados/` | Reference outputs (CSV, LaTeX matrices, text reports) |
| `README.md` | Installation and reproduction instructions |
| `LICENSE` | MIT License |

## Reproduce the results

```bash
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
python generar_datos_sinteticos.py
python alfabetizacion.py
pytest test_alfabetizacion.py -v
