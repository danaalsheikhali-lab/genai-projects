# Detecting AI-Generated News Articles

A text classifier that distinguishes human-written from LLM-generated news articles, comparing heuristic, perplexity, and TF-IDF approaches on a 10k-article dataset — with an adversarial-robustness analysis.

## What it does
A text classifier that distinguishes human-written news articles from LLM-generated
ones, built and evaluated on a balanced ~10k-article dataset (real *Guardian* articles
vs. LLM-generated articles in the same style).

The notebook works through four detection strategies and compares them on held-out data:

1. **Zero-shot LLM baseline** — ask an LLM to judge authorship directly *(optional, needs an API key)*
2. **Heuristic features** — stylometric signals (sentence-length variance, quote frequency, type-token ratio, etc.) + logistic regression
3. **Perplexity** — how "surprised" GPT-2 is by the text, added as a feature
4. **TF-IDF (unigrams + bigrams)** — the strongest model, selected as the final submission

It closes with an **adversarial-robustness** test (can a crafted prompt fool the detector?)
and a discussion of what that implies for deploying detection at scale.

## Stack
Python, scikit-learn, Hugging Face Transformers (GPT-2), pandas, OpenAI API

## Results
Heuristic + logistic regression reached 85.8% accuracy / 0.9166 AUC; adding GPT-2 perplexity raised AUC to 0.9391; a TF-IDF (unigram+bigram) model performed best and was the final submission. A zero-shot LLM baseline only reached ~60%.

## Running it
Open `ai_text_detector.ipynb` in Jupyter or Google Colab. The core classifier runs with no API key (public dataset + scikit-learn/Transformers). Only the optional LLM-baseline and adversarial sections require `OPENAI_API_KEY`.

```bash
export OPENAI_API_KEY="sk-..."   # if the notebook's API sections are used
```

---
*Course project for Harvard Kennedy School DPI-681, "Public Problem Solving with Generative AI." Built on course-provided scaffolding with AI-assisted coding; all modeling and design decisions are my own.*
