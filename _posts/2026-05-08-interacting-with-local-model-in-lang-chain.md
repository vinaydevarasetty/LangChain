---
title: "Using LangChain with Local Models"
date: 2026-05-08
categories: [LangChain, Ollama]
tags: [LangChain, Ollama, Phi3, Python, Local LLMs]
---

After setting up Ollama and running Phi-3 locally, the next step was understanding how to interact with the model using Python instead of the terminal.

This is where LangChain starts becoming useful.

Until now, the interaction was very manual.

Open terminal → type prompt → wait for response.

That works well for experimentation, but if we want to build applications, chatbots, or RAG pipelines, we need a way to interact with the model programmatically.

LangChain helps simplify this process.

One thing I liked immediately about LangChain is that it provides a common interface to work with different models.

Whether the model comes from:
- OpenAI
- Ollama
- another provider

the overall development experience remains quite similar.

For learning purposes, using a local model like Phi-3 creates a very comfortable setup because we can experiment freely without worrying about API costs.

## Verifying the Local Model

First, make sure Ollama is already installed and Phi-3 is running locally.

You can verify it using:

```bash
ollama run phi3
```

If the model starts successfully, you are ready for the next step.

## Installing LangChain

Now install LangChain and the required community package.

Open terminal and run:

```bash
pip install langchain langchain-community
```

Once the installation is complete, create a new Python file or open a Jupyter notebook.

## Connecting LangChain with Ollama

Add the following code:

```python
from langchain_community.chat_models import ChatOllama

# Initialize the local Phi-3 model
model = ChatOllama(model="phi3")

# Send a prompt to the model
response = model.invoke(
    "Explain cloud computing in simple terms"
)

# Print the response
print(response.content)
```

## Understanding the Code

Let’s understand what is happening step by step.

### Importing ChatOllama

```python
from langchain_community.chat_models import ChatOllama
```

This acts like a bridge between LangChain and the locally running model.

### Initializing the Model

```python
model = ChatOllama(model="phi3")
```

Here we are telling LangChain:

“Use the Phi-3 model that is already running through Ollama.”

### Sending a Prompt

```python
response = model.invoke(...)
```

The `.invoke()` method is very important.

For now, think of it as:

“Send input to the model and receive a response.”

### Printing the Output

```python
print(response.content)
```

This prints only the generated text returned by the model.

## Experimenting with Prompts

At this stage, I spent some time experimenting with different prompts.

For example:

```python
response = model.invoke(
    "Explain what a data engineer does"
)
```

```python
response = model.invoke(
    "Explain LangChain for beginners"
)
```

```python
response = model.invoke(
    "Explain cricket using simple language"
)
```

One interesting thing I noticed while using local models is that you start observing the actual behavior of the LLM much more closely.

You can see:
- response speed
- token generation
- differences in output quality
- how prompts influence answers

This learning experience feels much more practical compared to only using cloud APIs.

## Small Issues I Faced

Initially, there were a few moments where the model would not respond.

Most of the time, Ollama was simply not running in the background.

In those cases, rerunning:

```bash
ollama run phi3
```

fixed the issue immediately.



“building with AI using code.”

The next step is making prompts dynamic and reusable using Prompt Templates.
