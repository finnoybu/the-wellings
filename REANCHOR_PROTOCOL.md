# Re-Anchor Protocol (Canonical Governance)

This document defines the **governance rules, authority hierarchy, and ingestion requirements**
for all project materials. It must be applied **before** any interpretation, analysis, or action.

---

## Authority Hierarchy

All project materials are governed by the following authority layers, listed from **highest** to **lowest** authority:

### Layer 0 — Procedural Authority (Meta-Governance)

Controls *how* all other materials are ingested, interpreted, validated, and tracked.

- `REANCHOR_PROTOCOL.md`
- `PATH_TRACKING_CHECKLIST.md`

These documents are **procedurally authoritative over all other files**, including canon.
They do not define project truth; they define **how truth and materials are handled**.

Failure to comply with procedural authority invalidates all downstream work.

---

### Layer 1 — Canonical Truth

Defines what is **true** about the project.

Canon is the **sole source of truth** for decisions, invariants, requirements, and architecture.
Anything not documented in canon **does not exist** for purposes of execution.

Canon may only be modified through an explicit promotion process.

---

### Layer 2 — Supporting Project Artifacts

Defines **implementation details, planning context, research, tracking, or exploratory work**.

These files:
- Are **not optional**
- Must be ingested and understood
- Do **not** override canon
- Always outrank conversation

Examples include (but are not limited to):
- Design notes
- Research documents
- Status files
- Checklists (non-governing)
- Drafts and experiments

---

### Layer 3 — Conversation

Ephemeral discussion and reasoning.

Conversation:
- Is valid only within the current session
- Must never outrank any file
- Is discarded unless explicitly promoted into documentation

---

## Protocol Precedence

Every re-anchoring operation **must begin** with ingestion of:
1. `REANCHOR_PROTOCOL.md`
2. `PATH_TRACKING_CHECKLIST.md`

No other files may be ingested, analyzed, or acted upon until these documents have been read and applied.

---

## Session Scope Rule

In addition to files, any discussion **since the most recent update pack upload** is considered valid working context.

All discussion **prior** to the latest update pack is intentionally discarded and must be treated as nonexistent unless captured in files.

If ambiguity exists between files and conversation, **files always prevail**.
If ambiguity exists between canon and other files, **canon prevails**.
If ambiguity exists about process, **procedural authority prevails**.

---

## Mandatory Full Update-Pack Traversal

Re-anchoring is **not complete** until **every file and folder** in the update pack has been traversed.

Traversal requirements:
- All directories must be enumerated
- All files must be individually identified
- No file may be implicitly assumed, skipped, or bulk-acknowledged

Re-anchoring applies to the **entire update pack**, not just canon.

---

## Lightweight Per-File Acknowledgment

For each file in the update pack, you must acknowledge ingestion using the following **minimal format**:

- **File:** `<path/filename>`
  - Classification: Procedural Authority | Canon | Supporting Artifact
  - Purpose: (one concise sentence)
  - Status: Read / Understood / Flagged (if issues exist)

No summaries, rewrites, or analysis are required unless issues are flagged.

This acknowledgment exists to:
- Prove ingestion
- Confirm role comprehension
- Prevent silent drift

---

## Re-Anchoring Completion Criteria

Re-anchoring is considered complete **only when all of the following are true**:

- Procedural authority documents ingested first
- Full update-pack traversal completed
- Every file acknowledged and classified
- Canon reviewed and re-anchored
- Supporting artifacts ingested
- Any flagged issues surfaced before forward progress

---

## Automatic Re-Anchoring on Re-Entry

Re-anchoring is required on **any resumption of work** after a break in continuity, including:
- Extended user absence
- Session or thread reset
- Requests to “continue,” “resume,” or “pick up where we left off”
- Any uncertainty about alignment with the latest update pack

No work may proceed until re-anchoring is complete unless explicitly waived by the user.

---

## Required Acknowledgement

After re-anchoring, explicitly confirm:

- Procedural authority was ingested first
- Full update-pack traversal was completed
- All files were acknowledged and classified
- Re-anchoring is complete or blocked (with reasons)

Failure to meet these conditions constitutes **incomplete execution**.
