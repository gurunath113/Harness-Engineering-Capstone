# Harness Engineering with Claude and Claude Code — Capstone

## Overview

This project is the final capstone for **Harness Engineering with Claude and Claude Code**.

The project demonstrates how reliable AI systems can be engineered by separating **model reasoning, deterministic harness logic, context management, tool execution, Claude Code configuration, state management, testing, and multi-step orchestration**.

## Four Systems

### 1. Claims Intake Agent

Demonstrates a `stop_reason`-driven agentic loop for dynamic claims intake.

**Key concepts:**
- Agentic tool-use loop
- `stop_reason`-driven control
- Dynamic decomposition
- Structured tool execution
- Anti-pattern detection

**Evidence:**
`evidence/system1_agentic_loop/`

**Test result:** `29 passed`

For the recorded `claim_01_kitchen_fire` trace:

```text
Turn 1 → stop_reason: tool_use
Turn 2 → stop_reason: end_turn
2. Long-Conversation Context Strategy
Demonstrates context engineering for a retail support copilot.
The system reduces unnecessary context while preserving active information.
Measured results:
Baseline context:  38,708 tokens
Assembled context: 16,804 tokens
Reduction:          56.59%
The dominant section was:
active: 15,789 tokens
Evidence:
evidence/system2_context_strategy/
Includes:
- pytest_S2.log
- budget.json
- eval.jsonl
- eval_control.jsonl
Test result: 28 passed, 2 skipped
3. Claude Code Multi-Surface Configuration
Demonstrates Claude Code configuration for a multi-surface monorepo.
Key concepts:
- Path-scoped rules
- Claude Code skills
- Forked validation
- Read-only tool restrictions
- Project-level configuration
Example React rule:
paths:
  - "src/components/**/*"
  - "src/pages/**/*"
The deployment validation skill uses:
context: fork
Evidence:
evidence/system3_claude_config/
Includes:
- pytest_S3.log
- validator_output.txt
- claude_dir_structure.txt
- React/API/test/skill/Claude/review rule evidence
Validation: OK
Test result: 35 passed
4. Multi-Shift Quality Monitoring
Demonstrates Claude orchestration across multiple monitoring shifts.
Key concepts:
- Warm storage
- Bounded hot state
- Scratchpads
- Forked execution
- Crash recovery
- Shift-level analysis
Recorded hot-state size:
643 bytes
The recovery system uses a 30-minute threshold to determine whether incomplete work should be resumed or restarted.
Example recorded Shift C result:
Shift C: 0 new defects

Shift C 2026-04-30:
3 high + 2 medium defects on capacitor-bank-C-7,
all from lot 2026-0430-B.
1 low VP-4 vent squeal (repeat).
Lot quarantine recommended.
Evidence:
evidence/system4_orchestration/
Includes:
- pytest_S4.log
- shift_run_output.txt
- hot_state_size.txt
- scratchpad_line.jsonl
Test result: 33 passed
Overall Test Results
System	Result
System 1 — Claims Intake	29 passed
System 2 — Context Strategy	28 passed, 2 skipped
System 3 — Claude Code Configuration	35 passed
System 4 — Multi-Shift Monitoring	33 passed


Evidence Structure
evidence/
├── system1_agentic_loop/
│   ├── pytest_S1.log
│   ├── summary.md
│   └── claim_01_kitchen_fire.jsonl
│
├── system2_context_strategy/
│   ├── pytest_S2.log
│   ├── budget.json
│   ├── eval.jsonl
│   └── eval_control.jsonl
│
├── system3_claude_config/
│   ├── pytest_S3.log
│   ├── validator_output.txt
│   ├── claude_dir_structure.txt
│   └── supporting rule and skill evidence
│
└── system4_orchestration/
    ├── pytest_S4.log
    ├── shift_run_output.txt
    ├── hot_state_size.txt
    └── scratchpad_line.jsonl
Key Engineering Principles
Structured Control
System 1 uses the API-level stop_reason rather than parsing natural-language responses to determine whether the agent should continue or stop.
Context Engineering
System 2 deliberately assembles and compresses context instead of blindly passing an entire conversation history to the model.
Scoped Instructions
System 3 uses path-scoped Claude Code rules so that instructions apply only where they are relevant.
Isolated Execution
The forked Claude Code validation skill separates validation work from the main session.
Bounded State
System 4 keeps long-term information in warm storage while maintaining a small operational hot state.
Crash Recovery
System 4 explicitly handles incomplete executions through resume-versus-fresh recovery logic.
Automated Testing
Each system includes automated tests to verify architectural behavior in addition to successful example runs.
Reflection
The completed reflection brief is available in:
my-reflection-brief.md
It documents the engineering decisions, observed results, context strategy, reliability mechanisms, orchestration architecture, and lessons learned from the four systems.
Evidence Archive
A complete evidence archive is also included:
Harness_Engineering_Evidence.zip
Repository Contents
.
├── evidence/
├── my-reflection-brief.md
├── Harness_Engineering_Evidence.zip
├── README.md
└── .gitignore
Project Status
- ✅ System 1 — Claims Intake Agent
- ✅ System 2 — Long-Conversation Context Strategy
- ✅ System 3 — Claude Code Configuration
- ✅ System 4 — Multi-Shift Quality Monitoring
- ✅ Automated test evidence
- ✅ Evidence archive
- ✅ Reflection brief
- ✅ GitHub repository
Capstone Focus
This project demonstrates that reliable AI systems can be built by combining model reasoning with deterministic software, explicit context management, controlled tools, testing, state management, and orchestration.
The model performs reasoning where it is useful, while the surrounding harness provides structure, limits, validation, state management, and recovery.
