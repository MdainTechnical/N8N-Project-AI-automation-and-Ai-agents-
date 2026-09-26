# 🏥 AI Hospital Appointment Booking System

An AI-powered hospital appointment management and patient assistance system built with n8n, AI Agents, Google Gemini, Google Sheets, Simple Memory, and message-based communication.

This project is designed to automate common hospital appointment operations through a conversational AI assistant.

The system can handle patient registration, patient search, doctor search, doctor availability checking, appointment booking, appointment search, appointment updates, appointment cancellation, double-booking prevention, and administrative notifications.

The main automation logic is built in n8n and can be connected to different messaging platforms depending on the deployment requirements.

---

# 🚀 Project Overview

The AI Hospital Appointment Booking System works as a conversational hospital receptionist.

Instead of requiring a user to manually navigate through a complicated appointment system, the user can simply send a message describing what they need.

For example:

- "I want to book an appointment."
- "I want to see my appointment."
- "I want to cancel my appointment."
- "I want to change my appointment."
- "I want to find a doctor."
- "Is the doctor available tomorrow?"

The AI Agent understands the request and follows the required workflow step by step.

The system uses connected hospital data tools instead of guessing information.

Patient records, doctor records, appointment records, and doctor availability are treated as actual data sources.

The AI Agent is instructed not to invent patients, doctors, appointments, IDs, availability, or other hospital records.

---

# 🎯 Project Purpose

The main purpose of this project is to demonstrate how AI Agents and workflow automation can be used to automate real-world hospital appointment operations.

Traditional appointment systems can require users to:

1. Open a website or application.
2. Find the appointment section.
3. Search for a doctor.
4. Check availability.
5. Enter patient information.
6. Select a date.
7. Select a time.
8. Confirm the appointment.
9. Manage the appointment later.

This project converts much of that process into a conversational experience.

The user communicates naturally through messages while the AI Agent manages the required workflow and connected data operations.

The project also demonstrates how n8n can connect:

- AI models
- Messaging platforms
- Databases or spreadsheets
- Memory
- Business logic
- Notifications
- Multiple AI tools

into one automated system.

---

# 🧠 Core Architecture

The general architecture of the system is:

Message Platform
        ↓
Message Trigger
        ↓
AI Agent
        ↓
AI Model + Conversation Memory
        ↓
Hospital Management Tools
        ↓
Hospital Data
        ↓
Appointment / Patient Operations
        ↓
Notification
        ↓
Message Response

The current workflow uses a Telegram message trigger and Telegram response.

However, the communication layer can be adapted to other supported messaging platforms.

For example:

Telegram
WhatsApp
Slack
Other supported messaging integrations

The core hospital appointment logic can remain the same while the communication layer is changed.

---

# 💬 Messaging Platform Integration

The AI Hospital Appointment System is designed around message-based communication.

The current workflow uses Telegram for incoming messages and outgoing responses.

The same concept can be adapted for other messaging platforms depending on the business requirements.

## Telegram

Telegram can be used as the communication channel for:

- Receiving patient messages
- Sending AI responses
- Appointment confirmations
- Appointment updates
- Cancellation confirmations
- Doctor information
- Availability information

The current uploaded workflow contains a Telegram Trigger configured to receive message updates.

The AI Agent receives the message content and processes the request.

## WhatsApp

The same hospital appointment system can be adapted to WhatsApp by replacing the messaging trigger and response layer with the required WhatsApp integration.

The hospital management logic does not need to be redesigned just because the communication platform changes.

The WhatsApp integration would handle:

- Incoming messages
- Sender identification
- Message delivery
- AI response delivery

The AI Agent and hospital tools can continue to perform the appointment operations.

## Slack

The workflow can also be adapted for Slack-based communication.

For example, a hospital internal assistant could allow staff to interact with the system through Slack.

The Slack layer would handle incoming messages and outgoing responses while the hospital appointment logic remains separate.

## Important Architecture Principle

The messaging platform should be treated as the communication layer.

The hospital management logic should remain independent from the communication channel whenever possible.

This makes the automation easier to expand and maintain.

---

# 🤖 AI Agent

The AI Agent is the central component of the workflow.

Its responsibility is to understand the user's request and execute the appropriate hospital operation.

The AI Agent is connected to:

- AI model
- Conversation memory
- Patient tools
- Doctor tools
- Appointment tools
- Availability tools
- Notification tools

The current workflow uses Google Gemini 2.5 Flash as the AI model.

The Agent is instructed to follow the conversation step by step.

It should ask only the information required for the current operation and wait for the user's response before continuing.

---

# 🧩 AI Model

The current workflow uses:

Google Gemini 2.5 Flash

