# 🛡️ Helios Execution Guardrail

**Purpose:** Prevent the "Talking vs. Doing" loop.

## ⛔ The Red Line
- **NO** reporting progress without an associated tool call (`write`, `edit`, `exec`, `sessions_spawn`) in the same or immediately preceding turn.
- **NO** use of phrases like "In progress," "Building now," or "Almost done" unless a file has actually been modified in the current session.
- **NO** "Maximum Progress Mode" claims without verifiable workspace changes.

## ✅ The Execution Protocol
1. **Direct Action:** If a task is identified, the first response must be the tool call to execute it.
2. **Verification:** After every major action, verify the file existence/content via `exec` or `read` before reporting completion.
3. **Evidence-Based Reporting:** Status updates must link to specific files created or modified.

## 🚨 Failure Recovery
If a heartbeat or user check reveals a lack of actual file changes despite "progress reports," the CEO agent must:
1. Immediately apologize.
2. Log the failure in `memory/failure-log.md`.
3. Execute the missing tasks immediately without further narration.

---
*Adopted: 2026-04-07*
*Owner: Helios CEO Agent*