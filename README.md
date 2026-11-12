# AutoSpec AI

## 1. Project Overview
* **Project Name:** AutoSpec AI
* **Purpose:** AutoSpec AI is an AI-powered automotive performance analysis and comparison platform.
* **Main Features:**
  * **Dynamic Vehicle Filtering & Dashboard:** Filter inventory by body style (e.g., SUV), specs, and criteria.
  * **Detailed Spec & Side-by-Side Comparison Views:** Inspect granular vehicle metrics and compare top contenders.
  * **Interactive Data Visualizations:** Visual charts breaking down vehicle performance and value metrics.
  * **AI Buying Advisor (Track & Daily Modes):** Contextual AI recommendations tailored to specific driving use cases, complete with graceful error handling for malformed AI responses
  * **Responsive Mobile Experience:** Full layout adaptability for smaller viewports.

---

## 2. Architecture Summary
- **System Architecture:** A client-side single-page web application (`src/index.html`) utilizing modular state management, structured vehicle data filtering, dynamic charting libraries for performance and value metrics, and a contextual AI advisor integration layer featuring response validation and graceful mock fallbacks.
- **Main Technologies:** HTML5, CSS3, JavaScript (ES6+), chart visualization libraries, Claude AI integration layer, and Python + Playwright for automated end-to-end testing (`tests/e2e_test.py`).
- **Important Design Decisions:**
  * **Spec-Driven Development:** Established formal requirements, architecture, and security guidelines before generating UI components and application logic.
  * **Defensive AI Output Handling:** Implemented schema/format validation on AI advisor responses so malformed payloads trigger a user-friendly fallback UI (`08-error-malformed-AI.png`) rather than crashing the client application.
  * **Hybrid Traditional & AI Processing:** Utilized traditional programming for objective mathematical calculations (such as power-to-weight ratios) and data visualization charts, while leveraging Claude AI strictly for interpreting those results and delivering personalized, scenario-aware recommendations.
  * **Context-Driven Dynamic Prompting:** Architected the AI integration layer to dynamically adapt its reasoning based on user-selected scenarios (e.g., shifting priorities from high-performance track metrics to practical daily driving comfort).

---
3. AI Models and Tools Used
| AI Model / Tool | SDLC Phase(s) | Specific Role & Responsibilities |
| :--- | :--- | :--- |
| **Claude 3.5 Sonnet / Claude Code** | Architecture, Implementation, Testing | Guided by `CLAUDE.md` to scaffold `src/index.html`, implement vehicle filtering and data visualization charting logic, and generate Playwright E2E tests (`tests/e2e_test.py`). |
| **ChatGPT (GPT-4o)** | Planning, Requirements, Reflection | Brainstormed user personas, drafted initial SDLC specifications (`docs/planning.md`, `docs/requirements.md`), and cross-checked security edge cases (`docs/security.md`). |
| **Cursor AI Editor** | Implementation, Debugging | Provided the primary integrated development environment for iterative UI refinement, inline diff reviews, and debugging state handling for the dynamic advisor scenarios. |

---

## 4. AI Engineering Analysis
*(Pull specific examples directly from your `docs/ai-workflow-log.md` to make this section concrete.)*

* **What AI Tools Did Particularly Well:**
  * Rapidly translating structured markdown specifications (`requirements.md`, `design.md`) into working frontend components and responsive CSS layouts.
  * Generating comprehensive Playwright test selectors and end-to-end test cases (`tests/e2e_test.py`).
* **Where AI Struggled or Failed:**
  * [Insert a specific bug or mistake from `docs/ai-workflow-log.md` — e.g., Initially generated fragile DOM selectors, hallucinated data fields, or failed to handle malformed JSON from the advisor endpoint.]
  * [Insert an example where you rejected or overrode an AI suggestion — e.g., Replaced an overly complex state structure with a cleaner vanilla JS approach.]
* **Tradeoffs & Challenges Encountered:**
  * Balancing speed of generation against context window drift; required breaking large tasks into isolated, single-responsibility prompts.
* **Prompting Strategies That Worked vs. Did Not Work:**
  * **Worked:** Providing persistent context files (`CLAUDE.md`, `architecture.md`), specifying exact acceptance criteria, and asking AI to critique its own output before writing code.
  * **Did Not Work:** Broad, open-ended prompts (e.g., "Build the comparison page") without schema constraints, which led to inconsistent styling and missing edge-case handling.

---

## 5. Engineering Reflection
* **Approach Without AI:** Without AI, significantly more time would have been spent writing boilerplate HTML/CSS, wiring up chart configurations manually, and authoring Playwright test scripts from scratch—leaving less time for thorough edge-case testing and documentation.
* **What AI Helped Accomplish More Effectively:** Accelerated prototyping across all six SDLC phases, acted as a sounding board for security and failure-mode analysis (`security.md`), and enabled full E2E test coverage within project timelines.
* **What AI Made More Difficult or Potentially Worse:** Debugging subtle logic errors introduced by confident-sounding AI code required careful line-by-line auditing. Relying on AI without strict specs risked architectural inconsistency across iterations.
* **Key Takeaways on Engineering with AI:** AI is a force multiplier only when the engineer maintains strict control over requirements, architecture, and verification. Context engineering (`CLAUDE.md` and `/docs`) matters just as much as individual prompts.

---

## 6. Supporting Documentation and Context Files
All project specifications, AI context rules, and verification logs are maintained in this repository:
* [`CLAUDE.md`](./CLAUDE.md) — Primary instructions, coding standards, and behavioral guardrails provided to AI coding agents.
* [`docs/planning.md`](./docs/planning.md) — Project scope, constraints, assumptions, and development roadmap.
* [`docs/requirements.md`](./docs/requirements.md) — Functional/non-functional requirements, user personas, and user stories.
* [`docs/architecture.md`](./docs/architecture.md) — System design, component structure, and technical decisions.
* [`docs/design.md`](./docs/design.md) — UI/UX wireframes, layout hierarchy, and design rationale.
* [`docs/security.md`](./docs/security.md) — Security considerations, input sanitization, and AI output validation rules.
* [`docs/testing.md`](./docs/testing.md) & [`docs/test-run-output.txt`](./docs/test-run-output.txt) — Testing strategy and verified Playwright execution logs.
* [`docs/ai-workflow-log.md`](./docs/ai-workflow-log.md) — Detailed chronological log of prompts, iterations, AI errors, and human overrides.
