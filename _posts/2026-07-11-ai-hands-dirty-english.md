---
layout: post
title: "Hands-on Guide: Getting Started with LLM API Integration"
date: 2026-07-11 10:30:00 +0530
categories: [ai, programming]
tags: [ai, python, openai, llm, tools]
field: "AI (Artificial Intelligence)"
language: "English"
section: "Hands dirty with AI"
description: "A practical guide to connecting and interacting with Large Language Model APIs using Python."
image: "https://images.unsplash.com/photo-1677442136019-21780efad99a?auto=format&fit=crop&w=600&q=80"
---

Large Language Models (LLMs) are transforming how we build software applications. Integrating them into your code allows you to perform summaries, translations, sentiment analyses, and even write automated coding assistants. In this hands-on lab, we will connect to an LLM provider using Python.

## Prerequisites
Make sure you have Python installed on your local machine, and then install the required package:

```bash
pip install openai python-dotenv
```

## Step 1: Setting Up Environment Variables
Create a file named `.env` in your project root to securely store your API keys:

```ini
OPENAI_API_KEY=your_actual_api_key_goes_here
```

## Step 2: Writing the Connection Script
Create a file named `llm_client.py` and write the following code:

```python
import os
from openai import OpenAI
from dotenv import load_dotenv

# Load key from .env file
load_dotenv()

# Initialize Client
client = OpenAI(
    api_key=os.getenv("OPENAI_API_KEY")
)

def ask_assistant(prompt):
    try:
        response = client.chat.completions.create(
            model="gpt-4o-mini",
            messages=[
                {"role": "system", "content": "You are a helpful programming assistant."},
                {"role": "user", "content": prompt}
            ],
            max_tokens=150,
            temperature=0.7
        )
        return response.choices[0].message.content.strip()
    except Exception as e:
        return f"An error occurred: {e}"

# Test Run
if __name__ == "__main__":
    test_prompt = "Write a python function to check if a number is prime."
    print("Sending prompt to assistant...")
    result = ask_assistant(test_prompt)
    print("\nAssistant Response:")
    print(result)
```

## Step 3: Run the Script
Execute the python script from your terminal:

```bash
python llm_client.py
```

You should see a fully generated response containing the prime number checker function! You can easily tweak the `temperature` parameter (closer to `0` for structured outputs, closer to `1` for creative ideas) to suit your specific application goals.
