# AI Lead Capture Automation (n8n + Gemini)

An automation that captures leads from a web form, labels them
Hot / Warm / Cold with AI, and sends an instant reply.

## Problem
Small businesses lose customers when leads are answered late or
never sorted by priority.

## Solution
Every new form submission is processed automatically, with no
manual work.

## How it works
1. Customer submits a Google Form
2. The response is saved in Google Sheets
3. n8n detects the new row (Google Sheets Trigger)
4. Gemini labels the lead and writes a one-line summary
5. The result is written back to the Sheet ("AI Result" column)
6. Gmail sends an automatic reply to the customer

## Tech Stack
n8n | Google Forms | Google Sheets | Gemini API | Gmail

## Screenshots


![Workflow](screenshots/workflow.png)




![Sheet result](screenshots/sheet.png)



## Demo
[Watch the demo video](paste-your-LinkedIn-post-link-here)

## AI Prompt Used
You are a lead assistant for a business.
Reply in the format:
Label: Hot, Warm, or Cold
Summary: one short sentence about this lead

## Setup
1. Create a Google Form with: Full Name, Phone Number,
   Email address, What do you need?, How soon do you need it?
2. Link the form to a Google Sheet and add a column "AI Result"
3. In n8n, import Lead Capture.json
4. Connect your own Google and Gemini credentials
5. Select your Sheet in the trigger and update nodes, then publish

## Challenges and Lessons
- Gemini free tier returns "too many requests" when many rows
  are sent at once; fixed with Retry On Fail
- Invalid emails in the form make the Gmail step fail, so
  input validation is needed
- Expressions must be dragged from the input panel to avoid
  field-name errors

## Future Improvements
- Telegram alert for Hot leads
- Different email for each label
- Email validation before sending

## Author
Farhad Ali Zahid, AIOps student
LinkedIn: www.linkedin.com/in/farhad-ali-zahid-99a846446

