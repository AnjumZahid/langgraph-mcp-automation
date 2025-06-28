# AI Agent with MCP: Weather and Email Automation (LangGraph + Groq)

This is an end-to-end AI automation project that demonstrates how to build a smart agent using **LangGraph** and **Model Context Protocol (MCP)** to:

-Get the current weather of any location  
-Send the weather update to an email address  
-Automatically select and use the correct tools via AI reasoning

---

## Demo Workflow

1. You ask: “What is the weather in Karachi?”
2. The LangGraph agent calls the `weather` tool server.
3. It gets the weather using the `wttr.in` API.
4. Then, the agent calls the `email` tool server and sends an email with the weather update.

---

## Project Structure

📁 project-root/
├── weather.py # Tool server for weather updates (MCP)
├── emailtool.py # Tool server for sending emails via Gmail SMTP (MCP)
├── client.py # LangGraph agent client using Groq (Qwen model)
├── .env # Environment variables (GROQ_API_KEY, EMAIL_APP_PASSWORD)
└── README.md # Project documentation

yaml
Copy
Edit

---

## Requirements

- Python 3.10+
- [Groq API Key](https://console.groq.com/)
- Gmail App Password (for email sending)

---

## Setup Instructions

### 1. Clone the Repo

```bash
git clone https://github.com/your-username/mcp-weather-email-agent.git
cd mcp-weather-email-agent
2. Create and Activate Virtual Environment (using uv)
bash
Copy
Edit
uv venv
source .venv/bin/activate    # On Windows: .venv\Scripts\activate
3. Install Dependencies
bash
Copy
Edit
uv pip install -r requirements.txt
Or manually install:

bash
Copy
Edit
uv pip install fastmcp langchain langgraph langchain-groq httpx python-dotenv
 .env File Example
Create a .env file in the root folder:

env
Copy
Edit
GROQ_API_KEY=your_groq_api_key_here
EMAIL_APP_PASSWORD=your_gmail_app_password_here
-How to Run
Step 1: Start MCP Tool Servers (in separate terminals)
Weather Tool Server

bash
Copy
Edit
python weather.py
Email Tool Server

bash
Copy
Edit
python emailtool.py
Step 2: Run the LangGraph AI Agent
bash
Copy
Edit
python client.py
You should see:

Weather response in terminal

Confirmation of email being sent

How It Works
Unified API in Client
The client sees all MCP tools through a unified tool schema.

You don’t have to know how each tool is built internally.

Unique APIs in Tool Servers
weather.py uses external API wttr.in

emailtool.py uses Gmail SMTP server

Internally different, but unified externally via FastMCP

Technologies Used
Component	Technology
AI Agent	LangGraph (ReAct agent)
LLM	Groq (Qwen-32b)
Tool Server	FastMCP
Email Service	Gmail SMTP
Weather API	wttr.in
Async HTTP	httpx
Env Management	python-dotenv

YouTube Tutorial
Watch the full tutorial: https://youtu.be/Z5S5eVHFH9I?si=MwpspN3e5daPtShN
AI Agent MCP Project - Weather + Email Automation

Contact
Author: Anjum Zahid
LinkedIn: linkedin.com/in/anjumzahid789
