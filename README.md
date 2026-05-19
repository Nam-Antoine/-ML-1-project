# Can AI Help You Build a Better Machine Learning Model?

**Course:** ICT 3.3 Machine Learning and Data Mining
**Date:** May 2026

---

## Overview

This project investigates whether an AI assistant (LLM) can meaningfully improve a small machine learning pipeline. Rather than chasing the highest accuracy, we focus on understanding the data, making fair comparisons, and honestly evaluating where the LLM helped — or didn't.

## What We Did

- Picked **one dataset** and **one clear ML task**
- Trained a **simple baseline model**
- Made **one controlled improvement** (feature engineering / error analysis assisted by an LLM)
- Evaluated baseline vs improved version on the **same train/test split**
- Analyzed **three concrete model mistakes** in depth
- Reflected on whether the LLM was useful, misleading, or neutral

---

## Dataset & Task

- **Dataset:** _[e.g., Palmer Penguins / Heart Disease / Student Performance]_
- **Task:** _[e.g., Classify penguin species from body measurements]_
- **Type:** _[Classification / Regression / Clustering]_
- **Source:** _[link to dataset]_

---

## Team

| Member | Role | Responsibilities |
|---|---|---|
| _[Tran Khoa Nam]_ | Project Manager | Coordination, deadlines, unblocking |
| _[Vu Duc An]_ | Data | Loading, cleaning, exploration, visualization |
| _[Nguyen Anh Tuan]_ | Modeling | Baseline + improved model, metrics, error export |
| _[Phan Nam Anh]_ | Slides & Error Analysis | 3 mistake explanations, slides, presentation |

---

## Project Structure

```
.
├── data/                   # Raw and processed data (gitignored)
├── notebooks/              # Jupyter notebooks
│   └── main.ipynb          # Main pipeline
├── src/                    # Helper scripts
├── results/                # Plots, metrics, error analysis
├── slides/                 # Final presentation
├── requirements.txt
├── LICENSE
└── README.md
```

---

## How to Run

### 1. Clone the repo

```bash
git clone https://github.com/Nam-Antoine/ML1-project.git
cd ML1-project
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Run the notebook

```bash
jupyter notebook notebooks/main.ipynb
```

---

## LLM Component

We used **Google Gemini (`gemini-2.5-flash`)** for one controlled step: _[Feature Engineering Helper / Error Analysis Assistant]_.

To run the LLM step yourself:

1. Get a free API key from [Google AI Studio](https://aistudio.google.com/app/apikey)
2. Create a `.env` file:
   ```
   GEMINI_API_KEY=your_key_here
   ```
3. Install the client:
   ```bash
   pip install google-genai
   ```

The exact prompt we used is documented in `notebooks/main.ipynb`.

---

## Results Summary

| Model | Metric | Score |
|---|---|---|
| Baseline | _[Accuracy / RMSE / F1]_ | _[xx.x]_ |
| Improved | _[Accuracy / RMSE / F1]_ | _[xx.x]_ |

See `results/` for full plots and the three-mistake error analysis.

---

## Did the LLM Help?

_[Short honest reflection — 2–3 sentences. Did it suggest something useful? Did it mislead? Was its explanation aligned with your own reasoning?]_

---

## Key Rules We Followed

- Locked the train/test split on Day 1 and never changed it
- Tested only **one** improvement, not many
- Compared baseline vs improved version fairly
- Reported honestly when the LLM did not help

---

## License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

## Acknowledgments

- Course staff for ICT 3.3 Machine Learning and Data Mining
- Dataset providers (see Dataset section)
- Google AI Studio for free-tier Gemini API access
