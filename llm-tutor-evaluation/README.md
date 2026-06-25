# AI SAT Tutor + LLM-as-Judge Benchmark

A Socratic SAT tutor that never gives away the answer, paired with an LLM-as-judge benchmark that scores tutor responses against an explicit rubric.

## What it does
Two linked pieces of applied-AI work:

1. **A Socratic tutor bot** — an LLM (`gpt-5-nano`) prompted to help low-income high-school
   students prepare for the SAT *without ever handing over the answer*, using hints and
   checkpoint questions instead.
2. **An evaluation benchmark** — an **LLM-as-judge** harness that scores the tutor's responses
   against an explicit rubric, so "is this tutor actually good?" becomes measurable rather than
   a matter of vibes.

The design choice at the center is the **alignment trade-off**: a prompt strict enough to never
leak answers can become useless, so the tutor is tuned to stay helpful while resisting
answer-extraction — and the benchmark is built to *detect* when it fails.

## Stack
Python, OpenAI API, Pydantic (structured outputs), pandas

## Results
Implements a multi-turn tutor with a hint/checkpoint pedagogy, then a benchmark that generates and scores responses on a 4-criterion rubric (accuracy, clarity, no-answer-giving, support). Centers the alignment trade-off between strictness and usefulness, and red-teams the prompt for answer-leakage.

## Running it
Open `llm_tutor_and_benchmark.ipynb` in Jupyter or Google Colab. Requires `OPENAI_API_KEY`.

```bash
export OPENAI_API_KEY="sk-..."   # if the notebook's API sections are used
```

---
*Course project for Harvard Kennedy School DPI-681, "Public Problem Solving with Generative AI." Built on course-provided scaffolding with AI-assisted coding; all modeling and design decisions are my own.*
