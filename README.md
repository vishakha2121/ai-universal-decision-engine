<div align="center">

# 🧠 AI Universal Decision Engine

### *Reasonix — Because "why" matters as much as "what".*

[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?logo=python&logoColor=white)](https://python.org)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.100+-009688?logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com)
[![React](https://img.shields.io/badge/React-18+-61DAFB?logo=react&logoColor=black)](https://react.dev)
[![TailwindCSS](https://img.shields.io/badge/Tailwind-3.0+-38B2AC?logo=tailwindcss&logoColor=white)](https://tailwindcss.com)
[![Gemini](https://img.shields.io/badge/Gemini-API-4285F4?logo=google&logoColor=white)](https://ai.google.dev)
[![SQLite](https://img.shields.io/badge/SQLite-3.0+-003B57?logo=sqlite&logoColor=white)](https://sqlite.org)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

<br/>

**A modular, multi-domain AI reasoning engine that solves real-world problems across Finance, Medicine, Logistics, Engineering, and Science — delivering explainable, step-by-step decision traces instead of black-box answers.**

[Explore Architecture](#-system-architecture) • [API Docs](#-api-endpoints) • [Setup Guide](#-getting-started) • [Interview Notes](#-why-this-project-stands-out)

</div>

---

## 📌 Table of Contents

1. [Introduction](#1-introduction)
2. [The Problem](#2-the-problem)
3. [The Solution](#3-the-solution)
4. [Core Features](#4-core-features)
5. [Supported Domains](#5-supported-domains)
6. [Modular Reasoning Strategies](#6-modular-reasoning-strategies)
7. [System Architecture](#7-system-architecture)
8. [The Reasoning Trace (Hero Feature)](#8-the-reasoning-trace-hero-feature)
9. [Tech Stack](#9-tech-stack)
10. [Project Structure](#10-project-structure)
11. [Database Design](#11-database-design)
12. [API Endpoints](#12-api-endpoints)
13. [Getting Started (Setup Guide)](#13-getting-started-setup-guide)
14. [Environment Variables](#14-environment-variables)
15. [Running the Application](#15-running-the-application)
16. [Example Use Cases](#16-example-use-cases)
17. [Design Principles](#17-design-principles)
18. [Why This Project Stands Out](#18-why-this-project-stands-out)
19. [Roadmap](#19-roadmap)
20. [Known Limitations](#20-known-limitations)
21. [Contributing](#21-contributing)
22. [License](#22-license)
23. [Acknowledgements](#23-acknowledgements)
24. [Contact](#24-contact)

---

## 1. Introduction

**AI Universal Decision Engine** (codename: **Reasonix**) is a modular, multi-domain reasoning system designed to solve practical, real-world problems across five distinct fields:

- 💰 **Finance**
- 🏥 **Medicine**
- 🚚 **Logistics**
- ⚙️ **Engineering**
- 🔬 **Science**

Unlike traditional AI chatbots that return a final answer and hide their internal logic, Reasonix exposes its **complete reasoning trace**. Every step — every rule fired, every formula applied, every observation recorded — is stored and displayed to the user. This makes the AI's decisions **transparent, explainable, and auditable**.

Built with a hybrid reasoning strategy (rule-based + formula-based + LLM-based), Reasonix demonstrates how a modular architecture can turn a simple question-answering bot into a trustworthy decision engine.

> **Note:** This project was built as a **practice / learning project** to demonstrate modular architecture, the Strategy design pattern, and explainable AI. It is **not intended for production deployment**, though it is architected like a real system.

---

## 2. The Problem

Artificial Intelligence is increasingly used to make high-stakes decisions:

- Should this loan be approved?
- Does this patient's symptom indicate a serious disease?
- Which delivery route is most cost-effective?
- Does this bridge design meet safety standards?

These decisions matter. But most modern AI systems are **black boxes**:

- They return an answer without explaining *how* they got there.
- There is no audit trail — you cannot verify the reasoning.
- If the AI makes a mistake, you cannot pinpoint *where* it went wrong.
- In regulated domains (finance, medicine), an unexplainable decision is legally and ethically useless.

**The gap:** There is a need for AI systems that not only decide, but **explain their decision**.

---

## 3. The Solution

Reasonix solves this by combining:

1. **Multiple reasoning paradigms** — rule-based logic, formula computation, chain-of-thought, ReAct, tree-of-thoughts, and LLM fallback.
2. **Domain-specific modules** — each of the five domains has its own rules, formulas, and prompts.
3. **A complete trace logger** — every reasoning step is captured, timestamped, and stored in the database.
4. **A confidence scorer** — the system rates its own confidence in each decision.
5. **A transparent UI** — the frontend displays the entire reasoning trace as an animated timeline.

The result is a decision engine you can **trust**, **audit**, and **learn from**.

---

## 4. Core Features

| Feature | Description |
|---------|-------------|
| 🌐 **5 Domains** | Finance, Medicine, Logistics, Engineering, Science |
| 🧩 **6 Reasoning Strategies** | Rule-Based, Formula, Chain-of-Thought, ReAct, Tree of Thoughts, LLM Fallback |
| 🎯 **Auto Domain Detection** | The system auto-detects which domain a query belongs to based on keywords & intent |
| 🧠 **Auto Strategy Selection** | Picks the best reasoning strategy for each query |
| 📜 **Full Reasoning Trace** | Every step is logged: thought → action → observation → conclusion |
| 📊 **Confidence Scoring** | Each final decision is assigned a confidence score (0-100%) |
| 💾 **Persistent History** | All sessions and steps stored in SQLite |
| 🎨 **Modern UI** | Dark theme, animated step-by-step trace viewer, glassmorphism cards |
| ⚡ **Hybrid Intelligence** | Rule-based fast path + LLM fallback for unknown queries |
| 🔌 **Modular Design** | Add a new domain or strategy by dropping in a new folder — zero core changes |
| 🧪 **Test-Friendly** | Every reasoner is independently testable |
| 🛡️ **Graceful Fallbacks** | If Gemini API fails, rule-based reasoning takes over |

---

## 5. Supported Domains

### 💰 Finance
- Loan approval predictions
- EMI calculations
- Debt-to-income ratio checks
- Credit risk scoring
- Simple interest / compound interest
- Break-even analysis

### 🏥 Medicine
- Symptom → disease mapping
- Drug interaction warnings
- BMI / dosage calculations
- Risk factor assessments
- Basic triage recommendations

### 🚚 Logistics
- Route optimization (distance/time)
- Delivery cost estimation
- Load planning
- Fuel consumption estimates
- Warehouse inventory checks

### ⚙️ Engineering
- Load calculations
- Material selection
- Safety threshold checks
- Unit conversions
- Tolerance analysis

### 🔬 Science
- Physics numericals (velocity, force, energy)
- Chemistry problems (moles, molarity)
- Formula-based problem solving
- Unit conversion chains
- Experimental error estimation

---

## 6. Modular Reasoning Strategies

Reasonix employs the **Strategy Design Pattern** — each reasoner is a pluggable module that conforms to a common interface (`BaseReasoner`).

### 1. 🔹 Rule-Based Reasoning
**How it works:** Deterministic if-then logic. Fast and predictable.  
**Best for:** Simple business rules (loan thresholds, safety limits).  
**File:** `backend/reasoning/rule_based_reasoner.py`

### 2. 🔹 Formula Reasoning
**How it works:** Evaluates mathematical formulas safely.  
**Best for:** Numerical problems (EMI, load, moles).  
**File:** `backend/reasoning/formula_reasoner.py`

### 3. 🔹 Chain-of-Thought (CoT)
**How it works:** Prompts the LLM to "think step by step".  
**Best for:** Open-ended analysis where reasoning flow matters.  
**File:** `backend/reasoning/chain_of_thought_reasoner.py`

### 4. 🔹 ReAct (Reason + Act)
**How it works:** Iteratively reasons, acts (calls tools), observes results.  
**Best for:** Multi-step problems needing external lookups.  
**File:** `backend/reasoning/react_reasoner.py`

### 5. 🔹 Tree of Thoughts
**How it works:** Explores multiple reasoning branches, picks the best.  
**Best for:** Ambiguous problems with multiple valid approaches.  
**File:** `backend/reasoning/tree_of_thoughts_reasoner.py`

### 6. 🔹 LLM Fallback (Gemini)
**How it works:** Directly queries Gemini API for open-ended queries.  
**Best for:** Novel or unrecognized queries.  
**File:** `backend/services/gemini_service.py`

---

## 7. System Architecture

```text
┌──────────────────────────────────────────────────────────────┐
│                        REACT FRONTEND                        │
│  ┌────────────┐  ┌──────────────┐  ┌────────────────────┐   │
│  │ Domain Picker│ │ Input Form  │  │  Trace Viewer (UI) │   │
│  └────────────┘  └──────────────┘  └────────────────────┘   │
└──────────────────────────────┬───────────────────────────────┘
                               │ HTTP (REST)
                               ▼
┌──────────────────────────────────────────────────────────────┐
│                       FASTAPI BACKEND                        │
│  ┌────────────────────────────────────────────────────────┐ │
│  │                 /api/reason (POST)                     │ │
│  └────────────────────────────────────────────────────────┘ │
│                            │                                 │
│                            ▼                                 │
│  ┌────────────────────────────────────────────────────────┐ │
│  │              CORE ENGINE (Orchestrator)                │ │
│  │  1. Domain Detector                                    │ │
│  │  2. Strategy Selector                                  │ │
│  │  3. Trace Logger                                       │ │
│  │  4. Confidence Scorer                                  │ │
│  └────────────────────────────────────────────────────────┘ │
│                            │                                 │
│         ┌──────────────────┼──────────────────┐             │
│         ▼                  ▼                  ▼             │
│  ┌───────────┐      ┌────────────┐     ┌────────────┐       │
│  │ Rule      │      │ Formula    │     │ Gemini LLM │       │
│  │ Reasoner  │      │ Reasoner   │     │ Reasoner   │       │
│  └───────────┘      └────────────┘     └────────────┘       │
│         │                  │                  │             │
│         └──────────────────┼──────────────────┘             │
│                            ▼                                 │
│  ┌────────────────────────────────────────────────────────┐ │
│  │             DOMAIN HANDLERS (5 Modules)                │ │
│  │  Finance │ Medicine │ Logistics │ Engineering │ Science│ │
│  └────────────────────────────────────────────────────────┘ │
│                            │                                 │
│                            ▼                                 │
│  ┌────────────────────────────────────────────────────────┐ │
│  │                   SQLite Database                      │ │
│  │  sessions | requests | steps | decisions | feedback    │ │
│  └────────────────────────────────────────────────────────┘ │
└──────────────────────────────────────────────────────────────┘


git clone https://github.com/vishakha2121/ai-universal-decision-engine.git
cd ai-universal-decision-engine

cd backend
python -m venv venv

# Activate virtualenv
# On Windows:
venv\Scripts\activate
# On macOS/Linux:
source venv/bin/activate

pip install -r requirements.txt

cd frontend
npm install