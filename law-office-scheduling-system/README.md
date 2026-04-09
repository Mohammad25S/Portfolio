# Law Office Appointment Scheduling System

A full systems analysis and design capstone project completed for a real client — the Hasin Chaudhary Law Office in Toronto. The project involved identifying operational problems with the firm's existing scheduling process and delivering a complete solution proposal, including business process redesign, system design artifacts, and a working proof-of-concept prototype.

**Role:** Project Manager | **Team Size:** 5 | **Duration:** Feb 2023 – Apr 2023 | **Course:** ITM 900, Toronto Metropolitan University

---

## The Problem

The law office was managing all client appointment requests entirely through email, which created a cascade of issues: response times of 1–2 business days, double bookings, lost emails from spam bots, and clients arriving at meetings without having submitted case details in advance — forcing the lawyer to spend meeting time just understanding the situation rather than providing legal advice.

---

## The Solution

A web-based appointment scheduling system integrated into the firm's existing website (hasinlaw.ca), allowing clients to self-serve the entire booking process end-to-end. Key features of the proposed system include:

- **Client account registration and credential validation** with lockout protection after failed login attempts
- **Digital intake form** collecting personal information, case details, and supporting documents before the meeting — ensuring the lawyer is fully prepared in advance
- **Meeting type selection** — clients choose between 30-minute (free) or 1-hour ($150) meetings, via In-Person, Zoom, or Phone
- **Live time slot availability calendar** — clients pick from available slots, with automatic updates to prevent double booking
- **Appointment management** — clients can reschedule, cancel, or attach additional documents post-booking, with automated email notifications sent to both parties
- **Automated reminders** sent 2 days before and on the day of the appointment
- **Admin panel for the lawyer** — full weekly calendar view with the ability to open and close time slots

---

## Project Deliverables

### Business Analysis
- Diagnostic table mapping causes, problems, and consequences of the current system
- As-Is BPMN model documenting the existing email-based scheduling process
- To-Be BPMN models for all 10 redesigned use cases

### System Design
- Full Use Case Model with 10 detailed use case descriptions covering all actors (Client, Lawyer, System)
- Entity Relationship Diagram (ERD) with 5 entities: Client, Appointment, Lawyer, Intake Form, Time Slots, Reminder
- Normalized Database Schema
- UML Class Diagram with full attributes and methods
- 10 Sequence Diagrams covering every major system interaction

### Prototype
- Fully designed proof-of-concept UI prototype including: Home Page, Sign-In & Register, Account Dashboard, Intake Form, Meeting Type Selection, Time Slot Calendar, Appointment Review, Appointment Management, and Admin Panel

### Project Management
- Project Charter with defined objectives, success criteria, and stakeholder roles
- Gantt Chart covering 49-day project timeline across 5 phases: Initiation, Planning, Executing, Closing
- Risk Assessment and Mitigation Plan covering privacy/data security, system overload, double-booking conflicts, and ongoing maintenance

---

## Methodologies & Tools

- Business Process Modeling (BPMN)
- Use Case Modeling (UML)
- Entity Relationship Diagramming
- Object-Oriented Design (Class & Sequence Diagrams)
- Agile-style project management with bi-weekly client check-ins
- Figma (UI Prototype)
- Microsoft Project (Gantt Chart)

---

## Key Takeaway

This project demonstrates the full business analyst lifecycle — from client discovery and problem diagnosis, through requirements gathering and system modeling, to prototype delivery and risk planning — applied to a real business with real operational pain points.
