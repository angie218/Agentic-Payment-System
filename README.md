# Agentic Payment System

An LLM-powered multi-agent payment platform that combines autonomous AI agents with deterministic Python business logic to simulate secure digital payment workflows.

## Overview

The Agentic Payment System explores how specialized LLM agents can collaborate within a financial workflow while keeping critical payment operations deterministic and controlled.

The system interprets natural-language requests, coordinates payment operations, evaluates transactions for potential fraud, performs security reviews, reflects on failed operations, critiques system responses, and generates user-friendly explanations.

A central design principle is the separation between **AI reasoning** and **financial execution**. LLM agents are responsible for understanding, routing, analysis, and explanation, while deterministic Python components validate business rules and execute payment operations.

> **Note:** This project is an educational simulation and does not connect to real bank accounts, credit cards, or payment services.

## Key Features

- Natural-language payment requests
- LLM-based intent detection and routing
- Multi-agent workflow orchestration
- Deterministic payment execution
- Fraud-risk analysis
- Security review
- Contextual business memory
- Structured LLM outputs with Pydantic
- Reflection and critique mechanisms
- User-friendly action explanations
- Fallback handling for unsupported or incomplete requests
- JSON-based persistence and system restoration

## Multi-Agent Architecture

The system contains specialized agents with clearly separated responsibilities:

| Component | Responsibility |
|---|---|
| **RouterAgent** | Converts natural-language requests into structured intents and parameters |
| **OrchestratorAgent** | Determines the appropriate workflow and system component |
| **FraudDetectionAgent** | Analyzes transaction risk using deterministic fraud features |
| **SecurityAgent** | Performs security analysis using deterministic inspection results |
| **ReflectionAgent** | Analyzes rejected operations and suggests corrective actions |
| **CriticAgent** | Evaluates the quality and consistency of system results |
| **ExplanationAgent** | Generates understandable explanations of recent actions |
| **FallbackAgent** | Handles unsupported, ambiguous, or incomplete requests |
| **OrchestratorRuntime** | Coordinates the complete workflow and executes structured decisions |
| **PaymentSystem** | Executes deterministic payment operations and maintains financial state |

## Architecture Philosophy

The project separates LLM reasoning from deterministic execution.

### LLM Layer

LLM-powered agents handle:

- Intent recognition
- Parameter extraction
- Workflow coordination
- Fraud and security analysis
- Reflection and critique
- Natural-language explanations

### Deterministic Python Layer

Python components handle:

- User and wallet management
- Balance validation
- Money transfers
- Payment requests
- Transaction management
- Fraud feature calculation
- Security inspection
- Audit logging
- Persistence
- Business-rule enforcement

This architecture prevents the language model from directly modifying balances or executing financial operations.

## Supported Operations

The system supports natural-language requests for:

- Creating users
- Checking balances
- Transferring money
- Creating payment requests
- Approving payment requests
- Rejecting payment requests
- Viewing transaction history
- Performing fraud analysis
- Running security reviews
- Explaining recent actions

## Structured LLM Integration

The project integrates the OpenAI API through a shared provider abstraction.

Pydantic models define structured outputs for the agents, allowing LLM responses to be validated before they are processed by downstream components.

This provides a consistent interface between probabilistic language-model reasoning and deterministic application logic.

## Business Memory

`BusinessMemory` maintains short-term contextual information across operations, including:

- Last detected intent
- Last user
- Last transaction
- Last payment request
- Recent system actions

This allows agents such as the `ExplanationAgent` to reason about recent activity without treating conversational memory as financial state.

## Fraud and Security Analysis

Fraud and security workflows combine deterministic inspection with LLM-based interpretation.

Deterministic components calculate transaction-risk features and perform security checks. Specialized agents then analyze those results and return structured assessments.

This keeps measurable security and fraud signals separate from natural-language reasoning.

## Persistence

The payment system supports JSON-based persistence.

Users, wallets, transactions, payment requests, audit information, and identifier counters can be saved and restored, allowing operations to continue after the system state is reloaded.

## Testing

The notebook contains component-level and end-to-end integration tests covering:

- User creation
- Balance verification
- Valid and invalid transfers
- Insufficient funds
- Missing users
- Self-transfer prevention
- Payment-request creation
- Approval and rejection workflows
- Duplicate request handling
- Suspicious transaction detection
- Security review
- Fraud analysis
- Explanation generation
- Unsupported requests
- Persistence and restoration
- Final system-state validation

## Technologies

- Python
- OpenAI API
- GPT-5 mini
- Pydantic
- Structured Outputs
- Multi-Agent Systems
- Prompt Engineering
- Gradio
- JSON Persistence
- Google Colab

## Running the Project

### 1. Clone the repository

```bash
git clone https://github.com/angie218/Agentic-Payment-System.git
cd Agentic-Payment-System
```

### 2. Install dependencies

```bash
pip install openai pydantic python-dotenv gradio pandas
```

### 3. Configure the OpenAI API key

When using Google Colab, add a secret named:

```text
OPENAI_API_KEY
```

For a local environment, configure `OPENAI_API_KEY` as an environment variable.

**Never hard-code or commit an API key to the repository.**

### 4. Open the notebook

Run:

```text
agentic_payment_project.ipynb
```

in Google Colab or another Jupyter-compatible environment.

## Project Structure

```text
Agentic-Payment-System/
│
├── agentic_payment_project.ipynb
└── README.md
```

## Disclaimer

This project is intended for educational and portfolio purposes. It simulates payment-system workflows and security analysis but is not designed for production financial transactions.
