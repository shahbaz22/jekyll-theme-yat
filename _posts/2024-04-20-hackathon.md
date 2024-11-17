---
layout: post
title: Agent based model to create legal documents
subtitle: Evidence house Gen AI hackathon
excerpt_image: /assets/images/legislation.png
categories: markdown
tags: [LLMs, agents]
---


As part of the Evidence House and No. 10 Downing Street Gen AI hackathon, our team of five was selected to tackle key challenges faced by government departments. We chose to focus on the creation of legislative text using LLMs (Large Language Models). The aim was to explore how AI could streamline drafting, formalizing, and proofreading legislation in a way that’s efficient and accurate, while allowing human oversight.

## An Agent-Based Approach to Legislative Drafting
The core of our approach revolved around an agent-based model, leveraging LLM agents—each responsible for a specific section of the legislative document. This modular system addresses several constraints typical of LLMs, like context size and output limits, while also allowing more precision by breaking down tasks into specialized sub-components.

We relied on Claude Opus from Anthropic for the LLM. The system functioned by integrating examples from two reference laws—focused on the regulation of sunbeds and smoking—to maximize diversity in our small sample. This technique, known as few-shot prompting, was key to ensuring the model understood the structure and tone of legal text.

<p style="text-align: center;">
<img src="{{ site.baseurl }}/assets/images/gen_ai_pitch_model.png" alt="Crepe">
  <figcaption style="text-align: center;">A workflow diagram illustrating the legislative drafting process. The system uses multiple AI agents working in parallel to transform an initial prompt into a finalised document, with opportunities for human review at each stage. The process includes a Section Coordinator agent that manages different workflows, with specialised agents handling drafting, formalising, and proof stages. While AI agents collaborate to refine and validate the legislative document, human experts can monitor and verify the outputs at each checkpoint before proceeding to the next stage, ensuring accuracy, compliance, and quality control. This human-in-the-loop approach combines AI efficiency with essential human oversight in the legislative drafting process.</figcaption>
</p>

## How It Worked

#### Input and Coordination:

The process began with an initial prompt outlining key features of the law. The first agent integrated the title and preliminary sections.

#### Drafting Sections:

Based on the input examples, subsequent agents generated relevant sections of the law, focusing on clauses, definitions, and regulatory conditions. This was done using about 40 Opus API calls.

#### Formalising and Proofreading:

Additional agents handled the formalisation and proofread the text for consistency, ensuring there were no duplicates or conflicts. The “human-in-the-loop” checks were crucial at each stage, allowing us to fine-tune outputs based on feedback from Ministry of Justice legal experts.

#### Explanatory Notes:

The same agent-based method was applied to generate explanatory notes, which are documents that explain the purpose of a Bill to MPs in the houses of parliament.In this case we leveraged contextual data from two external sources, namely the news-catcher API and Legislation API.

#### Key Benefits of the Approach:

1. **Modular & Scalable**: The agent-based system enables parallel processing, making it possible to draft large documents quickly while maintaining a high level of detail.
2. **Human Oversight**: By embedding checkpoints at each stage, the system allows for human intervention, ensuring that the final output is legally sound.
3. **Real-World Applications**: This model mimics the real-life legislative process, and was refined using feedback from domain experts (government legal advisors).
4. **Structured PDF output**: The output was structured in JSON and later converted into a formatted PDF document in the style of a piece of government legislation.

<p style="text-align: center;">
<img src="{{ site.baseurl }}/assets/images/example_leg.svg" alt="Crepe">
  <figcaption style="text-align: center;">An example piece of legislation created by this agent based model.</figcaption>
</p>


## Conclusion
Our approach centres on an agent-based model that employs Large Language Model (LLM) agents, with each agent specialising in distinct sections of legislative documents. This modular system effectively addresses common LLM constraints, such as context size and output limitations, whilst enabling enhanced precision through task specialisation.


## Project Contributors
We extend our gratitude to the core team members:
- Alun Rees
- Kevin Russling
- Tom Savage
- Jess Watson


