# Can AI Help You Build a Better Machine Learning Model?

**Course:** Machine Learning and Data Mining 1
**Date:** May 2026

---

## Overview

This project investigates whether an AI assistant (LLM) can meaningfully improve a small machine learning pipeline. Rather than chasing the highest accuracy, we focus on understanding the data, making fair comparisons, and honestly evaluating where the LLM helped — or didn't.

## What We Did

- Picked **one dataset** and **one clear ML task**
- Trained a **simple baseline model** (Multinomial Logistic Regression)
- Made **one controlled improvement** using a Gemini-suggested engineered feature (Tranquil Soundscape Index)
- Evaluated baseline vs improved version on the **same train/test split**
- Analyzed **three concrete model mistakes** in depth
- Reflected honestly on whether the LLM was useful, misleading, or neutral

---

## Dataset & Task

- **Dataset:** Spotify Tracks Dataset (`yashdev01` on Kaggle) — 81,343 tracks across 114 genres, with audio features extracted from the Spotify API.
- **Task:** Classify each song into one of four mood quadrants:
  - **Happy** — high valence + high energy
  - **Angry** — low valence + high energy
  - **Calm** — high valence + low energy
  - **Sad** — low valence + low energy

  Using audio features **excluding** `valence` and `energy` to avoid data leakage.
- **Type:** Multi-class classification (4 classes)
- **Source:** https://www.kaggle.com/datasets/yashdev01/spotify-tracks-dataset

### Class Distribution

| Mood | Count |
|---|---|
| Happy | 29,525 |
| Angry | 27,800 |
| Sad | 17,572 |
| Calm | 6,446 |

---

## Team

| Member | Role | Responsibilities |
|---|---|---|
| Tran Khoa Nam | Project Manager | Coordination, deadlines, unblocking |
| Vu Duc An | Data | Loading, cleaning, exploration, visualization |
| Nguyen Anh Tuan | Modeling | Baseline + improved model, metrics, error export |
| Phan Nam Anh | Slides & Error Analysis | 3 mistake explanations, slides, presentation |

---

## Project Structure

```
.
├── data/
│   └── processed/
│       ├── cleaned_data.csv        # Cleaned Spotify dataset
│       └── spotify-tracks-dataset.csv
├── LLM/
│   └── llm.ipynb                   # LLM feature engineering step
├── model/
│   └── model_baseline.ipynb        # Baseline + improved model
├── results/
│   ├── metrics.csv                 # Baseline vs improved scores
│   ├── wrong_predictions.csv       # 20 sampled errors for analysis
│   ├── llm_prompts.md              # Exact Gemini prompt + response
│   └── figures/                    # Confusion matrices, plots
├── slides/                         # Final presentation
├── .env                            # API key (not committed)
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

### 3. Run the baseline model

```bash
jupyter notebook model/model_baseline.ipynb
```

### 4. Run the LLM step

```bash
jupyter notebook LLM/llm.ipynb
```

---

## LLM Component

We used **Google Gemini (`gemini-2.5-flash`)** for one controlled step: **Feature Engineering Helper (Option 1)**.

We asked Gemini to suggest 3 derived features. It responded with:

1. **Vocal Emotionality Score** — speechiness × explicit × (1 − instrumentalness)
2. **Tranquil Soundscape Index** — acousticness × instrumentalness / (tempo × |loudness|)
3. **Rhythmic Character Balance** — danceability × tempo × (1 − speechiness)

We implemented **Tranquil Soundscape Index** because Calm was our rarest and hardest-to-classify mood (only 6,446 samples), and this feature directly and uniquely describes it.

To run the LLM step yourself:

1. Get a free API key from [Google AI Studio](https://aistudio.google.com/app/apikey)
2. Create a `.env` file in the project root:
   ```
   GEMINI_API_KEY=your_key_here
   ```
3. Install the client:
   ```bash
   pip install google-genai python-dotenv
   ```

The exact prompt and raw Gemini response are saved in `results/llm_prompts.md`.

---

## Results Summary

| Model | Accuracy | Macro-F1 | Note |
|---|---|---|---|
| Baseline | 0.6368 | 0.5806 | Logistic Regression, 10 original features |
| Improved | 0.6367   | 0.5805 | + Tranquil Soundscape Index (Gemini suggestion) |

---

## Did the LLM Help?

Gemini suggested the Tranquil Soundscape Index as a proxy for calm and peaceful musical character. The feature was theoretically well-motivated — targeting our rarest class (Calm) by combining acousticness and instrumentalness against tempo and loudness. However, since the individual components were already present as separate features, logistic regression had limited new information to work with. The LLM's intuition was reasonable but oversimplified: it assumed combining features into a composite would help, without accounting for what the model could already learn independently.

---

## Key Rules We Followed

- Tested only **one** LLM-suggested improvement
- Compared baseline vs improved version fairly on the same data
- Reported honestly when the LLM suggestion did not improve results

---

## License

This project is licensed under the MIT License & Kaggle License — see the [LICENSE](LICENSE) file for details.

---

## Acknowledgments

- Course staff for Machine Learning and Data Mining 1
- Dataset: Spotify Tracks Dataset by yashdev01 on Kaggle
- Google AI Studio for free-tier Gemini API access (`gemini-2.5-flash`)
