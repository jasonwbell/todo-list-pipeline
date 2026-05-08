# AI-Driven Task Ingestion System

## 🎯 Overview

This project explores a system for transforming **implicit work signals** (meetings, emails, conversations) into **explicit, structured tasks**—while preserving human accountability and minimizing noise.

The system uses:
- Microsoft Copilot / LLMs for extraction
- Power Automate for orchestration
- Microsoft To Do for task persistence
- Teams Adaptive Cards for approval

The design goal is not automation for its own sake, but **high-signal task creation with minimal friction**.

---

## 🧠 Problem Statement

Modern work suffers from a structural gap:

- Work is agreed in **meetings and conversations**
- Tasks are tracked in **formal systems (To Do, Planner, ADO)**

These systems are disconnected:
- Tasks are missed
- Ownership becomes ambiguous
- Manual entry is inconsistent and error-prone

This project addresses that gap by building a system that:

> Captures commitments at the moment they are made  
> Structures them into tasks  
> Requires human approval before persistence  

---

## 🏗 System Architecture

``
Meetings / Emails / Daily Activity
↓
AI Extraction Layer
↓
Confidence Filtering
↓
Approval (Teams Card)
↓
Microsoft To Do
``

---

## ⚙️ Core Concepts

### 1. Human-in-the-Loop Approval

The system does not automatically create tasks.

Instead:
- Tasks are proposed
- The user approves or rejects
- Only approved tasks are persisted

This ensures:
- Signal quality remains high
- Accountability is preserved

---

### 2. Confidence-Based Filtering

Each extracted task is scored:

| Level | Description |
|------|------------|
| HIGH | Explicit owner + action (+ optional due date) |
| MEDIUM | Reasonable action but some ambiguity |
| LOW | Discussion, no clear ownership (discarded) |

Only HIGH and MEDIUM tasks are surfaced.

---

### 3. Batch Decisioning

Tasks are not approved individually.

Instead:
- Per meeting
- Or daily batch (recommended)

Example actions:
- ✅ Approve High Only
- ✅ Approve All
- ✏️ Edit Before Create
- ❌ Reject All

---

### 4. Upstream Signal Control

The system depends heavily on **meeting behavior**.

Key habit:

> "Action check — [Owner] will [Action] by [Date]"

This ensures:
- Clear ownership
- Clean transcript signals
- Reliable downstream automation

---

## 🚀 Implementation Phases

---

### Phase 1 — Manual Pipeline

- Extract tasks via Copilot
- Review manually
- Copy into To Do

Goal:
- Validate signal quality

---

### Phase 2 — Power Automate Integration

Implement:

- End-of-day task aggregation
- Teams Adaptive Card approval
- Task creation in Microsoft To Do

---

### Phase 3 — Optimization

- Improve confidence scoring
- Add email triggers (filtered)
- Enable optional auto-approval for HIGH confidence

---

### Phase 4 — Advanced (Optional)

- Introduce MCP / API integration
- Build persistent ingestion agent
- Add feedback loops for learning

---

## 🔄 Core Flows

---

### 📅 Meeting-Based Extraction (Primary)

Trigger:
- Meeting ends

Process:
1. Extract transcript / summary
2. Identify action statements
3. Score confidence
4. Send approval card
5. Create tasks (on approval)

---

### 📧 Email-Based Extraction (Selective)

Trigger:
- Flagged emails
- Specific senders
- Action-oriented keywords

Process:
- Extract → Filter → Approve → Create

---

### 🌆 End-of-Day Aggregation (Recommended)

Trigger:
- Scheduled (e.g., 5:30 PM)

Process:
1. Collect day’s signals
2. Extract tasks
3. Deduplicate
4. Present single approval batch

---

## ✅ Example Approval Card
``
Task Review — Daily Summary
HIGH CONFIDENCE

Resolve AT&T data access blocker
Review Connect document

MEDIUM CONFIDENCE

Participate in Ava integration
Identify pilot reviewers

[Approve High] [Approve All] [Edit] [Reject]
``
---

## ⚠️ Risks & Mitigations

---

### Risk: Task Flooding

Mitigation:
- Confidence filtering
- Deduplication
- Approval layer

---

### Risk: Loss of Accountability

Mitigation:
- Require explicit ownership signals
- Keep human approval mandatory

---

### Risk: Low-Quality Inputs

Mitigation:
- Improve meeting discipline
- Encourage explicit action statements

---

## 📊 Success Criteria

- Reduction in missed action items
- Higher task completion rates
- Decreased manual task entry effort
- Improved clarity in meetings

---

## 🧭 Operating Model

This system shifts the user’s role:

From:
> Task creator

To:
> Task approver and signal governor

---

## 🔚 End State

Work transitions from:

> Implicit, conversational commitments  

To:

> Explicit, structured, and trackable execution  

---

## 📝 Notes

This is an evolving system.

The most important lever is not tooling—it is **behavioral discipline in how work is articulated**.

Technology amplifies signal.  
It does not create it.
