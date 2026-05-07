---
title: "Learning LangChain with Local Models"
date: 2026-06-07
categories: [LangChain, Ollama]
tags: [LangChain, Ollama, Phi3, RAG, Local LLMs]
---

When I first started experimenting with LangChain, one thing became clear very quickly.

The biggest blocker for beginners is not the framework itself.

It is the constant dependency on paid API calls.

Every small experiment:
- testing prompts
- trying pipelines
- building mini RAG systems

starts consuming tokens and money.

That is where local models completely change the learning experience.

Instead of worrying about API costs, you can freely experiment, break things, rebuild, and understand how LLM applications actually work.

For anyone starting with LangChain, I strongly feel the best approach is:

## Start Local First

I recently began using Ollama with Phi-3 for this exact reason, and honestly it makes learning much more practical.

A few advantages immediately stand out:

- No API cost for experiments
- Faster iteration while learning
- Better understanding of model behavior
- Easy setup for testing LangChain concepts locally

For beginners, smaller local models are more than enough to learn:
- Prompting
- LangChain basics
- LCEL pipelines
- RAG fundamentals
- Simple agents

You do not need GPT-4 level infrastructure on Day 1.

You only need a setup that helps you learn consistently.

## Laptop Requirements

For anyone wondering about laptop requirements, here’s a simple guideline that works comfortably for small models like Phi-3.

### Minimum Recommended

- 16 GB RAM
- Intel i5 / Ryzen 5 or better
- 20–30 GB free storage

### Better Experience

- 32 GB RAM
- Apple Silicon (M1/M2/M3) or dedicated GPU
- SSD storage

## What I Am Using Local Models For

I am currently using local models mainly for:
- LangChain learning
- Prompt testing
- RAG experiments
- Pipeline understanding

## Setting Up Ollama

The setup process with Ollama is surprisingly simple.

### 1. Install Ollama

Download Ollama from the official website:

```text
https://ollama.com
```

### 2. Pull the Phi-3 Model

```bash
ollama pull phi3
```

### 3. Run the Model

```bash
ollama run phi3
```

Once the model starts, you can directly chat with it from the terminal.

That moment feels quite interesting the first time.

You realize the entire LLM is now running on your own laptop.

## What Comes Next

Connecting local models with LangChain using Python and building actual workflows on top of them.

That is what I’ll be exploring next.
