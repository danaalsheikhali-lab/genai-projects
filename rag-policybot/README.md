# PolicyBot — RAG for Evidence-Based Policy

A retrieval-augmented generation assistant grounded in five RCTs on Housing First, designed to surface uncertainty and trade-offs instead of one-size-fits-all advice.

## What it does
A retrieval-augmented generation (RAG) assistant that helps policymakers engage with
research evidence. It is grounded in a curated base of five randomized controlled trials on
**Housing First** interventions for homelessness, and is deliberately designed to *surface
uncertainty and trade-offs* rather than hand down one-size-fits-all recommendations.

**Pipeline:** parse evidence into structured records → embed each study
(`text-embedding-3-small`) → retrieve the top-k most relevant studies for a query via
cosine similarity → generate a grounded, appropriately-hedged answer (`gpt-5-mini`).

## Stack
Python, OpenAI API (embeddings + chat), Pydantic, NumPy

## Results
Builds an embedding index over a curated evidence base, retrieves the top-k relevant studies via cosine similarity, and generates grounded, source-citing answers that proved more evidence-bound and better-hedged than a plain LLM.

## Running it
Open `rag_policybot.ipynb` in Jupyter or Google Colab. Requires `OPENAI_API_KEY`.

```bash
export OPENAI_API_KEY="sk-..."   # if the notebook's API sections are used
```

---
*Course project for Harvard Kennedy School DPI-681, "Public Problem Solving with Generative AI." Built on course-provided scaffolding with AI-assisted coding; all modeling and design decisions are my own.*
