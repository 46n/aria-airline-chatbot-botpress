# ARIA — Airline AI Customer Support Chatbot

> AI-powered airline chatbot built on Botpress — handles flight status, booking management, baggage support, travel policies, and human-agent escalation through a structured menu-driven conversation design.

![Botpress](https://img.shields.io/badge/Built%20with-Botpress-1A1A2E)
![Type](https://img.shields.io/badge/Type-Conversational%20AI-6C63FF)
![Dev](https://img.shields.io/badge/Development-Low%20code%20%2F%20No%20code-43A047)

---

## What Is ARIA?

**ARIA** (Airline Response and Inquiry Assistant) is an AI airline customer support chatbot built in [Botpress](https://botpress.com). It was developed as part of an Introduction to Artificial Intelligence course project and cleaned for portfolio presentation.

ARIA simulates a realistic airline support experience. A passenger interacts with ARIA via webchat, provides their details, then navigates a structured main menu to get help. Under the hood, ARIA combines three layers to respond intelligently:

| Layer | What it does |
|---|---|
| **Semantic knowledge base** | `.txt` files defining airline entities, relationships, policies, and Q&A patterns — fed to Botpress's AI for retrieval-based responses |
| **Structured data tables** | CSV tables for real-time-style lookups of flight status, booking records, and customer details |
| **Conversation workflows** | Botpress flow nodes with AI-assisted transitions that route passengers between service menus, validate inputs, and trigger escalation |

The chatbot is deployed as a Botpress webchat widget embedded in a static website — no backend infrastructure required.

---

## Conversation Flow

```
Passenger opens webchat
  └── Customer intake (name, booking ref, email)
        └── Main menu (AI-assisted routing)
              ├── Flight Status       → lookup via flight-status table
              ├── Booking Management  → lookup via bookings + customers tables
              ├── Baggage Support     → KB-driven responses + policy rules
              ├── Travel Policies     → autonomous KB retrieval
              ├── Other Help          → general KB + escalation trigger
              └── Human Escalation    → when confidence is low or user requests it
```

---

## Knowledge Base

Eleven structured `.txt` documents train Botpress's AI on airline-specific domain knowledge. Each file covers a distinct topic area so retrieval stays focused:

| File | Covers |
|---|---|
| `overview.txt` | Chatbot scope and main service areas |
| `core-knowledge-model.txt` | Major airline entities and their relationships |
| `passenger-contact-and-travel-documents.txt` | Passenger identity, contact, and travel document support |
| `booking-payment-and-refund-support.txt` | Booking, payment, refund, cancellation, and modification queries |
| `ticket-and-baggage-support.txt` | Ticket, seat, and baggage-related responses |
| `flight-airport-aircraft-terminal-and-gate.txt` | Flight status, airport, terminal, gate, and aircraft information |
| `conversation-policy-and-validation-rules.txt` | Input validation, clarification prompts, and safe conversation rules |
| `escalation-policy.txt` | Conditions and procedure for escalating to a human agent |
| `semantic-relationships-representation.txt` | Airline concepts encoded as semantic network triples |
| `qa-retrieval-chunks.txt` | Retrieval-optimised Q&A patterns for common queries |
| `travel-policies-and-passenger-compliance-rules.txt` | Travel policy and passenger compliance rules |

---

## Data Tables

Three CSV files act as ARIA's structured data layer — Botpress queries these to return specific records rather than relying on the knowledge base alone:

| File | Purpose |
|---|---|
| `bookings-table.csv` | Sample booking records for validation and management flows |
| `customers-table.csv` | Sample customer records for intake and identification |
| `flight-status-table.csv` | Sample flight records for status lookup responses |

---

## Architecture Diagrams

### Semantic Network

ARIA's knowledge is modelled as a semantic network — entities (passenger, flight, booking, ticket, baggage) connected by typed relationships. These diagrams informed how the knowledge base documents were structured and how the AI retrieves coherent answers.

| | |
|---|---|
| ![Main semantic diagram](diagrams/main-semantic-relationship-diagram.png) **Main** — top-level airline entity relationships | ![Passenger diagram](diagrams/passenger-semantic-relationship-diagram.png) **Passenger** — passenger → document, contact, booking links |
| ![Flight diagram](diagrams/flight-semantic-relationship-diagram.png) **Flight** — flight → airport, terminal, gate, aircraft links | ![Payment & Booking diagram](diagrams/payment-and-booking-semantic-relationship-diagram.png) **Payment & Booking** — booking → payment, refund, cancellation links |
| ![Ticket & Baggage diagram](diagrams/ticket-and-baggage-semantic-relationship-diagram.png) **Ticket & Baggage** — ticket → seat, baggage, allowance links | |

### Conversation Flowcharts

Botpress workflow diagrams showing branching logic, validation checkpoints, and escalation triggers for each service menu:

<p align="center">
  <img src="diagrams/customer-details-and-main-menu-flowchart.png" alt="Customer intake and main menu flowchart" width="800">
</p>
<p align="center"><em>Customer intake → main menu routing</em></p>

<p align="center">
  <img src="diagrams/flight-status-menu-flowchart.png" alt="Flight status flowchart" width="800">
</p>
<p align="center">
  <img src="diagrams/booking-management-menu-flowchart.png" alt="Booking management flowchart" width="800">
</p>
<p align="center">
  <img src="diagrams/baggage-service-menu-flowchart.png" alt="Baggage service flowchart" width="800">
</p>
<p align="center">
  <img src="diagrams/other-help-menu-flowchart.png" alt="Other help and escalation flowchart" width="800">
</p>

---

## Screenshots

### Customer Intake and Main Menu

<p align="center">
  <img src="screenshots/customer-details-and-main-menu-screenshot-1.png" alt="Customer intake step 1" width="700">
</p>
<p align="center">
  <img src="screenshots/customer-details-and-main-menu-screenshot-2.png" alt="Customer intake step 2" width="700">
</p>

ARIA collects the passenger's name, booking reference, and email before presenting the main menu. AI transitions then route the passenger to the correct service flow based on their selection.

---

### Flight Status

<p align="center">
  <img src="screenshots/flight-status-menu-screenshot.png" alt="Flight status menu" width="700">
</p>

Passenger provides a flight number. ARIA queries `flight-status-table.csv` and returns departure time, gate, and current status.

---

### Booking Management

<p align="center">
  <img src="screenshots/booking-management-menu-screenshot.png" alt="Booking management menu" width="700">
</p>

Validates the passenger against `bookings-table.csv` and `customers-table.csv` before allowing modifications.

---

### Baggage Service

<p align="center">
  <img src="screenshots/baggage-service-menu-1.png" alt="Baggage service part 1" width="700">
</p>
<p align="center">
  <img src="screenshots/baggage-service-menu-2.png" alt="Baggage service part 2" width="700">
</p>
<p align="center">
  <img src="screenshots/baggage-service-menu-3.png" alt="Baggage service part 3" width="700">
</p>

Baggage queries are handled by the knowledge base — allowance rules, excess fees, restricted items, and lost baggage procedures.

---

### Travel Policies and Other Help

<p align="center">
  <img src="screenshots/travel-policies-menu-screenshot.png" alt="Travel policies menu" width="700">
</p>
<p align="center">
  <img src="screenshots/other-help-menu-screenshot.png" alt="Other help menu" width="700">
</p>

Travel policy queries go fully autonomous — ARIA retrieves answers from the KB without needing structured table data. Other Help routes to general KB retrieval or triggers human-agent escalation.

---

### Website Integration

<p align="center">
  <img src="screenshots/website-screenshot.png" alt="Website with embedded webchat widget" width="700">
</p>

ARIA embedded as a Botpress webchat widget on a static website.

---

## How to Import

1. Install [Botpress Studio](https://botpress.com).
2. Go to **Import** and select `botpress-export/aria-airline-chatbot.bpz`.
3. Replace the data table CSVs in `data/` if you want to use your own records.
4. Update the `.txt` files in `knowledge-base/` as needed for your airline context.

Full documentation: [`documentation/aria-chatbot-documentation.pdf`](documentation/aria-chatbot-documentation.pdf)

---

## Team Contribution

This is a cleaned portfolio version of an academic group project. The team contribution covered:

- chatbot design and conversation flow architecture
- semantic network modelling and knowledge base organisation
- Botpress workflow documentation
- portfolio writeup and presentation

---

## What We Learned

- How to structure domain knowledge for AI retrieval — separating policies, entity definitions, Q&A patterns, and semantic relationships into distinct KB documents rather than one monolithic file keeps retrieval focused and reduces hallucination
- How AI-assisted routing in Botpress differs from hard-coded intent matching — and where each is more reliable
- Why semantic networks are useful for chatbot knowledge design: making implicit entity relationships explicit gives the AI a cleaner model of the domain to draw on
- The value of a structured data layer alongside a knowledge base — KB alone cannot reliably return specific booking or flight records

---

## Future Improvements

- Connect to real airline APIs for live flight status
- Improve natural language understanding for free-text queries
- Add multilingual support (Malay / English at minimum)
- Add a conversation analytics dashboard to monitor drop-off and escalation rates
- Strengthen pre-booking-change authentication
- Improve human-agent escalation handoff with full conversation context transfer

---

## Repository Structure

```
aria-airline-chatbot-botpress/
├── botpress-export/
│   └── aria-airline-chatbot.bpz
├── knowledge-base/
│   ├── overview.txt
│   ├── core-knowledge-model.txt
│   ├── passenger-contact-and-travel-documents.txt
│   ├── booking-payment-and-refund-support.txt
│   ├── ticket-and-baggage-support.txt
│   ├── flight-airport-aircraft-terminal-and-gate.txt
│   ├── conversation-policy-and-validation-rules.txt
│   ├── escalation-policy.txt
│   ├── semantic-relationships-representation.txt
│   ├── qa-retrieval-chunks.txt
│   └── travel-policies-and-passenger-compliance-rules.txt
├── data/
│   ├── bookings-table.csv
│   ├── customers-table.csv
│   └── flight-status-table.csv
├── diagrams/
│   ├── main-semantic-relationship-diagram.png
│   ├── passenger-semantic-relationship-diagram.png
│   ├── flight-semantic-relationship-diagram.png
│   ├── payment-and-booking-semantic-relationship-diagram.png
│   ├── ticket-and-baggage-semantic-relationship-diagram.png
│   ├── customer-details-and-main-menu-flowchart.png
│   ├── flight-status-menu-flowchart.png
│   ├── booking-management-menu-flowchart.png
│   ├── baggage-service-menu-flowchart.png
│   └── other-help-menu-flowchart.png
├── screenshots/
│   ├── customer-details-and-main-menu-screenshot-1.png
│   ├── customer-details-and-main-menu-screenshot-2.png
│   ├── flight-status-menu-screenshot.png
│   ├── booking-management-menu-screenshot.png
│   ├── baggage-service-menu-1.png
│   ├── baggage-service-menu-2.png
│   ├── baggage-service-menu-3.png
│   ├── travel-policies-menu-screenshot.png
│   ├── other-help-menu-screenshot.png
│   └── website-screenshot.png
├── documentation/
│   └── aria-chatbot-documentation.pdf
├── README.md
└── .gitignore
```

---

> **Privacy note:** This repository is a cleaned portfolio version of an academic group project. Private workspace links, API keys, tokens, student IDs, and raw submission details are intentionally excluded.
