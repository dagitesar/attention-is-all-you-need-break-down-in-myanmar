# Attention Is All You Need ကို အပိုင်းလိုက် ခွဲကြည့်မယ်

A Burmese, beginner-friendly breakdown of the Transformer paper
*[Attention Is All You Need](https://arxiv.org/abs/1706.03762)* (Vaswani et al., 2017),
one idea per page. Each lesson explains the idea with everyday analogies first, then the
math, code and interactive visuals, and ends with discussion questions and a question form.

Made by **Da Gite Sar**.

## Lessons

| # | Lesson | Paper section | Status |
| --- | --- | --- | --- |
| 1 | Positional Encoding (sin/cos, နာရီလက်တံ) | 3.5 | ✅ Published |
| 2 | Scaled Dot-Product Attention (Query, Key, Value) | 3.2.1 | ⬜ Planned |
| 3 | Multi-Head Attention | 3.2.2 | ⬜ Planned |
| 4 | Masking, Self-Attention & Cross-Attention | 3.2.3 | ⬜ Planned |
| 5 | Feed-Forward, Residual Connections & Layer Norm | 3.1, 3.3 | ⬜ Planned |
| 6 | Embeddings & the Output Layer | 3.4 | ⬜ Planned |
| 7 | The Full Encoder–Decoder Architecture | 3, 3.1 | ⬜ Planned |
| 8 | Why Self-Attention (vs RNN and CNN) | 4 | ⬜ Planned |
| 9 | Training: Adam Warmup, Dropout, Label Smoothing | 5 | ⬜ Planned |
| 10 | Results, and What Came After (BERT, GPT, ViT) | 6, 7 | ⬜ Planned |

The order may change as the series grows. Update the table when a lesson goes live.

## Repository layout

```
index.html                      ← series home page (links to every lesson)
positional-encoding/index.html  ← lesson 1
<next-lesson>/index.html        ← one folder per lesson
assets/                         ← shared images, logo, etc. (optional)
apps-script/questions_inbox.gs  ← Google Apps Script for the question form
.github/workflows/deploy.yml    ← publishes the site to GitHub Pages
README.md
```

Each lesson lives in its own folder, so its address stays short and permanent:
`https://<your-username>.github.io/<repo-name>/<lesson-folder>/`.

## Adding a new lesson

1. Create a folder with a short English name, e.g. `scaled-dot-product-attention/`.
2. Copy an existing lesson's `index.html` into it as a starting point. It already includes the
   two-column layout, styles, logo, question drawer and form script.
3. Change the `<title>`, the header, and the content. The form sends the page title and URL with
   every question, so you can tell which lesson a question came from.
4. Keep `QUESTION_ENDPOINT = "PASTE_YOUR_WEB_APP_URL_HERE"` as it is. The workflow fills in the
   real URL for every page when it deploys.
5. Add a link to the lesson on the home page (`index.html`) and update the table above.
6. Push to `main`. The site redeploys automatically.

### Style notes for lessons

- Two columns: Burmese explanation on the left; equations, code, tables and visuals on the right.
- Introduce ideas with analogies before formulas; assume only basic school math.
- Explain any new math (like π or radians) before it is used.
- End with a short summary and 3–4 discussion questions.

## Publishing (GitHub Pages)

1. **Settings → Pages → Build and deployment → Source: GitHub Actions.**
2. **Settings → Secrets and variables → Actions → Variables → New repository variable**
   - Name: `QUESTION_ENDPOINT`
   - Value: your Apps Script web app URL (ends in `/exec`)
3. Push to `main`, or run **Deploy to GitHub Pages** from the **Actions** tab.

The workflow publishes every page and folder in the repo except `.github/`, `apps-script/`
and this README, and inserts `QUESTION_ENDPOINT` into every `.html` file.

## Question inbox (Apps Script)

One Google Sheet collects questions from every lesson.

1. Create a Google Sheet → **Extensions → Apps Script**, paste `apps-script/questions_inbox.gs`.
2. **Project Settings → Time zone → (GMT+06:30) Yangon.**
3. Run `setup()` once and approve permissions.
4. **Deploy → New deployment → Web app** (Execute as: Me, Who has access: Anyone).
5. Copy the URL into the `QUESTION_ENDPOINT` repository variable above.

Each email can submit one question per day across the whole site. After changing the script:
**Deploy → Manage deployments → edit → New version** (the URL stays the same).

Planned: a scheduled Kaggle notebook that reads new questions and sends them to Telegram.

## Reference

Vaswani, A., Shazeer, N., Parmar, N., Uszkoreit, J., Jones, L., Gomez, A. N., Kaiser, Ł., and
Polosukhin, I. (2017). *Attention Is All You Need.* NeurIPS 2017.
[arXiv:1706.03762](https://arxiv.org/abs/1706.03762)
