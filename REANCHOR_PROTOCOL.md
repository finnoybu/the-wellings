# REANCHOR_PROTOCOL.md

## Purpose

This document defines the **governance rules, authority hierarchy, and ingestion requirements**
for project materials. It is a minimal revision of the original protocol designed to be
project/repo-agnostic and to add low-overhead AI auditability.

Re-anchoring is the process by which the agent re-establishes alignment with the
project's canonical materials, governance rules, and active working context.

Re-anchoring is **not optional**, **not implicit**, and **not inferred**.

---

## Authority Hierarchy

All project materials are governed by the following authority layers, listed from **highest** to **lowest** authority:

### Layer 0 — Procedural Authority (Meta-Governance)

Controls *how* all other materials are ingested, interpreted, validated, and tracked.

- `REANCHOR_PROTOCOL.md`
- `PATH_TRACKING_CHECKLIST.md`

These documents are **procedurally authoritative over all other files**. They define **how truth and materials are handled**, not the project truth itself.

Failure to comply with procedural authority invalidates downstream work.

---

### Layer 1 — Canonical Materials

Defines what is **true** about the project. Canonical materials may be supplied as a `canon/` directory, a canonical ZIP pack, or an explicit canonical manifest.

Canon is the **sole source of truth** for decisions, invariants, requirements, and architecture. Anything not documented in canonical materials **does not exist** for purposes of execution.

Canonical materials may only be modified through an explicit promotion process.

---

### Layer 2 — Supporting Project Artifacts

Defines **implementation details, planning context, research, tracking, or exploratory work**.

These files:
- Are **not optional**
- Must be ingested and understood
- Do **not** override canonical materials
- Always outrank conversation

Examples include: design notes, research documents, status files, checklists, drafts, manuscripts, and image assets.

Supporting artifacts may include (but are not limited to) manuscripts, images, CSV files,
draft documents, production assets, and working notes.

Image assets must be visually inspected and contextually ingested when they are referenced
by canonical materials or by other supporting artifacts.

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
1. `REANCHOR_PROTOCOL.md` (this document)
2. `PATH_TRACKING_CHECKLIST.md`

No other files may be ingested, analyzed, or acted upon until those documents have been read and applied.

---

## Session Scope Rule

In addition to canonical materials, any conversation occurring after the most recent canonical upload is considered valid working context.

Working context may inform analysis and clarify intent, but **may not modify or expand canonical materials** unless content is explicitly promoted and re-supplied as canonical.

If ambiguity exists:
> **Canonical materials always prevail.**

---

## Mandatory Full Update-Pack Traversal (original behavior preserved)

Re-anchoring is **not complete** until every file and folder in the update pack has been traversed, per original rules, unless a specific mode (below) reduces scope.

Traversal requirements:
- All directories must be enumerated
- All files must be individually identified (or explicitly enumerated in a provided listing)
- No file may be implicitly assumed, skipped, or bulk-acknowledged without explicit enumeration

---

## Lightweight Per-File Acknowledgment (original format)

For each file, acknowledge ingestion using the following minimal format:

- **File:** `<path/filename>`
  - Classification: Procedural Authority | Canonical | Supporting Artifact
  - Purpose: (one concise sentence)
  - Status: Read / Understood / Flagged (if issues exist)

No summaries are required unless issues are flagged. This proves ingestion and prevents drift.

---

## Re-Anchoring Completion Criteria

Re-anchoring is complete only when all of the following are true:
- Procedural authority documents ingested first
- Full update-pack traversal completed (or traversal scope honored per mode)
- Every file acknowledged and classified
- Canonical materials reviewed and re-anchored
- Supporting artifacts ingested
- Any flagged issues surfaced before forward progress

---

## Modes (minimal opt-in enhancement)

To reduce unnecessary overhead while preserving original rigor, the agent MAY operate in a limited set of modes when specific artifacts are supplied. Modes are optional and do not remove the requirement that canonical materials be authoritative.

- Snapshot mode (canonical ZIP supplied): agent ingests canonical materials from the ZIP in full and reports missing items.
- Targeted mode (canonical ZIP + diff/gitshow supplied): agent ingests canonical materials and reviews only listed diffs for additional verification.
- Full mode (explicit listing provided such as `ls -R`): agent enumerates and ingests everything as in original rules.

Modes may reduce traversal scope only when triggered by the provided artifacts; otherwise full traversal applies.

---

## Minimal AI Audit Artifact (minimal enhancement)

After completing re-anchoring, the agent MUST produce a small audit artifact named `REANCHOR_REPORT_[DATE].md` placed in the project root. The report must be lightweight and include:
- Mode used (if any)
- Timestamp
- Agent id/version (tool name or identifier, optional)
- Brief summary of files ingested (canonical vs supporting)
- List of missing or flagged items and whether they are blocking
- Short proceed/halt recommendation

