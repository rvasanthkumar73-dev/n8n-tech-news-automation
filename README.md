# 🚀 AI Tech News Executive Briefing Agent

An automated, AI-powered intelligence workflow built using **n8n** and **Google Gemini 3.1 Flash Lite**. This agent automatically fetches live global tech RSS feeds, isolates high-impact updates involving major tech leaders (e.g., Elon Musk, Sundar Pichai, Satya Nadella), formats the insights into a responsive HTML newsletter with dynamic breaking-news highlight banners, and delivers a daily email briefing to mailboxes.

---

## 📌 Architecture & Workflow Pipeline

```text
[ Schedule Trigger (09:00 AM) ]
              │
              ▼
  [ HTTP Request (Google RSS) ]
              │
              ▼
   [ AI Agent + Gemini 3.1 ] ──► (Parses XML, extracts URLs, generates dynamic HTML)
              │
              ▼
    [ Send Email (SMTP) ]   ──► (Delivers formatted report to mailbox)

1. **Schedule Trigger:** Runs automatically every morning at 09:00 AM (configured for `Asia/Kolkata` timezone).
2. **HTTP Request Node:** Fetches raw global tech RSS XML data from Google News.
3. **AI Agent + LLM (Google Gemini):**
   * Parses raw RSS feeds and isolates the **Top 10** high-impact stories.
   * Extracts target direct article URLs using exact character-for-character matching rules.
   * Contextually evaluates breaking updates and dynamically highlights high-stakes items with light-blue visual containers.
   * Compiles the briefing using responsive, inline CSS HTML styling optimized for Gmail clients.
4. **Send Email Node:** Dispatches the rendered newsletter to subscriber mailboxes via SMTP.

---

## 🛠️ Tech Stack & Dependencies

* **Automation Engine:** [n8n](https://n8n.io/)
* **AI Model:** Google Gemini (`gemini-3.1-flash-lite` via `@n8n/n8n-nodes-langchain`)
* **Data Ingestion:** RSS / HTTP GET (XML format)
* **Email Delivery:** SMTP / Native Email Node
* **Templating:** Dynamic Inline HTML/CSS

---

## 🚀 Setup & Installation Instructions

### 1. Import Workflow into n8n
1. Download the `AI_Tech_News_Automation.json` file from this repository.
2. Open your local or hosted **n8n canvas**.
3. In the top-right menu, select **Workflows** > **Import from File**.
4. Upload `AI_Tech_News_Automation.json`.

---

### 2. Configure Credentials
Before activating the workflow, set up two connections in n8n:

1. **Google Gemini API Key:**
   * Double-click the **Google Gemini Chat Model** node.
   * Connect your `Google Gemini (PaLM) API` credential.
2. **SMTP / Email Account:**
   * Double-click the **Send an Email** node.
   * Attach your standard SMTP account or app-specific password credentials.

---

### 3. Customize Recipient & Sender
1. Open the **Send an Email** node parameters.
2. Update `fromEmail` and `toEmail` from `YOUR_EMAIL@gmail.com` to your target email addresses.
3. Turn on the **Active** switch in the top toolbar to enable the daily 9:00 AM trigger.

---

## 🔒 Security & Privacy Notice
* Sensitive API keys, OAuth tokens, and database passwords are **never stored** in n8n workflow exports.
* Before pushing customizations, verify that recipient email addresses are kept as configuration placeholders.

---

## 👨‍💻 Author
**Vasanth Kumar R**  
*Computer Science Undergraduate | Full-Stack & Automation Developer*  
* **Portfolio:** [vasanth-kumar-portfolio-sooty.vercel.app](https://vasanth-kumar-portfolio-sooty.vercel.app/)  
* **GitHub:** [@rvasanthkumar73-dev](https://github.com/rvasanthkumar73-dev)
