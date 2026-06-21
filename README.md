ResolveIQ — AI Support Ticket Router 🎫🤖


Automatically classify, route, log, and reply to customer support emails in under 10 seconds — no human triage needed.



⭐ If this project helped you or gave you ideas, consider starring the repo!


🚀 What It Does

ResolveIQ is an end-to-end AI automation workflow that takes a raw customer support email and:


Reads the incoming email via Gmail
Classifies it by category (Billing / Technical / General) and urgency (1–10) using OpenAI
Routes it to the right team channel on Slack with a full structured ticket
Logs the ticket record in Airtable for tracking
Replies to the customer instantly with a personalised AI-written email
Displays everything on a clean no-code frontend built with Lovable


All of this happens automatically, in under 10 seconds, the moment an email arrives.


❌ Problem It Solves

Small support teams waste hours every day:


Manually reading and sorting incoming emails
Deciding which team should handle which ticket
Writing the same generic acknowledgment replies over and over
Dropping tickets because nothing was logged or tracked


ResolveIQ eliminates all of that. Every email is handled instantly, consistently, and correctly — without a human touching it.


⚙️ How It Works

Customer Email
      ↓
Gmail Trigger (Get many messages)
      ↓
Email Analyze (OpenAI) → Classifies category, urgency, team, summary
      ↓
IF Node → Filters unread/new emails only
      ↓
      ├──→ Code Node → Formats structured Slack ticket
      │         ↓
      │    Create Record (Airtable) → Logs ticket
      │         ↓
      │    Send Message (Slack) → Notifies assigned team
      │
      └──→ Reply Node (OpenAI) → Generates personalised customer reply
                ↓
          Reply to Message (Gmail) → Sends reply in same thread


🛠️ Tech Stack

ToolPurposen8nWorkflow automation engineOpenAI (GPT-4o)Email classification + reply generationGmailEmail trigger + sending repliesSlackTeam notifications and routingAirtableTicket logging and trackingLovableNo-code frontend dashboard


📋 AI Classification Output

The Email Analyze node returns structured JSON for every ticket:

json{
  "category": "Billing",
  "urgency": 7,
  "urgency_reason": "Customer is being charged incorrectly",
  "assigned_team": "Billing Team",
  "summary": "Customer reports unexpected charge on their account",
  "customer_email": "customer@example.com"
}


🖥️ Setup Instructions

Prerequisites


n8n instance running (local or cloud)
OpenAI API key
Gmail account with OAuth connected
Slack workspace with a bot token
Airtable account with a base set up


Steps


Download the workflow JSON

Click resolveiq-workflow.json in this repo
Click "Download raw file" (top right of the file view)



Import into n8n

Open your n8n instance
Go to Workflows → Import
Upload the downloaded resolveiq-workflow.json
The entire workflow will rebuild itself automatically



Reconnect your credentials

Gmail OAuth → connect your Gmail account
OpenAI API key → add your key
Slack Bot Token → connect your workspace
Airtable API key → connect your account



⚠️ Credentials are never included in the export for security reasons, so you'll need to add your own.




Update node references

In the Airtable node: update your Base ID and Table name
In the Slack node: update your channel ID
In the Email Analyze node: update the prompt fields if needed



Activate the workflow

Toggle the workflow from Inactive → Active
Send a test support email and watch it run end-to-end


📸 Screenshots

<img width="1466" height="678" alt="Screenshot 2026-06-21 at 5 48 00 AM" src="https://github.com/user-attachments/assets/7bd6d462-2a4a-4d02-8e2e-d7c8c8a708e9" />
<img width="1466" height="678" alt="Screenshot 2026-06-21 at 5 48 00 AM" src="https://github.com/user-attachments/assets/e7072c9d-565e-46f6-afec-2423f70631f4" />



🎥 Demo


https://www.linkedin.com/posts/aman5511_n8n-workflowautomation-automation-ugcPost-7474253392043851776-ZOC7/?utm_source=social_share_send&utm_medium=member_desktop_web&rcm=ACoAAE0bGwUBjYN0-BX6B7Sahd4h-Mr2JKyeDoc



📁 Files in This Repo

resolveiq-ai-support-router/
├── resolveiq-workflow.json     # n8n workflow export
├── screenshots/
│   ├── workflow-canvas.png
│   └── lovable-frontend.png
└── README.md


👨‍💻 Author

Aman Yadav
BCA Graduate | AI Automation Developer
Building real-world LLM-powered systems with n8n, OpenAI & Anthropic



📄 License

MIT License — free to use, modify, and build on top of.



