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
