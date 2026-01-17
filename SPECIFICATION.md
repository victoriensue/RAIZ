# RAIZ Protocol Specification

**Version 1.0.0**
**Date: January 17, 2026**
**Status: Initial Release**

---

## 1. Abstract

This document specifies the RAIZ Protocol, an open standard for preserving and transferring human cognitive identity across artificial intelligence systems. RAIZ defines data structures, communication protocols, and interoperability requirements for creating portable digital identities (e-DNA) that maintain context and continuity independent of any single AI platform.

---

## 2. Introduction

### 2.1 Purpose

RAIZ enables humans to maintain persistent cognitive context when interacting with AI systems. Unlike platform-specific memory features, RAIZ creates a user-owned, portable identity that works across any compliant AI system.

### 2.2 Scope

This specification covers:
- Data structure requirements
- File format standards
- Communication protocol
- Interoperability requirements
- Implementation guidelines

### 2.3 Terminology

| Term | Definition |
|------|------------|
| **e-DNA** | Electronic Digital Native Architecture — a structured representation of human cognitive patterns |
| **RAIZ Repository** | Local file system containing the three-layer structure |
| **Trigger** | Standardized command that initiates protocol actions |
| **Session** | A single conversation between human and AI |

---

## 3. Architecture

### 3.1 Three-Layer Structure

```
RAIZ/
│
├── ACTIVE_CONTEXT.md      # Current state pointer
├── ARCHITECTURE.md        # System documentation
│
├── 01_DATES/              # Layer 1: Timelapse
│   └── YYYY/MM/DD.md      # Daily records
│
├── 02_eDNA/               # Layer 2: Digital Identity
│   ├── personality/       # Behavioral traits
│   ├── reasoning/         # Created concepts
│   └── patterns/          # Decision patterns
│
└── 03_PROJECTS/           # Layer 3: Application
    └── [project_name]/    # Project-specific context
        └── README.md      # Project state
```

### 3.2 Layer 1: DATES (Timelapse)

**Purpose:** Immutable chronological record of all interactions.

**Rules:**
- One file per day: `YYYY/MM/DD.md`
- Content is raw, unedited conversation summaries
- Files are append-only after creation
- Serves as source of truth

**Format:**
```markdown
# Session Record — YYYY-MM-DD

## Session 1 (HH:MM - HH:MM)
### Topics Covered
- [topic 1]
- [topic 2]

### Decisions Made
- [decision 1]

### Key Outputs
- [output 1]

---
```

### 3.3 Layer 2: e-DNA (Digital Identity)

**Purpose:** Extracted patterns that define the user's cognitive identity.

**Subdirectories:**

| Directory | Content |
|-----------|---------|
| `personality/` | Communication style, preferences, behavioral traits |
| `reasoning/` | Original concepts created by user |
| `patterns/` | Recurring decision patterns |

**Personality File Format:**
```markdown
# User Profile: [Name]

## Communication Style
- [trait 1]
- [trait 2]

## Thinking Patterns
- [pattern 1]
- [pattern 2]

## Decision Patterns
- [pattern 1]

## Technical Level
- [description]

## Created Concepts
### [Concept Name] (Date)
[Brief description]
File: `reasoning/[number]_[name].md`
```

### 3.4 Layer 3: PROJECTS

**Purpose:** Context-specific knowledge for active work areas.

**Structure:**
```
03_PROJECTS/
└── [PROJECT_NAME]/
    ├── README.md       # Project status and context
    ├── decisions.md    # Key decisions made
    └── outputs/        # Generated artifacts
```

**README Format:**
```markdown
# Project: [Name]

## Status
[Current state]

## Objective
[What we're trying to achieve]

## Context
[Relevant background]

## Pending
- [ ] Task 1
- [ ] Task 2

## Related Documents
- [link 1]
```

---

## 4. Communication Protocol

### 4.1 Session Start Trigger

**Command:** "Good morning [AI_NAME]" (or localized equivalent)

**AI Actions:**
1. Read `ACTIVE_CONTEXT.md`
2. Read primary e-DNA file (`02_eDNA/personality/[user].md`)
3. Identify active project from context
4. Read project README if applicable
5. Check last DATES entry for continuity
6. Respond with context summary
7. Ask: "Continue where we left off or start something new?"

