# AI Dental Receptionist (ElevenLabs + n8n)

A voice agent that answers calls for a dental clinic, answers questions from a knowledge base, books appointments in Google Calendar, and sends a confirmation email.

## How it works
Caller -> ElevenLabs voice agent -> n8n webhook -> Google Calendar event -> Gmail confirmation

## Features
- Natural voice conversation
- Answers questions about services, prices, hours, and policies
- Collects name, phone, email, service, date, and time
- Creates a Google Calendar event automatically
- Sends a confirmation email to the caller

## Tech stack
- ElevenLabs Agents (voice)
- n8n (automation)
- Google Calendar and Gmail

## Files
- system_prompt.md: the agent's instructions
- clinic_info.txt: knowledge base (upload it to ElevenLabs)
- book_appointment.json: n8n workflow (import it into n8n)

## Setup
1. Create an agent in ElevenLabs and paste in system_prompt.md as the System prompt.
2. Upload clinic_info.txt to the agent's Knowledge Base.
3. In n8n, import book_appointment.json and connect your own Google Calendar and Gmail accounts.
4. Publish the n8n workflow and copy the Production URL.
5. In ElevenLabs, add a webhook tool named book_appointment (POST) with the Production URL and these 6 string parameters:
   - name
   - phone
   - email
   - service
   - date (format YYYY-MM-DD)
   - time (format HH:MM)
6. Publish the agent and test it with the Test AI agent button.

## Notes
- Never commit API keys or passwords.
- The clinic details in clinic_info.txt are sample data for demo purposes.

## Status
Working end to end: booking, calendar event, and confirmation email.

## Next
- Lead qualification agent
- Appointment reminders