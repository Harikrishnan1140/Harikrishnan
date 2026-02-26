---
layout: post
title: "Building Your First AI Chatbot with LangChain - What I Learned"
date: 2026-02-26 00:00:00 +0000
---

Hello readers! This is my second day of learning LangChain, and today's topic was LLM fundamentals. I'm learning from a book called *Learning LangChain* by Mayo Oshin and Nuno Campos.

## What is an LLM?

LLM stands for **Large Language Model**, where:

- **Large** refers to the size of the model in terms of the data and parameters it was trained on.
- **Language** refers to the algorithm, which is trained to receive written text and produce output as written text.

I use AI to generate responses in my day-to-day life, but while reading through the book, I came to appreciate the importance of prompting and the different techniques used for it. Let's walk through some examples.

---

## Prompting Techniques

### 1. Zero-Shot Prompting

In zero-shot prompting, we ask the model to produce a desirable output without giving it any examples.

**Prompt:**
> Classify the sentiment of the following text as Positive, Negative, or Neutral.
> Text: "The new software update completely broke my workflow and I lost hours of work."
> Sentiment:

**Response:** Negative

---

### 2. Chain-of-Thought (CoT)

In Chain-of-Thought prompting, we ask the model to think through a problem step by step before arriving at an answer. This technique is particularly useful for multi-step reasoning tasks.

**Prompt:**
> A store has 48 apples. They sell 3 bags of 6 apples each, then receive a shipment of 20. How many apples do they have now? Think step by step.

**Response:**
1. **Initial quantity:** The store starts with 48 apples.
2. **Apples sold:** They sell 3 bags × 6 apples = 18 apples.
3. **After selling:** 48 − 18 = 30 apples remaining.
4. **New shipment:** They receive 20 more apples.
5. **Final quantity:** 30 + 20 = **50 apples**.

---

### 3. Retrieval-Augmented Generation (RAG)

RAG involves supplying the model with relevant context directly in the prompt, allowing it to answer questions it otherwise wouldn't have access to.

**Prompt:**
> As of Q3 2024, Acme Corp reported revenue of $4.2B, up 12% YoY, driven by cloud services. How did Acme Corp perform last quarter?

**Response:**
> Acme Corp performed well in the last quarter. They reported revenue of $4.2 billion, marking a 12% year-over-year increase driven primarily by their cloud services.

---

### 4. Tool Calling

In this technique, we give the model access to an external function it can invoke to answer a question.

**Prompt:**
> You are an assistant with access to the following tool:
>
> **Tool Name:** `get_weather`
> **Description:** Gets the current weather for a city
> **Parameters:** `{ "city": "string" }`
>
> User question: What's the weather like in Tokyo right now?

**Response:**

The model would call the tool like this:
```json
{
  "tool": "get_weather",
  "parameters": { "city": "Tokyo" }
}
```

Simulated result:
```json
{
  "temperature": "15°C",
  "weather_condition": "Partly Cloudy",
  "humidity": "60%",
  "wind_speed": "15 km/h"
}
```

> The weather in Tokyo right now is partly cloudy with a temperature of 15°C, 60% humidity, and a wind speed of 15 km/h. Sounds like a pleasant day!

---

### 5. Few-Shot Prompting

Here we give the model a few examples of the desired input-output pattern, allowing it to learn a new task without additional training or fine-tuning. There are two types:

#### Static Few-Shot Prompting
A small, fixed list of examples is included in every prompt.

**Prompt:**
> Convert these sentences to a formal tone:
>
> Casual: "Can't make it to the meeting, sorry!"
> Formal: "I regret to inform you that I am unable to attend the meeting."
>
> Casual: "This report is kinda hard to read."
> Formal: "The report is somewhat difficult to comprehend."
>
> Casual: "Hey, just wanted to check if you got my email?"
> Formal: ???

**Response:**
> "I am writing to inquire whether you have received my previous email."

---

#### Dynamic Few-Shot Prompting
Instead of a fixed list, the model is given a larger bank of examples and selects the most relevant ones for each query.

**Example bank:**
- *Complaints:* "We messed up the order, our bad." → "We sincerely apologize..."
- *Scheduling:* "Can't make it to the meeting." → "I regret I am unable to attend..."
- *Follow-ups:* "Did you get my email?" → "I wanted to follow up..."
- *Feedback:* "This report is hard to read." → "The report is difficult to comprehend..."
- *Introductions:* "Just wanted to say hi!" → "I am reaching out to introduce myself..."

**User Input:** "Wanna grab a quick call sometime this week?"

**Response:**
> "Would it be possible to schedule a brief call with you at your convenience this week?"

---

That's a wrap on Day 2! Each of these techniques has its own strengths, and understanding when to use them is key to getting the most out of large language models.
