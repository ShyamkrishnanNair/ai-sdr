# 🤖 AI SDR - AI Accountant

An **AI-powered Sales Development Representative (SDR)** that automates the entire early-stage sales process on WhatsApp.  
From **first-touch outreach** to **lead qualification**, **demo scheduling/rescheduling**, **HubSpot updates**, and **WhatsApp notifications**, this system saves SDR time and boosts demo conversion rates.  

---

## 🚀 Features
- **First-Touch Automation** → Sends a personalized WhatsApp message when a new lead comes in.  
- **AI Conversation Handling** → Once the lead replies, the AI agent qualifies the lead, answers FAQs about AI Accountant, and manages scheduling.  
- **Demo Scheduling** → Books demos with both the lead and the assigned SDR, on Teams, and notifies both via WhatsApp.  
- **Rescheduling & Escalation** → Handles rescheduling and escalates complex queries to the SDR concerned.  
- **HubSpot Integration** →  
  - Updates deal stages (e.g. *Demo Scheduled*).  
  - Logs WhatsApp conversations as HubSpot notes.

---

## 📂 Workflow Files
| File Name                                | Description                                    |
|------------------------------------------|------------------------------------------------|
| `Official Whatsapp First Touch.json`     | Sends the initial WhatsApp message to new leads |
| `Whatsapp First Touch Reply Workflow.json` | Handles replies, qualification, and scheduling |
| `Demo Reminder Workflow.json`            | Sends a daily morning WhatsApp reminder of all demos scheduled for that day |
| `DNP Follow Up Workflow.json`            | Sends a WhatsApp follow-up when deal stage changes to DNP (Did Not Pick), re-engages the lead, and resumes AI SDR handling |


---

## 🔧 How to Import Workflows into n8n
1. Open **n8n** → go to **Workflow → Import from File**.  
2. Choose the `.json` workflow file from this repo.  
3. Update the credentials for WhatsApp, Airtable, HubSpot, and Calendar integrations.  
4. Save & Activate the workflow.  

---

## 📌 Example Flow
1. New Lead comes in via HubSpot → First-touch WhatsApp message is sent automatically.

2. Lead Replies → AI SDR takes over:
   - **If demo is requested** → schedules the demo, updates HubSpot deal stage, and notifies SDR + lead.  
   - **If general queries** → AI SDR answers questions about AI Accountant.  
   - **If rescheduling** → AI SDR cancels the old demo and books a new slot.  
   - **If complex queries / escalation** → AI SDR escalates to the assigned SDR and notifies them.  

3. If lead didn’t pick the call (DNP) →
   -  Deal stage changes to DNP.
   -  DNP Follow Up Workflow sends a WhatsApp re-engagement message.
   -  If the lead engages → AI SDR picks up the conversation again, qualifies, and reschedules.
   -  All rescheduled demos are logged in HubSpot with source DNP Follow Up for tracking.

4. After Deal stage is changed to Demo Conducted → AI SDR sends a personalized follow-up email from the SDR to the lead.

---

## 🌟 Impact
- Faster lead response times  
- Reduced manual follow-ups  
- Fewer scheduling conflicts  
- Improved demo conversion rates  

---

## 🛠️ Tools & Technologies Used

1. n8n → Core automation engine to connect HubSpot, WhatsApp, Airtable, Teams, and AI agent.
2. HubSpot CRM → Deal pipeline tracking, automation triggers, and lead management.
3. Meta Cloud API → Sending/receiving WhatsApp messages for SDR <> lead communication.
4. Zapier → Automatic meeting creation, rescheduling, and cancellations.
5. Airtable → Lead activity log, conversation history, and workflow storage.
6. AI Agent (Claude - Sonnet-4) → Handles natural language queries, demo scheduling logic, rescheduling, and escalation.

--- 

## Future Enhancements

1. **Smarter Scheduling** → AI SDR checks SDR availability and suggests multiple time slots instead of just booking directly.
2. **Lead Researcher** → Automatically gather contextual data from LinkedIn, company websites, and prior chat history when a lead comes in.
3. **Conversation Summarizer** → Generate summaries of all WhatsApp exchanges for SDRs.
4. **Database Expansion** → Build a centralized knowledge base for FAQs, lead behavior, and past conversations.
5. **Front-End Dashboard** → A UI for SDRs to monitor AI SDR performance, leads, and escalations.

---

## ⚠️ Note
This repo only contains **workflow JSONs**.  
Credentials and environment variables must be set up in your own n8n instance.  

---
