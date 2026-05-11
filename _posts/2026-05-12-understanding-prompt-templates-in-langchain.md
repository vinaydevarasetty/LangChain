---
title: "Day 3 - Understanding Prompt Templates in LangChain"
date: 2026-05-12
categories: [LangChain, Ollama, Generative AI]
tags: [LangChain, Prompt Engineering, Ollama, Phi-3, Local LLMs]
---

# Day 3: Understanding Prompt Templates in LangChain

After interacting with Phi-3 using LangChain in the previous step, one thing started becoming obvious very quickly.

The prompts were getting hardcoded everywhere.

For example:

```python
response = model.invoke(
    "Explain cloud computing in simple terms"
)

This works perfectly fine for small experiments.

But the moment we want to build something dynamic, the approach starts becoming difficult to manage.

Imagine building:

a chatbot
a Q&A system
a document assistant

In all these cases, the input changes constantly.

We cannot keep rewriting prompts manually every single time.

This is where Prompt Templates become useful.

Prompt Templates allow us to create reusable prompts with placeholders that can accept dynamic values.

Instead of writing fixed prompts repeatedly, we can define a structure once and reuse it with different inputs.

That makes the application cleaner and much easier to scale later.

The setup remains exactly the same as Day 2.

We still use:

Ollama
Phi-3
LangChain

The only new concept introduced today is the Prompt Template.

Ensure Phi-3 is Running

Before starting, ensure Phi-3 is running locally.

ollama run phi3
Creating Your First Prompt Template

Now let us create our first prompt template.

from langchain_core.prompts import ChatPromptTemplate
from langchain_community.chat_models import ChatOllama

# Initialize the local model
model = ChatOllama(model="phi3")

# Create a reusable prompt template
prompt = ChatPromptTemplate.from_template(
    "Explain {topic} in simple terms"
)

# Fill the placeholder dynamically
formatted_prompt = prompt.invoke(
    {"topic": "cloud computing"}
)

# Send prompt to model
response = model.invoke(formatted_prompt)

# Print response
print(response.content)

At first glance, this may look slightly longer compared to the previous examples, but the idea is actually very simple.

Let us understand it step by step.

Understanding the Prompt Template

The first new concept is:

ChatPromptTemplate

This helps us create reusable prompts.

Inside the template:

"Explain {topic} in simple terms"

{topic} acts like a placeholder.

We can replace it with:

cricket
AI
data engineering
LangChain
cloud computing

or anything else dynamically.

Next comes this part:

prompt.invoke({"topic": "cloud computing"})

Here we are passing the actual value for the placeholder.

LangChain then converts the template into a final prompt like this:

Explain cloud computing in simple terms

This formatted prompt is then sent to the model.

Why This Starts Feeling Like Real Application Development

One thing I liked while experimenting with Prompt Templates is how naturally they fit into real application development.

For example, imagine taking input directly from a user.

user_input = "machine learning"

Now we can dynamically generate prompts like this:

formatted_prompt = prompt.invoke(
    {"topic": user_input}
)

This is the point where the workflow starts feeling more like actual software development instead of isolated AI experiments.

Trying Different Topics

I also tried a few different topics while testing:

{"topic": "cricket"}
{"topic": "data engineering"}
{"topic": "LangChain"}

The responses were surprisingly decent for a small local model.

What Prompt Templates Actually Solve

One thing that became clear during this exercise is that Prompt Templates are not really about reducing typing.

They are about introducing structure.

As prompts become larger and more detailed later, having a reusable template system becomes extremely important.

Without templates:

prompts become messy
code duplication increases
maintaining applications becomes difficult

With templates:

prompts remain reusable
applications become dynamic
workflows become easier to manage

This also explains why prompt engineering becomes such an important part of LLM applications.

The model output depends heavily on how clearly and consistently prompts are structured.

Final Thoughts

Overall, Day 3 felt like the point where the interaction became more organized and reusable instead of manually writing prompts every time.

The next step is where things become even more interesting.

Instead of manually passing:

prompt
model
output

we will start connecting them together into simple pipelines using LCEL.****
