# 🤖 AI Daily Productivity Planner

<p align="center">

<b>{=html}An AI-powered daily planning and reminder workflow built
with n8n, Google Gemini, and Gmail.</b>{=html}

</p>

<p align="center">

<img src="https://img.shields.io/badge/n8n-Automation-FF6D5A?style=for-the-badge&logo=n8n&logoColor=white">{=html}
<img src="https://img.shields.io/badge/Google%20Gemini-LLM-4285F4?style=for-the-badge&logo=google&logoColor=white">{=html}
<img src="https://img.shields.io/badge/Gmail-Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white">{=html}
<img src="https://img.shields.io/badge/Docker-Local%20Deployment-2496ED?style=for-the-badge&logo=docker&logoColor=white">{=html}

</p>
```
## 📌 Overview

**AI Daily Productivity Planner** is an automated personal productivity
system built with **n8n**, **Google Gemini**, and **Gmail**.

It automatically generates a structured daily plan from a user's goals,
routine, college schedule, and priorities, then delivers the plan
through email.

``` text
Schedule Trigger
       ↓
Personal Context
       ↓
AI Agent
       ↓
Google Gemini
       ↓
Generated Daily Plan
       ↓
Gmail
       ↓
Daily Email
```

## 🎯 Problem

Students and learners often manage several competing priorities such as
placement preparation, DSA, AI/ML learning, college work, projects,
exercise, and personal development.

A fixed timetable does not automatically turn these priorities into a
focused daily plan. This project automates that process using an AI
agent.

## 💡 Solution

The workflow provides the AI with structured personal context:

-   Goal
-   College schedule
-   Wake-up time
-   Sleep time
-   Priorities
-   Personal background

The AI then creates a realistic daily schedule with time blocks,
estimated durations, breaks, Top 3 priorities, and a short motivational
tip.

## ✨ Features

-   ⏰ Automated daily scheduling
-   🧠 AI-powered planning with Google Gemini
-   🎯 Goal-oriented task prioritization
-   📚 Java DSA, AI/ML, placement, project and college-work planning
-   🏃 Exercise and break inclusion
-   🥇 Top 3 daily priorities
-   📧 Automatic Gmail delivery
-   🔧 Fully customizable personal profile
-   🐳 Local n8n deployment using Docker
-   🔐 OAuth 2.0 authentication for Gmail

## 🏗️ Workflow

### 1. Schedule Trigger

The workflow is configured to run every day at **7:30 AM**.

### 2. Edit Fields

The node stores the personal context used by the AI:

``` text
Name
Goal
College Timing
Wake-up Time
Sleep Time
Priorities
About Me
```

### 3. AI Agent

The AI Agent receives that context and generates the daily plan.

The current planning rules include:

``` text
- Give today's plan only.
- Assume today is a normal weekday.
- Placement preparation is the highest priority.
- Include Java DSA.
- Include AI/ML learning.
- Include one personal project.
- Include exercise.
- Keep breaks between study sessions.
- Don't overload the schedule.
- Give estimated durations.
- End with Top 3 priorities.
- Finish with one short motivational tip.
```

### 4. Google Gemini

The current workflow uses:

``` text
Gemini 2.5 Flash
```

### 5. Gmail

The generated AI output is sent through Gmail.

Current email subject:

``` text
TO DO
```

## 🧰 Tech Stack

  Technology                   Purpose
  ---------------------------- ---------------------------------------
  **n8n**                      Workflow automation and orchestration
  **Google Gemini**            AI-based daily plan generation
  **Gmail API / OAuth 2.0**    Automated email delivery
  **Docker**                   Local n8n deployment
  **JavaScript Expressions**   Dynamic n8n data mapping
  **Markdown**                 AI-generated plan formatting

## 🔄 End-to-End Architecture

``` text
                    ┌──────────────────────┐
                    │   Schedule Trigger   │
                    │       7:30 AM        │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │     Edit Fields      │
                    │ Goals + Schedule +   │
                    │ Priorities + Profile │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │      AI Agent        │
                    │   Planning Logic     │
                    └──────────┬───────────┘
                               │
                     ┌─────────▼─────────┐
                     │  Gemini 2.5 Flash │
                     │    LLM Model      │
                     └─────────┬─────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │        Gmail         │
                    │  Daily Plan Email   │
                    └──────────────────────┘
```

## 🚀 Setup

### Prerequisites

-   Docker
-   n8n
-   Google account
-   Google Gemini API access
-   Gmail account

### Run n8n locally

``` bash
docker run -d   --name n8n   -p 5678:5678   -v ~/.n8n:/home/node/.n8n   docker.n8n.io/n8nio/n8n
```

Open:

``` text
http://localhost:5678
```

### Import the workflow

Import:

``` text
Workflow.json
```

from the n8n interface.

## 🔑 Google Gemini Setup

Create a Gemini API credential in n8n and add your API key.

The workflow uses:

``` text
models/gemini-2.5-flash
```

Never commit your API key to GitHub.

## 📧 Gmail OAuth Setup

Create a Google OAuth client with:

``` text
Application type:
Web application
```

For local n8n, use this exact **Authorized redirect URI**:

``` text
http://localhost:5678/rest/oauth2-credential/callback
```

Do not place the callback path under **Authorized JavaScript origins**.

Then configure the matching:

``` text
Client ID
Client Secret
```

inside the n8n Gmail OAuth credential and complete Google authorization.

## ⚙️ Customize the Planner

Edit the **Edit Fields** node to change the personal context.

Example:

``` text
Goal:
Get placed in a top product-based company

