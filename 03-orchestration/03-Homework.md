## Module 3 Homework: AI Orchestration with Kestra

> Submission by Shanice W

ATTENTION: At the end of the submission form, you will be required to include a link to your GitHub repository or other public code-hosting site. This repository should contain your code for solving the homework. If your solution includes code that is not in file format, please include these directly in the README file of your repository.

> It's possible your answers won't match exactly. If so, select the closest one

## Prerequisites

Before starting this homework, ensure you have:

1. Completed the [Module 3 lessons](../../../03-orchestration/README.md) — the questions reference flows and concepts covered there
2. Kestra running locally with API keys configured (see the [Setup](../../../03-orchestration/lessons/03-setup.md) lesson) -- this includes the Gemini API key, which is also required for the AI Copilot
3. Imported all flows from the `03-orchestration/flows/` directory (covered in the Setup lesson)

## Question 1: Context Engineering

Try the following experiment:

1. Open ChatGPT in a private browser window: https://chatgpt.com
2. Enter this prompt: "Create a Kestra flow that loads NYC taxi data from CSV to BigQuery"
3. Then, use Kestra's AI Copilot with the same prompt

After trying the same prompt in ChatGPT vs Kestra's AI Copilot, what is the primary reason AI Copilot generates better Kestra flows?

- AI Copilot uses a more powerful model
- AI Copilot has access to current Kestra plugin documentation [X]
- AI Copilot uses more tokens
- AI Copilot has internet access

## Question 2: RAG vs No RAG

Run both `1_chat_without_rag.yaml` and `2_chat_with_rag.yaml` in the Kestra UI. Read the execution logs for each.

The non-RAG response about Kestra 1.1 features is best described as:

- Accurate and specific, matching the actual release notes
- Vague, generic, or fabricated — the model guesses from training data [X]
- Empty — the model refuses to answer without context
- Identical to the RAG version

## Question 3: Token usage — short summary

Run `4_simple_agent.yaml` with `summary_length = short` (leave the other inputs as defaults).

Open the execution logs and find the token usage logged by the `log_token_usage` task.

What is the approximate **output** token count for `multilingual_agent`?

- 5-15 tokens
- 60-100 tokens [X]
- 200-400 tokens
- 500+ tokens

This is the summary that is output with a short summary length:
> Kestra is an open-source orchestration platform that uses declarative YAML for workflow definition and offers a no-code interface for automation. It supports custom use cases via plugins and scripts, and its flexible design makes it suitable for various applications like data engineering and business process automation. In the LLM Zoomcamp bonus module, Kestra is used to explore how AI can accelerate workflow development through features like AI Copilot and autonomous agents.

![Screenshot of log_token_usage after running multilingual agent with short summary length](03-orchestration/assets/log_token_usage_short.png)

## Question 4: Token usage — long summary

Run `4_simple_agent.yaml` again with `summary_length = long`.

Compare the `multilingual_agent` output token count to your result from Question 3. Roughly how many times more output tokens does the long summary use?

- About the same (within 20%)
- 2-5x more [X]
- 10-20x more
- 50x more

This is the summary that is output with a long summary length:
> Kestra is an open-source orchestration platform for defining workflows declaratively in YAML, supporting both developers and non-developers with a no-code interface. It ensures workflows are versioned, governed, secure, and auditable, and offers extensibility through plugins and custom scripts. The platform is designed for scalable growth, allowing users to start with simple workflows and integrate more complex elements like Python scripts, Docker containers, or advanced branching logic as needed. Kestra is suitable for various applications, including data engineering, ETL pipelines, and business process automation. In the context of the LLM Zoomcamp, Kestra's capabilities are being explored in a bonus module to demonstrate how AI, specifically through AI Copilot, RAG, and autonomous agents, can enhance and accelerate workflow development for production-ready LLM applications.

Visually we can see the diffence in outputs, but we can also see it in the token usage:

![Screenshot of log_token_usage after running multilingual agent with long summary length](03-orchestration/assets/log_token_usage_long.png)

## Question 5: Modifying a flow

Open `4_simple_agent.yaml` in the Kestra flow editor. Find the `english_brevity` task and change its prompt from asking for exactly **1 sentence** to asking for exactly **3 sentences**.

Save the flow, then run it with `summary_length = long`.

Compare the `english_brevity` output token count to the original 1-sentence version (also with `summary_length = long`). How do they compare?

- About the same (within 20%)
- 2-4x more [X]
- 5-10x more
- 10x+ more

![Screenshot of log_token_usage after updating english_brevity task](03-orchestration/assets/token_usage_english_brevity.png)


## Question 6: Best Practices

Based on what you learned in this module, for production workflows requiring deterministic, repeatable results with strict compliance requirements (e.g., financial reporting, workflows in highly regulated industries), which approach is most appropriate?

- Always use AI agents for maximum flexibility and adaptation
- Use traditional task-based workflows for predictability and auditability [X]
- Use only RAG without agents for better performance
- Use web search tools exclusively to ensure current data

## Learning in Public

We encourage everyone to share what they learned. This is called "learning in public".

Read more about the benefits [here](https://alexeyondata.substack.com/p/benefits-of-learning-in-public-and) and in the [course's learning in public guide](https://datatalks.club/docs/courses/zoomcamp-logistics/learning-in-public/).

### Example post for LinkedIn

Tag [@Alexey Grigorev](https://www.linkedin.com/in/agrigorev/) and [@DataTalksClub](https://www.linkedin.com/company/datatalks-club/) in your post - we'll like and comment to give your post more reach.

```
🚀 Module 3 of LLM Zoomcamp by @DataTalksClub complete!

Just finished Module 3 - AI Orchestration with @Kestra. Learned how to:

✅ Engineer context so the LLM gets the right information
✅ Ground answers in real data with RAG
✅ Build AI agents that decide which tools to call
✅ Orchestrate multi-agent systems

Here's my homework solution: <LINK>

Following along with this amazing free course by @Alexey Grigorev - who else is learning to build with LLMs?

You can sign up here: https://github.com/DataTalksClub/llm-zoomcamp/
```

### Example post for X

```
🤖 Module 3 of LLM Zoomcamp done!

- AI orchestration with @kestra_io
- Context engineering
- RAG-grounded answers
- AI agents & multi-agent systems

My solution: <LINK>

Free course by @Al_Grigor & @DataTalksClub: https://github.com/DataTalksClub/llm-zoomcamp/
```

## Submitting the Solutions

* Form for submitting: https://courses.datatalks.club/llm-zoomcamp-2026/homework/hw3
* Check the link above to see the due date