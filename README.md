# 🤖 AI Daily Productivity Planner

An AI-powered daily productivity planner built using **n8n**, **Google Gemini**, **Gmail**, **PostgreSQL**, and **Render**. The workflow automatically generates a personalized daily schedule and emails it every morning.

## ✨ Features

- ⏰ Automatic daily scheduling
- 🤖 AI-generated personalized study and productivity plan
- 📧 Sends the plan directly to Gmail
- ☁️ Runs 24/7 on Render
- 🗄️ PostgreSQL database support
- 🎯 Designed for students preparing for placements

## 🛠️ Tech Stack

- n8n
- Google Gemini API
- Gmail API
- PostgreSQL
- Render

## 🔄 Workflow

```
Schedule Trigger
      │
      ▼
Edit User Details
      │
      ▼
Google Gemini AI Agent
      │
      ▼
Send Email via Gmail
```

## 🚀 Setup

1. Import `Workflow.json` into n8n.
2. Configure your Google Gemini API credentials.
3. Configure Gmail OAuth credentials.
4. Activate the workflow.
5. Deploy n8n on Render.

## 📂 Repository Structure

```
AI-Daily-Planner/
├── Workflow.json
├── README.md
├── LICENSE
└── .gitignore
```

## 📌 Future Improvements

- Telegram and WhatsApp notifications
- Google Calendar integration
- Task completion tracking
- Weekly productivity reports
- Multiple user support

## 👨‍💻 Author

**Vigneshwaran**

- GitHub: https://github.com/Vignesh14007
- LinkedIn: https://www.linkedin.com/in/vigneshwaran14007/