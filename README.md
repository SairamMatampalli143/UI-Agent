# UI-Agent
To automate the execution, monitoring, and reporting of a Java Selenium Cucumber UI automation suite using an AI agent controlled through a Telegram bot interface, without relying on external schedulers like Jenkins or Task Scheduler.


## 🤖 AI Automation Agent for Cucumber Test Suites

This is an intelligent AI-powered automation agent that integrates with **Telegram** to:

* ✅ Trigger UI automation test suites remotely
* 📩 Report real-time execution status
* 🧠 Summarize failed test steps with AI suggestions
* 🗃️ Maintain historical test data and reports
* 🔁 Keep the agent alive and interactive without external orchestrators

---

### 🛠 Features

* 🔘 **Telegram Command Interface**
  Run suite, stop suite, check agent/suite status using natural language commands or inline buttons.

* 📊 **Test Report Summarization**
  Parses `cucumber-json-report.json` and gives pass/fail summaries.

* 🧠 **Failure Analysis with GPT**
  Uses AI (Gemini, OpenRouter, etc.) to analyze failed steps and provide possible fixes.

* 📍 **Multi-user Access**
  Authorized users (via chat ID) can securely interact with the agent.

* 🕒 **Heartbeat System**
  Sends a ping every 3 hours to show the bot is alive.

---

### 📁 Project Structure

```
ai-automation-agent/
├── ai_agent.py                   # Core bot and execution logic
├── failure_summarizer.py        # Summarization and AI analysis
├── config.json.example          # Sample config
├── requirements.txt             # Dependencies
├── .gitignore
└── README.md
```

---

### ⚙️ Configuration

#### 🔐 `config.json.example`

Rename this file to `config.json` and fill with your values:

```json
{
  "bot_token": "YOUR_TELEGRAM_BOT_TOKEN",
  "chat_ids": ["123456789", "987654321"],
  "command_trigger": "run suite",
  "suite_command": "your_suite_command_here",
  "working_directory": "path/to/your/project",
  "report_path": "path/to/cucumber-json-report.json"
}
```

---

### 💬 Telegram Bot Commands

| Command              | Description                  |
| -------------------- | ---------------------------- |
| `run suite`          | Triggers the test suite      |
| `stop suite`         | Terminates running suite     |
| `check agent status` | Confirms bot is alive        |
| `check suite status` | Shows current suite progress |
| `menu` / `/start`    | Shows command help           |

---

### 🧠 AI Failure Summarization

After each suite run:

* Failed steps from the report are extracted
* Error stack trace is summarized
* GPT (e.g., Gemini / OpenRouter) suggests potential fixes

Example output in Telegram:

```
❌ Failure Summary:
1. Feature: X
   Scenario: Y
   Step: Z
   Error: Element not clickable at location...

🧠 AI Suggestion:
Try waiting for element visibility or use JS executor click.
```

---

### 🧪 Sample Test Report Format

The agent expects a Cucumber JSON report like:

```json
[
  {
    "name": "Feature Name",
    "elements": [
      {
        "name": "Scenario Name",
        "steps": [
          {
            "name": "Step Name",
            "result": {
              "status": "failed",
              "error_message": "java.lang.AssertionError: ..."
            }
          }
        ]
      }
    ]
  }
]
```
### 💡 Notes

* Designed for long-running UI suites (e.g., Selenium, Cucumber)
* Works without Jenkins, cron jobs, or external schedulers
* AI agent stays alive and fully autonomous