### 4.2 Session End Trigger

**Command:** "Goodbye [AI_NAME]" (or localized equivalent)

**AI Actions:**
1. Create/update `01_DATES/YYYY/MM/DD.md` with session summary
2. If new pattern identified → add to `02_eDNA/`
3. If worked on project → update `03_PROJECTS/[name]/README.md`
4. Update `ACTIVE_CONTEXT.md` with final state
5. Respond: "Saved! [summary]. You can safely close this conversation."

### 4.3 Trigger Localization

| Language | Start | End |
|----------|-------|-----|
| English | "Good morning [AI]" | "Goodbye [AI]" |
| Portuguese | "Bom dia [AI]" | "Tchau [AI]" |
| Spanish | "Buenos días [AI]" | "Adiós [AI]" |

---

## 5. File Format Requirements

### 5.1 Encoding

- UTF-8 without BOM
- Unix line endings (LF)

### 5.2 Format

- Markdown (.md) for all text files
- No binary files in core structure
- Images referenced by path, not embedded

### 5.3 Naming Conventions

| Type | Convention | Example |
|------|------------|---------|
| Date files | `DD.md` | `17.md` |
| Concept files | `NNN_name.md` | `001_three_layer_system.md` |
| Project folders | `UPPERCASE_NAME` | `CLIENT_MIGRATION` |

---

## 6. Non-Revalidation Principle

### 6.1 Definition

Information stored in the RAIZ repository is considered **validated truth**. Compliant AI systems MUST NOT:
- Question the accuracy of repository content
- Request confirmation of stored facts
- Suggest alternatives to documented decisions

### 6.2 Rationale

Repository content has been reviewed, validated, and committed by the user. Revalidation wastes tokens and undermines trust.

### 6.3 Exception

AI MAY flag apparent contradictions between repository content and current conversation, but MUST defer to repository as authoritative.

---

## 7. Interoperability

### 7.1 Universal Format

Markdown (.md) is chosen because:
- Plain text (minimal token cost)
- Human and machine readable
- No platform dependency
- Supported by all major AI systems

### 7.2 Token Efficiency

Target metrics for RAIZ overhead:
- ACTIVE_CONTEXT.md: <500 tokens
- Primary e-DNA file: <1,000 tokens
- Project README: <500 tokens
- **Total context load: <2,000 tokens** (<2% of typical context window)

### 7.3 AI Platform Requirements

To be RAIZ-compliant, an AI system MUST:
1. Read local files via tool/function
2. Write local files via tool/function
3. Recognize trigger commands
4. Apply e-DNA as behavioral filter
5. Respect non-revalidation principle

---

## 8. Security Considerations

### 8.1 Access Control

- RAIZ repository is local (user's file system)
- AI accesses only during active session
- User controls sharing permissions

### 8.2 Privacy

- e-DNA contains personal behavioral data
- Users SHOULD NOT share raw e-DNA publicly
- Anonymization guidelines needed for research use

### 8.3 Integrity

- Date files are append-only
- Changes to e-DNA should be logged
- Version control (git) recommended

---

## 9. Future Work

### 9.1 Semantic Tokenization

Proposed: Allow validated meaning blocks to be treated as single tokens, reducing reprocessing overhead.

### 9.2 ID Standard

Proposed: Universal identifier for individuals and organizations, enabling cross-platform identity verification.

### 9.3 Certification Program

Planned: RAIZ-Certified and RAIZ-Compatible designations for compliant systems.

---

## 10. References

- Iensue, V. (2026). "e-DNA: Digital Identity Extraction from Human-AI Interaction"
- Iensue, V. (2026). "Three-Layer Cognitive Architecture"
- Iensue, V. (2026). "Semantic Tokenization Proposal"

---

## 11. Changelog

| Version | Date | Changes |
|---------|------|---------|
| 1.0.0 | 2026-01-17 | Initial release |

---

## 12. Author

**Victor Iensue**
- Role: Creator, Conceptual Architecture
- Contact: victor.iensue@yahoo.com

---

*End of Specification*