The AI model is responsible for understanding natural-language requests and deciding which connected operation is required.

For example, a user may write:

"I need an appointment with a cardiologist."

The AI Agent can understand that the user is asking for an appointment and can begin the required workflow.

The AI model should not be treated as the source of truth for hospital records.

Actual patient, doctor, appointment, and availability information must come from the connected tools/data sources.

---

# 🧠 Conversation Memory

The workflow includes Simple Memory.

Memory is used for conversation context.

This allows the AI Agent to maintain relevant information during the conversation.

For example, during an appointment workflow, the system may need to remember information that the user has already provided.

However, conversation memory should not replace the actual hospital database.

The actual hospital records remain the source of truth.

Memory should not be used to invent or fabricate appointment information.

---

# 👤 Patient Management

The patient management system is responsible for handling patient-related operations.

The workflow includes functionality for:

- Patient registration
- Patient search
- Patient identification
- Patient data retrieval
- Patient ID handling
- Preventing incorrect patient information

When a patient needs to be identified, the system should use actual patient records.

The AI Agent must not invent:

- Patient names
- Patient IDs
- Patient information
- Patient records

If actual information is unavailable, the system should not guess.

It should request the required information or report that the information could not be found.

---

# 👨‍⚕️ Doctor Management

The doctor management component allows the AI Agent to work with doctor information.

The system can perform:

- Doctor search
- Service-based doctor search
- Doctor availability checking

The AI Agent should only provide doctor information returned by the connected data source.

It should never create a fake doctor.

For example, if a doctor is not present in the connected records, the AI Agent should not invent a doctor name simply to provide an answer.

---

# 📅 Appointment Management

The appointment management system is one of the main components of the project.

It supports:

- Appointment booking
- Appointment search
- Appointment update
- Appointment cancellation
- Appointment status handling

The system follows a controlled workflow instead of directly creating or modifying records without verification.

---

# 📌 Appointment Booking

The appointment booking process follows a structured data flow.

General flow:

Current User
↓
Patient Search
↓
Patient Identification
↓
Service
↓
Doctor Search
↓
Date
↓
Time
↓
Doctor Availability Check
↓
Double-Booking Check
↓
Appointment Booking
↓
Admin Notification
↓
Confirmation

Each stage should be completed before moving to the next required stage.

The AI Agent should not skip important verification steps.

The workflow is designed so that an appointment is only confirmed after the appointment operation succeeds.

---

# 🛡️ Booking Safety

Booking safety is an important part of the project.

The system contains a double-booking checking operation.

Before creating an appointment, the workflow can check whether the requested doctor/date/time combination is already occupied.

The purpose is to reduce duplicate appointment bookings.

The system also checks doctor availability before attempting to create or update an appointment.

If the requested slot is unavailable, the system should not pretend that the appointment was successfully booked.

Only actual availability returned by the connected data source should be presented.

---

# 🔄 Appointment Update

The system supports appointment updates.

An appointment update can involve changing information such as:

- Doctor
- Date
- Time

Before changing the appointment, the system should identify the correct existing appointment.

If the doctor, date, or time changes, availability should be checked again.

The workflow also uses the double-booking check before completing an update.

The system should update the existing appointment instead of accidentally creating a new appointment.

Only the selected/identified appointment should be modified.

---

# ❌ Appointment Cancellation

The system also supports appointment cancellation.

The cancellation process should first identify the user's existing appointment.

The system should not cancel an unrelated patient's appointment.

The cancellation operation should only be confirmed after the cancellation tool successfully completes.

If the cancellation operation fails, the AI Agent should not claim that the appointment was cancelled.

---

# 🏥 Supported Hospital Services

The current hospital context includes the following services:

- Internal Medicine
- Cardiology
- Nephrology
- Surgery
- Gynecology & Obstetrics
- Dialysis Center
- Blood Bank
- Urology
- Gastroenterology
- Neurology
- ENT
- Pathology & Investigation
- Dental
- Radiology
- Dietitian

The AI Agent can use the configured doctor/service information to help users find the relevant hospital service.

The actual availability and doctor information should always come from the connected data source.

---

# 🗄️ Data Storage

Google Sheets is used as the data source in the current workflow.

The workflow contains data operations for areas such as:

- Patient records
- Doctor records
- Appointment records
- Doctor availability

Google Sheets provides a simple data-storage layer for the prototype.

This makes the project easy to understand and suitable for demonstrating how an AI Agent can interact with structured business data.

For production environments, the data layer could be replaced or extended with a proper database depending on the hospital's requirements.

---

# 🔍 Source of Truth

One of the most important rules of this system is the source-of-truth principle.