Wakeup:
6:00 AM

Sleep:
11:30 PM

College:
Monday to Friday, 9:00 AM to 4:00 PM

Priorities:
Placement Preparation,
Java DSA,
AI and Machine Learning,
Project Development,
College Work
```

You can replace these values with your own schedule and goals.

## 🧠 Prompt Design

The AI Agent is designed as a personal productivity coach rather than a
generic chatbot.

The prompt gives the model:

``` text
Personal Context
       +
Goals
       +
Available Schedule
       +
Priorities
       ↓
AI Planning
       ↓
Structured Daily Plan
```

This keeps the AI output focused on the user's actual routine.

## 📁 Project Structure

``` text
AI-Daily-Planner/
│
├── Workflow.json
├── README.md
└── .gitignore
```

The main application logic is represented by the n8n workflow.

## 🧪 Testing

Test the workflow in this order:

``` text
1. Schedule Trigger
        ↓
2. Edit Fields
        ↓
3. AI Agent
        ↓
4. Gemini Response
        ↓
5. Gmail
        ↓
6. Received Email
```

Before activating the workflow, verify that:

-   Gemini credentials are valid.
-   Gmail OAuth is authorized.
-   The AI Agent produces output.
-   Gmail receives the generated plan.

## 🔐 Security

Never commit:

``` text
API keys
OAuth client secrets
OAuth access tokens
Passwords
Private credentials
.env files
```

Use GitHub for the workflow configuration and documentation, not private
secrets.

## 💰 Cost

The project is designed for a low-cost/local development setup.

-   n8n can run locally with Docker.
-   Gemini usage depends on the Google account/API limits and applicable
    pricing.
-   Gmail usage is subject to Google's account and API limits.

Always check the provider's current limits before production use.

## 📊 Current Implementation

### Implemented

-   [x] n8n workflow
-   [x] Daily scheduled trigger
-   [x] Personal profile configuration
-   [x] AI Agent
-   [x] Google Gemini integration
-   [x] Daily schedule generation
-   [x] Top 3 priorities
-   [x] Gmail integration
-   [x] Gmail OAuth 2.0
-   [x] Docker-based local n8n setup
-   [x] Workflow import/export

### Planned

-   [ ] Persistent task history
-   [ ] PostgreSQL task storage
-   [ ] Task completion tracking
-   [ ] Calendar integration
-   [ ] Weekly productivity reports
-   [ ] Feedback-based planning
-   [ ] Productivity dashboard
-   [ ] Multi-user support
-   [ ] Production deployment

## 🗺️ Roadmap

### Phase 1 --- Core Automation

``` text
Daily Trigger
      ↓
AI Planning
      ↓
Email Delivery
```

### Phase 2 --- Persistent Memory

Store:

``` text
Daily Plans
Tasks
Completed Tasks
Missed Tasks
User Preferences
Productivity History
```

### Phase 3 --- Adaptive Planning

``` text
Previous Plans
      ↓
Completion History
      ↓
User Feedback
      ↓
Next Daily Plan
```

### Phase 4 --- Calendar Integration

The planner can consider:

``` text
Classes
Meetings
Deadlines
Exams
Events
```

### Phase 5 --- Productivity Dashboard

``` text
Today's Tasks
      ↓
Completion Rate
      ↓
Weekly Progress
      ↓
Learning Hours
      ↓
Project Progress
```

## 🌟 What This Project Demonstrates

This project demonstrates the practical combination of:

-   AI / LLM integration
-   Prompt engineering
-   Agent-based workflow design
-   Workflow automation
-   API integration
-   OAuth 2.0
-   Email automation
-   Docker
-   Configuration management
-   Secret management

The main idea is:

> **Turn an AI model into an automated productivity system instead of
> using it only as a chatbot.**

## 📚 Learning Outcomes

### AI & LLM

-   LLM-based planning
-   Prompt engineering
-   AI Agent workflows
-   Context-aware generation

### Automation

-   Scheduled workflows
-   Node-based orchestration
-   Data passing between nodes
-   Automated actions

### APIs & Authentication

-   Google APIs
-   OAuth 2.0
-   API credentials
-   Redirect URIs

### DevOps

-   Docker
-   Local service deployment
-   Workflow import/export

### Software Engineering

-   Modular workflow design
-   Configuration separation
-   Credential management
-   Workflow testing

## 🔮 Future Vision

The long-term goal is to evolve the project from a simple daily planner
into a personal AI productivity agent.

``` text
Understand Goals
       ↓
Understand Schedule
       ↓
Check Previous Progress
       ↓
Prioritize Tasks
       ↓
Generate Today's Plan
       ↓
Send Reminders
       ↓
Track Completion
       ↓
Learn From Feedback
       ↓
Improve Tomorrow's Plan
```

## 👨‍💻 Author

**Vigneshwaran S**

B.Tech Information Technology\
Kongu Engineering College, Tamil Nadu, India

-   GitHub: https://github.com/Vignesh14007
-   LinkedIn: https://linkedin.com/in/vigneshwaran14007/

## 📄 License

This project is intended as a learning and portfolio project.

If you add a license file, update this section to match the selected
license.

------------------------------------------------------------------------

```{=html}
<p align="center">
```
`<b>`{=html}Built with ❤️ using n8n + Google Gemini + Gmail`</b>`{=html}
```{=html}
</p>
```
```{=html}
<p align="center">
```
⭐ Star the repository if you find it useful.
```{=html}
</p>
```
