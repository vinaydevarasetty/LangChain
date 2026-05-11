---
title: "Day 3 - Understanding Prompt Templates in LangChain"
date: 2026-05-12
categories: [LangChain, Ollama, Generative AI]
tags: [LangChain, Prompt Engineering, Ollama, Phi-3, Local LLMs]
---

# Day 3: Understanding Prompt Templates in LangChain

In my previous post, we successfully interfaced with **Phi-3** using LangChain. It was a great "Hello World" moment, but a limitation quickly became obvious: **The prompts were hardcoded.**

```python
response = model.invoke("Explain cloud computing in simple terms")

This works for a one-off test, but if you are building a chatbot, a Q&A system, or a document assistant, the input is constantly changing. We can't manually rewrite the prompt logic for every user interaction.This is where Prompt Templates come in.Why Use Prompt Templates?Prompt Templates allow us to create reusable structures with placeholders. Think of them as the "f-strings" of the LLM world. Instead of static text, we define a blueprint that can accept dynamic values.The Problem vs. The SolutionAspectHardcoded PromptsPrompt TemplatesMaintenanceHigh (Change every line)Low (Change the template once)ScalabilityDifficultHigh (Reusable across modules)Clean CodeMessy/RedundantOrganized and StructuredSetting Up the EnvironmentThe stack remains the same as Day 2. We are utilizing local resources to keep the development fast and cost-effective.Ollama (Serving the model)Phi-3 (The LLM)LangChain (The Orchestrator)Make sure your local model is active:Bashollama run phi3
Implementation: Creating Your First TemplateHere is how we translate a raw prompt into a dynamic template using ChatPromptTemplate.Pythonfrom langchain_core.prompts import ChatPromptTemplate
from langchain_community.chat_models import ChatOllama

# 1. Initialize the local model
model = ChatOllama(model="phi3")

# 2. Define a reusable template with a {placeholder}
prompt = ChatPromptTemplate.from_template(
    "Explain {topic} in simple terms"
)

# 3. Fill the placeholder dynamically
formatted_prompt = prompt.invoke(
    {"topic": "cloud computing"}
)

# 4. Execute and display
response = model.invoke(formatted_prompt)
print(response.content)
Breaking Down the LogicChatPromptTemplate: This class is the factory for our prompts.{topic}: This is the placeholder. It tells LangChain to expect a variable named "topic" later.prompt.invoke({...}): This merges your template with your data. LangChain converts this into the final string: "Explain cloud computing in simple terms" before sending it to Phi-3.From "Experiment" to "Application"The real power shows when you connect this to user input. Instead of hardcoding "cloud computing," your code now looks like actual software development:Pythonuser_interest = input("What do you want to learn about? ")
formatted_prompt = prompt.invoke({"topic": user_interest})
Whether the user asks about Cricket, Data Engineering, or LangChain, the underlying structure remains consistent and professional.Pro-Tip: Prompt Templates aren't just about saving keystrokes; they are about Prompt Engineering. As your prompts grow into 50-line instructions with specific "system" and "human" roles, having them organized in templates is the only way to stay sane.Final ThoughtsDay 3 marks the shift from manual interaction to structured automation. The responses from Phi-3 remain impressive for a local model, and the workflow is starting to feel like a production-ready pipeline.Next Up: We’ll stop manually passing data between the prompt and the model. It’s time to look at LCEL (LangChain Expression Language) to chain these components into a seamless flow.
