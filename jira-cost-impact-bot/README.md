
## 📄 `jira-cost-impact-bot/README.md`


# JiraDocBot – Automated Cost Impact Report from Slack + JIRA

`JiraDocBot` is a Slack bot designed to automate the extraction of JIRA ticket data mentioned in a Slack channel and generate a Word document report estimating cost impact, cloud regions, and timelines — especially useful during migrations and deployments.

---

## 🔧 Features

- Extracts JIRA ticket keys from a Slack channel
- Queries JIRA API for metadata including:
  - Summary
  - Cost impact estimation
  - Cloud regions
  - Change start/finish times
- Groups tickets by deployment status
- Generates a `.docx` formatted report (sample provided)

---

## 📁 Folder Contents

| File                          | Description                                          |
|-------------------------------|------------------------------------------------------|
| `change_request_pull_v1.py`   | Main script for data gathering & report generation  |
| `sample/Jira_Cost_Report.docx`| Sample output document                              |
| `requirements.txt`            | Python dependencies                                 |
| `README.md`                   | Project documentation                               |

---

## 🔐 Authentication & Tokens

You'll need:

- **Slack Bot Token** – generated when creating the bot in Slack
- **Slack Channel ID** – where the bot is installed
- **JIRA API Token** – generated from Atlassian (see steps below)
- **JIRA Email** – linked to the JIRA account with API access

> ⚠️ For credentials or troubleshooting, contact the platform maintainer.

---

## 🛠️ Setup Instructions

### 1. Clone the Repository

```bash
git clone git@github.com:your-org/PlatformOps_Automations.git
cd PlatformOps_Automations/jira-cost-impact-bot
````

### 2. Create and Activate a Python Virtual Environment (recommended)

```bash
python3 -m venv venv
source venv/bin/activate
```

### 3. Install Python Dependencies

```bash
pip install -r requirements.txt
```

---

## 🪪 How to Generate a JIRA API Token

1. Go to: [https://id.atlassian.com/manage-profile/security/api-tokens](https://id.atlassian.com/manage-profile/security/api-tokens)
2. Click **Create API Token**
3. Provide a label (e.g., `JiraDocBot`) and click **Create**
4. Copy the token immediately (you won’t be able to see it again)
5. Use this token along with your Atlassian email in the script configuration

---

## 🤖 How to Install a Slack Bot (if not already done)

1. Go to: [https://api.slack.com/apps](https://api.slack.com/apps)
2. Click **Create New App** → "From scratch"
3. Choose a name like `JiraDocBot` and select your Slack workspace
4. Under **OAuth & Permissions**:

   * Add `channels:history`, `chat:write`, and `channels:read` scopes
   * Install the app to your workspace
5. Copy the **Bot User OAuth Token**
6. Add your bot to the relevant channel in Slack

---

## ▶️ Running the Bot

Run the script:

```bash
python3 change_request_pull_v1.py
```

### Sample Output:

```
📥 Fetching Slack messages from past 7 days...
📆 Fetching messages from: 2025-06-17 to 2025-06-24
🔍 Extracting Jira keys from 20 messages...
🎯 Found 7 unique Jira tickets.
🔄 Fetching data for PE-62936...
...
📝 Writing results to Word document grouped by Status...
✅ Report saved as: Jira_Cost_Report.docx
```

---

## 📄 Sample Report

Check the sample output file:

```
sample/Jira_Cost_Report.docx
```

---

## 👤 Maintainer

This project uses private access tokens. Please contact the repo maintainer for help with token generation, access permissions, or error resolution.

---

## 📝 License

This automation is intended for internal platform operations and reporting. No third-party redistribution is permitted without written consent.

```
