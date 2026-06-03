# Framingham Heart Study — Full Deployment Guide
## Flask API (Render) + Lovable Frontend

---

## STEP 1 — Run Your Notebook

Open `Framingham_Heart_ML_FINAL.ipynb`, run all cells.
Copy these 4 generated files into this folder:

```
best_clf_model.joblib
scaler_clf.joblib
best_reg_model.joblib
scaler_reg.joblib
```

---

## STEP 2 — Push to GitHub

```bash
git init
git add .
git commit -m "Framingham Heart Study ML API"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/framingham-api.git
git push -u origin main
```

> ✅ Make sure the 4 .joblib files are included in the repo

---

## STEP 3 — Deploy Flask API on Render.com

1. Go to https://render.com → Sign up / Log in
2. Click New + → Web Service
3. Connect your GitHub repo
4. Fill in settings:
   - Name: framingham-chd-predictor
   - Runtime: Python
   - Build Command: pip install -r requirements.txt
   - Start Command: gunicorn app:app
5. Click Create Web Service
6. Wait ~3 minutes → live URL:
   https://framingham-chd-predictor.onrender.com
7. Test: open https://your-url.onrender.com/health
   Should return: {"status": "ok", "clf_model_loaded": true, "reg_model_loaded": true}

---

## STEP 4 — Build Frontend on Lovable.dev

1. Go to https://lovable.dev → Sign up
2. Click New Project
3. Open LOVABLE_PROMPT.txt from this folder
4. Replace YOUR_RENDER_URL with your actual Render URL
5. Paste the full prompt → click Generate
6. Lovable builds a React app — preview live

---

## STEP 5 — Deploy Lovable Frontend

In Lovable: click Publish → live at https://your-project.lovable.app

---

## Architecture

User → Lovable Frontend → Flask API (Render) → .joblib Models
