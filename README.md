# Company Research Assistant – AI Agent Built Using n8n + OpenAI
An AI agent to aid marketing team in doing research for potential clients.
## Problem Statement
Sales teams need to research a company before outreach: what the company does, its products, industry, size, challenges, risks, and why it might need the product being sold.
This research process is manual, time-consuming, and varies in quality across team members.

This project solves that problem by building a conversational AI Agent that automatically generates an Account Plan for any company.
The agent can:

Research the company using external sources (Wikipedia tool).

Generate a detailed, structured account plan.

Hold a natural conversation with the user.

Update specific sections like Opportunities / Risks upon request.

Handle confused, efficient, and off-topic users gracefully.

The system is implemented entirely in n8n using the LangChain-based AI Agent + OpenAI GPT models, and the workflow JSON acts as the “codebase”.

## Solution Overview
This AI Agent:

Accepts user queries through an n8n Chat Trigger.

Uses the AI Agent (Tools Agent) node to orchestrate tool usage and reasoning.

Fetches real company information using the Wikipedia Tool.

Uses the OpenAI Chat Model (gpt-5-mini) for summarization, reasoning, and structured account plan generation.

Returns a clean Markdown Account Plan with predefined sections.

Supports section-level updates using a previous_plan input.

This makes it a real “agentic system” rather than a single-step LLM call.

<img width="543" height="273" alt="Screenshot 2025-11-25 121720" src="https://github.com/user-attachments/assets/ec8bf80d-94ea-48c5-9d0a-b8f2f60baf2b" />

## Architecture
Nodes Used (from JSON)

Chat Trigger – starts the workflow when a message is received.

AI Agent (Tools Agent) – core logic that decides how to research and generate output.

OpenAI Chat Model – GPT-5-mini used for reasoning and text generation.

Wikipedia Tool – retrieves factual company information from Wikipedia.

## Account Plan Structure
The agent always outputs:

1. Company Overview

2. Products / Services

3. Industry & Market Position

4. Company Size / Stage

5. Problems the Company is Solving

6. Why They Might Need Our Product

7. Recommended Sales Approach

8. Opportunities

9. Risks / Red Flags

10. Key Stakeholders

11. Next Steps

## Setup Instructions
1. Requirements
   - n8n Cloud OR self-hosted n8n
     
   - OpenAI API key with access to GPT-5-mini
   
   - The JSON workflow file from this repo
   
2. Import Workflow
   - Open n8n
   - Go to Workflows → Import
   - workflows/Company Research Assistant.json
   - Save.

3. Configure OpenAI credentials