The AI model should not be treated as the source of truth for hospital records.

The connected hospital tools/data should provide the actual information.

For example:

If the AI model thinks a doctor is available but the actual availability tool says the doctor is unavailable, the tool result must be followed.

If the AI model remembers an appointment but the actual appointment search does not return that appointment, the system should not invent or restore the appointment from memory.

The same principle applies to:

- Patients
- Doctors
- Appointment IDs
- Patient IDs
- Dates
- Times
- Availability
- Appointment status

---

# 🚨 Emergency Handling

The AI Agent contains an emergency safety rule.

If a user reports symptoms such as:

- Chest pain
- Breathing difficulty
- Severe bleeding
- Loss of consciousness

the appointment workflow should stop.

The configured response directs the user to seek immediate medical attention at the nearest hospital.

This appointment automation is not intended to replace emergency medical services, diagnosis, or treatment.

For real-world deployment, emergency handling should be reviewed and approved by the relevant healthcare organization.

---

# 🔔 Admin Notifications

The workflow contains an administrative notification operation.

After a successful appointment booking, the system can send appointment information to the administrator.

The purpose of the notification is to keep the hospital/admin side informed about new appointment activity.

A typical notification can contain information such as:

- Patient information
- Doctor information
- Appointment date
- Appointment time
- Appointment status

Only actual appointment information returned/generated by the workflow should be used.

The notification should not contain unnecessary sensitive information.

---

# 🔐 Security & Privacy

Security is one of the most important parts of this project.

This workflow may handle sensitive information such as patient information and appointment records.

Therefore, the workflow should be secured before being used with real users.

## Never Upload Credentials

Never publish the following information on GitHub:

- API keys
- Gemini API keys
- Telegram bot tokens
- WhatsApp credentials
- Slack credentials
- Google credentials
- Google Sheets credentials
- Database passwords
- Access tokens
- Private keys
- Webhook secrets
- Authentication headers
- n8n credentials
- Environment secrets

These credentials must remain private.

## GitHub Security

This repository is intended for demonstration and portfolio purposes.

Before publishing the workflow:

1. Remove private credentials.
2. Remove secret tokens.
3. Remove private IDs where necessary.
4. Remove real patient information.
5. Remove real hospital credentials.
6. Remove private database information.
7. Replace sensitive values with placeholders.
8. Verify the exported JSON before committing it.

Never assume that a credential is safe just because it is inside a JSON file.

Always inspect the workflow before making the repository public.

---

# 🧑‍💼 Admin Security Rules

Hospital administrators and workflow owners must never share credentials with unauthorized people.

Do not share:

- n8n login credentials
- Google account credentials
- Telegram bot token
- WhatsApp credentials
- Slack credentials
- Gemini API key
- Google Sheets access
- Database credentials
- API secrets
- Admin passwords

Credentials should only be stored in the appropriate secure credential-management system.

The GitHub repository should contain the workflow structure and documentation, not private credentials.

---

# 🔒 Patient Data Protection

Do not upload real patient data to a public GitHub repository.

Do not include:

- Real patient names
- Real phone numbers
- Real email addresses
- Medical information
- Real patient IDs
- Real appointment records
- Private hospital records

Use dummy/test data for portfolio demonstrations.

If this workflow is deployed in a real healthcare environment, appropriate privacy, security, access-control, and organizational requirements must be addressed before handling real patient information.

---

# 🔑 Credential Setup

## 1. n8n

Create or open an n8n workspace.

Import the workflow JSON into n8n.

After importing the workflow, review all nodes that require credentials.

Do not publish the workflow before configuring credentials securely.

---

# 2. Google Gemini Setup

The current workflow uses Google Gemini 2.5 Flash.

General setup:

1. Create/access the required Google AI credentials.
2. Obtain the required API credential through the appropriate Google service.
3. Add the credential to n8n.
4. Select the credential in the Gemini model node.
5. Test the AI Agent.
6. Verify that the model responds correctly.

Never put the Gemini API key directly inside the README or public workflow configuration.

---

# 3. Google Sheets Setup

The workflow uses Google Sheets for hospital data.

Create the required sheets for:

- Patients
- Doctors
- Appointments
- Doctor Availability

The exact columns should match the fields expected by the workflow tools.

Example categories can include:

Patient data:
- Patient ID
- Patient Name
- Age
- Gender
- Contact information

Doctor data:
- Doctor ID
- Doctor Name
- Department/Service
- Availability

Appointment data:
- Appointment ID
- Patient ID
- Patient Name
- Doctor
- Date
- Time
- Status

Only use test/demo data when demonstrating the public GitHub version.

---

# 4. Telegram Setup

