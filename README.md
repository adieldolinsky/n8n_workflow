# AI Customer Support Agent (n8n)

An n8n AI customer support agent equipped with strict security guardrails that handles general queries and automatically escalates billing issues via Gmail.

## Architecture & Workflow

This n8n workflow operates as a secure, automated customer support system through the following pipeline:

1. **Chat Trigger**  
   The process starts by receiving the user's input through a standard chat interface.

2. **Guardrails (Security Layer)**  
   Before reaching the main agent, the input is evaluated by a Guardrails node powered by a Gemini model. This strictly blocks any investment advice requests or jailbreak attempts, ensuring the core agent is only exposed to safe prompts.

3. **AI Agent**  
   Safe messages are routed to the main AI Agent, which follows a strict system prompt to act solely as a customer support representative. It utilizes a memory node to maintain conversation context across multiple interactions.

4. **Gmail Tool (Action Execution)**  
   If the agent detects a billing or payment issue, it automatically activates the connected Gmail tool to send a formatted alert. This alert contains the user's original message and is sent directly to the human support team for further review.

## Technologies Used
* **n8n** - Workflow automation and agent orchestration
* **Google Gemini** - Large Language Model powering both the Guardrails and the core Agent
* **Gmail API** - Integrated action tool for issue escalation
