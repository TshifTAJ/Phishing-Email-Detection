# ITRI625 – Phishing Email Detection (TF-IDF + Neural Network)

## Setup (once)
1. Download **Phishing Email Dataset** from Kaggle (file `Phishing_Email.csv`) and put it in this folder.
2. `pip install -r requirements.txt`

## Run order
1. Open `ITRI625_Phishing_Detection.ipynb` → **Kernel > Restart & Run All**. Leave ALL outputs in the notebook, then save (avoids the -10 deduction).
   This also creates `model/`, `training_log.csv` and `Theory_Report.md`.
2. Terminal 1: `python api.py`
3. Terminal 2: `python app.py` → paste an email → **Check Email**.

## Files
| File | Purpose |
|---|---|
| `ITRI625_Phishing_Detection.ipynb` | Data split, model, logging, graphs, early stopping, XAI |
| `phish_utils.py` | Prediction + word-occlusion explainability |
| `api.py` | Flask API (`POST /predict`) |
| `app.py` | Tkinter desktop app |
| `theory_template.md` → `Theory_Report.md` | Theory (auto-filled with your results) |

## Version control (REQUIRED – avoid -10)
Commit often, with real messages, over several days. Suggested sequence:
```
git init && git add README.md requirements.txt && git commit -m "Project setup"
git add notebook && git commit -m "Load data and split train/val/test"
git commit -am "Add TF-IDF and MLP model"
git commit -am "Add metric logging and early stopping"
git commit -am "Add evaluation graphs"
git add phish_utils.py api.py && git commit -m "Add XAI and Flask API"
git add app.py && git commit -m "Add Tkinter desktop app"
git add Theory_Report.md && git commit -m "Add theory report"
git remote add origin <your-repo-url> && git push -u origin main
```
(Use a `.gitignore` for `model/` only if the repo size is a problem; otherwise commit it so the app runs after cloning.)

## 5-minute demo script
1. **Problem:** phishing emails → classify Phishing/Safe.
2. **Data:** Kaggle dataset, split 70/15/15 (train/val/test).
3. **Model:** TF-IDF turns text into numbers → small neural net (64 ReLU neurons → sigmoid).
4. **Training:** show per-epoch log; early stopping (patience 3) stops it automatically.
5. **Results:** show loss curve, ROC, PR, confusion matrix, metrics table.
6. **App:** run `api.py` + `app.py`, paste a phishing and a safe email; point out the "Why?" words (XAI).