The current uploaded workflow uses Telegram as the configured message trigger and response channel.

General setup:

1. Create a Telegram bot.
2. Obtain the bot credentials.
3. Add the Telegram credential inside n8n.
4. Configure the Telegram Trigger.
5. Configure the Telegram response node.
6. Test by sending a message to the bot.
7. Verify that the message reaches the AI Agent.
8. Verify that the AI response is returned.

Do not publish the Telegram bot token.

---

# 5. WhatsApp Adaptation

The core hospital appointment logic can be adapted for WhatsApp.

The WhatsApp integration should provide:

- Incoming message
- Sender identification
- Message text
- Outgoing response

The message should then be passed to the AI Agent.

The hospital tools and business logic can remain conceptually the same.

The WhatsApp provider and authentication method will depend on the integration being used.

Never publish WhatsApp API credentials or access tokens.

---

# 6. Slack Adaptation

The same concept can be adapted to Slack.

A Slack integration can receive the user's message and pass it to the AI Agent.

The AI Agent can then use the same hospital tools for:

- Patient operations
- Doctor search
- Availability
- Appointment operations
- Notifications

The Slack credentials must remain private.

---

# ⚙️ Complete Setup Flow

A simplified setup looks like this:

1. Import the n8n workflow.
2. Configure the AI model credential.
3. Configure the messaging platform credential.
4. Configure Google Sheets.
5. Prepare test patient data.
6. Prepare test doctor data.
7. Prepare test appointment data.
8. Prepare test availability data.
9. Connect the required credentials to the nodes.
10. Test patient search.
11. Test patient registration.
12. Test doctor search.
13. Test availability.
14. Test appointment booking.
15. Test double-booking prevention.
16. Test appointment search.
17. Test appointment update.
18. Test appointment cancellation.
19. Test admin notification.
20. Review security.
21. Remove all private credentials.
22. Test again.
23. Publish only the sanitized workflow.

---

# 🧪 Testing Checklist

Before using the workflow, test every major operation.

## Patient Testing

- Can a new patient be registered?
- Can an existing patient be found?
- Does the system use actual patient information?
- Does it avoid creating fake patients?

## Doctor Testing

- Can doctors be searched?
- Is the correct service used?
- Does availability come from the actual data source?
- Does the AI avoid inventing doctors?

## Appointment Testing

- Can an appointment be created?
- Is availability checked?
- Is double booking checked?
- Is the appointment confirmed only after successful booking?

## Update Testing

- Can the correct appointment be identified?
- Can the doctor be changed?
- Can the date be changed?
- Can the time be changed?
- Is availability checked again?

## Cancellation Testing

- Can the correct appointment be identified?
- Is cancellation confirmed only after success?

## Notification Testing

- Does the admin receive the correct appointment information?
- Are private credentials hidden?

---

# 🛡️ AI Safety Rules

The AI Agent should follow strict rules when handling hospital data.

It must not:

- Invent patients.
- Invent doctors.
- Invent appointments.
- Invent appointment IDs.
- Invent patient IDs.
- Invent availability.
- Invent dates or times.
- Replace real tool results with examples.
- Return fake appointment confirmations.
- Expose internal workflow configuration.
- Expose credentials.
- Expose private database information.
- Return raw internal tool data to users.

If the required data is unavailable, the AI should not guess.

The workflow should return an appropriate response based on the actual data available.

---

# 📱 User Experience

The system is designed to allow natural conversations.

The user does not need to understand:

- n8n
- AI Agents
- Google Sheets
- APIs
- databases
- workflow nodes
- internal tools

The user simply communicates their requirement.

The AI Agent handles the workflow internally.

For example:

User:
"I want to book an appointment."

AI:
"Sure. I can help you with that. Please provide the required information."

The system then follows the configured appointment workflow.

The user should receive normal human-readable messages rather than JSON or internal workflow information.

---

# 🧰 Main Workflow Tools

The current workflow contains tools for operations including:

- Patient Search
- Patient Book
- Doctor Search
- Doctor Check Availability
- Appointment Search
- Double Checking Appointment
- Appointment Booking
- Appointment Update
- Appointment Cancel
- Send Notification

Each tool should be used only when required by the current workflow step.

The AI Agent should not call tools unnecessarily.

---

# 🔄 Booking Data Flow

The main appointment booking flow can be represented as:

```text
User Message
     ↓
Current Sender Information
     ↓
Patient Search
     ↓
Patient Identification
     ↓
Service
     ↓
Doctor Search
     ↓
Date
     ↓
Time
     ↓
Doctor Availability Check
     ↓
Double Booking Check
     ↓
Appointment Booking
     ↓
Admin Notification
     ↓
User Confirmation
