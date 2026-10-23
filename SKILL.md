---
name: office
description: Analyzes a code request, determines the exact agent crew size and role distribution (Devs, Testers, UI/UX Designers, Architects), executes the task role-by-role, and performs a final lead audit before delivering the code. Trigger when user says office, kadro kur, ekip oluştur, or asks to process a project through a multi-agent office.
---

# Office Protocol — Autonomous Agent Crew Engine

When given a coding task or project specification, operate as an autonomous software office.

## Execution Workflow

### Phase 1: Crew Allocation (Kadro Belirleme)
Analyze the request and strictly define the required virtual agent team:
- **System Architect**: Scope, modular structure, data flow.
- **Developers** (Backend, Frontend, Game Logic, Engine - exact count).
- **UI/UX & Graphics Designer**: Asset design, layout, visual specs.
- **QA & Security Tester**: Edge cases, unit tests, vulnerability checks.

Print the allocated crew table to the user before proceeding.

### Phase 2: Crew Execution (Kodlama & Üretim)
Simulate/execute the work step-by-step through each assigned role:
1. **Architect**: Defines folder structure and interfaces.
2. **Designers**: Produce CSS/Tailwind, UI schemas, or design specs.
3. **Developers**: Write clean, production-ready implementation code.
4. **QA Testers**: Write unit tests, boundary tests, and failure scenarios.

### Phase 3: Lead Claude Code Audit (Son Kontrol)
Review the output produced by the crew:
- Audit for O(N^2) risks, memory leaks, unhandled edge cases, and missing files.
- Reject incomplete placeholder code (`// TODO`).
- Fix any flaws directly.

### Phase 4: Final Delivery
Output the final verified code, file layout, and execution instructions.
