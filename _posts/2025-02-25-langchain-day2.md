
---
layout: default
title: Building Your First AI Chatbot with LangChain — What I Learned
---

# Building Your First AI Chatbot with LangChain — What I Learned

Hello readers! This is my second day of learning LangChain, and today's topic was LLM fundamentals through LangChain.

For context, I'm learning from a book called *Learning LangChain* by Mayo Oshin and Nuno Campos.

---

## What is an LLM?

LLM stands for **Large Language Model**, where:

- **Large** refers to the size of the model in terms of the data and parameters it was trained on.
- **Language** refers to the algorithm, which is trained to receive written text and produce output as written text.

I use AI to generate responses in my day-to-day life, but while reading through the book, I came to appreciate the importance of prompting and the different techniques used for it. Let's walk through some examples.

---

## Prompting Techniques

### Zero-Shot Prompting

In zero-shot prompting, we ask the model to produce a desirable output without giving it any examples. I used OpenAI as my platform for this experiment.

**Prompt:**

```
Classify the sentiment of the following text as Positive, Negative, or Neutral.
Text: "The new software update completely broke my workflow and I lost hours of work."
Sentiment:
```

**Response:** Negative

---

*More techniques to come as I continue learning!*