This artifact restores verifiability while keeping the workflow light.

---

## Automatic Re-Anchoring on Re-Entry (preserved)

Re-anchoring is required on any resumption of work after a break in continuity. No work may proceed until re-anchoring is complete unless explicitly waived by the project owner.

---

## Required Acknowledgement (preserved)

After re-anchoring, explicitly confirm:
- Procedural authority was ingested first
- Full traversal (or mode-based traversal) completed
- All files acknowledged and classified
- Re-anchoring is complete or blocked (with reasons)

Failure to meet these conditions constitutes incomplete execution.

---

## Summary (minimal v2)

This v2 document is a minimal clone of the original protocol with two targeted improvements:
1. Project/repo-agnostic wording for canonical materials
2. A lightweight AI audit artifact (`REANCHOR_REPORT_[DATE].md`) to preserve verifiability

These changes preserve the original structure and rigor while reducing human overhead and making the protocol applicable across repositories.

### Mode 1 — Fast-Path
- Trigger: No new canonical ZIP; periodic or scheduled check.
- Action: Reaffirm baseline canon; consider session conversation; produce `REANCHOR_REPORT`.

### Mode 2 — Snapshot (ZIP-only)
- Trigger: Canonical ZIP provided; no `ls -R` listing.
- Action: Treat the ZIP as authoritative snapshot; ingest all canonical files in full.
- Reporting/Flagging policy (mandatory):
  - AI must list every expected canonical filename and indicate `Found` or `Missing`.
  - Missing canonical files are flagged as **non-blocking** by default but recorded.
  - Any explicit contradictions within canon files are **blocking** and must halt progress until resolved.

### Mode 3 — Targeted Ingestion (ZIP + gitshow/diff)
- Trigger: Canonical ZIP + `.gitshow` or similar diff file provided.
- Action: Perform Mode 2 ingest, then ingest only files listed in the diff for additional review.
- Reporting/Flagging policy (mandatory):
  - For every file in the diff, report ingestion result and whether the change is consistent with canon.
  - Changes that create inconsistency with canonical invariants are **blocking** and must halt work.

### Mode 4 — Full Re-Anchor (`ls -R`)
- Trigger: `ls -R` directory listing provided or explicit user request.
- Action: Enumerate files exactly as listed (or enumerate the accessible workspace if `ls -R` is not a literal listing), ingest all canonical files in full, enumerate supporting artifacts, and surface all gaps/conflicts.
- Reporting: Full `REANCHOR_REPORT` with file counts, ingest summary, and blocking issues.

---

## REANCHOR_REPORT (AI Audit Artifact)

After any re-anchor the AI MUST create `REANCHOR_REPORT_[DATE].md` and commit/store it
in the project root. The report must include:
- Re-anchor mode used
- Timestamp and agent id/version (tool name or identifier, optional)
- Canonical ZIP name (if present)
- Summary of files ingested (canonical and supporting)
- List of missing expected canonical files
- List of flagged items (blocking vs non-blocking)
- Clear statement: `PROCEED` or `HALT` with reasons

Purpose: low-overhead audit trail the human and any downstream reviewers can open.

---

## Precedence Rules

1. `ls -R` forces Full Re-Anchor
2. Canonical ZIP supersedes prior state
3. `.gitshow`/diffs are informative and non-canonical
4. Conversation is advisory only

---

## Required Checklist

Every re-anchor must satisfy the applicable items:
- [ ] Canon identified and ingested per mode
- [ ] `REANCHOR_REPORT_[DATE].md` produced and saved
- [ ] All blocking issues described and marked `HALT` if present
- [ ] Non-blocking flags recorded with remediation notes

---

## Blocking vs Non-Blocking

- Blocking: contradictions within canon; missing essential canon files referenced by other canon files; structural errors that prevent correct interpretation.
- Non-blocking: missing optional assets (images, marketing), incomplete drafts, version notes.

Blocking issues must stop substantive work until resolved by the project owner.

On BLOCKING: create `REANCHOR_ISSUE_[DATE].md`, notify the project owner, and set the `REANCHOR_REPORT` verdict to `HALT`.

---

## Enforcement

The AI must refuse to perform substantive irreversible changes if its `REANCHOR_REPORT` result is `HALT` due to blocking issues.

---

## Minimal Human Interaction Model

This protocol preserves an AI-first workflow: humans need only upload a canonical ZIP,
`.gitshow` (optional), or `ls -R` when they intend to force a particular mode. The AI
generates the audit artifact and enforces blocking rules; humans resolve blocks.

---

## Summary

This v2 protocol is AI-driven, preserves canon-first governance, enforces a mandatory
AI audit artifact, and defines clear blocking rules so the AI can operate with limited
human overhead while maintaining verifiability.
