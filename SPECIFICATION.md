# RAIZ Protocol Specification

**Version 1.0.0**

**Date: January 17, 2026**

**Author: Victor Iensue**

---

## Table of Contents

1. Abstract
2. Introduction
3. Architecture
4. Communication Protocol
5. File Format Requirements
6. Non-Revalidation Principle
7. Interoperability
8. Security Considerations
9. Future Work
10. References
11. Changelog
12. Author

---

## 1. Abstract

RAIZ (from Portuguese "root") is an open protocol specification for preserving and porting human cognitive identity across artificial intelligence systems. This document defines the three-layer architecture, communication protocols, and file format requirements for RAIZ-compatible implementations.

The protocol enables users to maintain continuity of context, preferences, and knowledge patterns when interacting with AI systems, regardless of the underlying platform or model.

---

## 2. Introduction

### 2.1 Purpose

The purpose of this specification is to define a standardized method for:

- Preserving human-AI interaction history
- Extracting and maintaining cognitive identity patterns
- Enabling portability of digital identity across AI platforms
- Reducing computational overhead through semantic tokenization

### 2.2 Scope

This specification covers:

- Data structure and organization
- File format requirements
- Communication protocol between human and AI
- Interoperability requirements

This specification does not cover:

- Specific AI model implementations
- User interface requirements
- Network protocols for data transmission

### 2.3 Terminology

| Term | Definition |
|------|------------|
| RAIZ | Root Architecture for Identity Zero-loss |
| e-DNA | Electronic DNA - digital cognitive identity |
| Timelapse | Chronological record layer |
| Trigger | Command that initiates protocol action |
| Session | Single conversation instance |
| Context Window | AI's active memory during session |

---

## 3. Architecture

### 3.1 Three-Layer Structure

RAIZ defines three distinct layers for organizing human-AI knowledge:
```
┌─────────────────────────────────────────────┐
│           LAYER 1: DATES (Timelapse)        │
│                                             │
│  - Raw chronological records                │
│  - Immutable conversation logs              │
│  - Timestamp-based organization             │
│  - Format: YYYY-MM-DD_topic.md              │
└─────────────────────────────────────────────┘
                      │
                      ▼ (extraction)
┌─────────────────────────────────────────────┐
│        LAYER 2: e-DNA (Digital Identity)    │
│                                             │
│  - Behavioral patterns                      │
│  - Communication preferences                │
│  - Decision-making styles                   │
│  - Knowledge domain mappings                │
│  - Values and priorities                    │
└─────────────────────────────────────────────┘
                      │
                      ▼ (application)
┌─────────────────────────────────────────────┐
│        LAYER 3: PROJECTS (Application)      │
│                                             │
│  - Context-specific knowledge               │
│  - Active project documentation             │
│  - Domain-specific rules                    │
│  - Temporary working memory                 │
└─────────────────────────────────────────────┘
```

### 3.2 Layer 1: DATES (Timelapse)

**Purpose:** Immutable chronological record of all interactions.

**Requirements:**
- Files MUST be named with ISO date format: `YYYY-MM-DD_description.md`
- Content MUST NOT be modified after session completion
- Each file represents one session or logical unit
- Files MUST be stored in `01_DATAS/` directory

**Example structure:**
```
01_DATAS/
├── 2026-01-15_initial_setup.md
├── 2026-01-16_business_planning.md
└── 2026-01-17_protocol_development.md
```

### 3.3 Layer 2: e-DNA (Digital Identity)

**Purpose:** Extracted patterns that define the user's cognitive identity.

**Requirements:**
- Files organized by category in `02_eDNA/` directory
- Content is refined over time (mutable)
- Represents validated, stable patterns
- MUST include at minimum: personality profile, communication style

**Required subdirectories:**
```
02_eDNA/
├── personalidade/     # Personality traits
├── comunicacao/       # Communication patterns
├── decisao/          # Decision-making patterns
├── conhecimento/     # Knowledge domains
└── valores/          # Values and priorities
```

### 3.4 Layer 3: PROJECTS (Application)

**Purpose:** Context-specific knowledge for active work.

**Requirements:**
- Organized by project in `03_PROJETOS/` directory
- Contains working documentation
- May reference e-DNA and DATES layers
- Follows project-specific organization

**Example structure:**
```
03_PROJETOS/
├── PROJECT_A/
│   ├── README.md
│   ├── requirements.md
│   └── progress.md
└── PROJECT_B/
    └── ...
```

---

## 4. Communication Protocol

### 4.1 Trigger Commands

RAIZ defines specific trigger phrases that initiate protocol actions:

| Trigger (EN) | Trigger (PT) | Action |
|--------------|--------------|--------|
| "Good morning Claude" | "Bom dia Claudio" | Initialize session, load full RAIZ context |
| "Goodbye Claude" | "Tchau Claudio" | Save session, update DATES, sync e-DNA |

### 4.2 Session Initialization

When initialization trigger is detected, AI MUST:

1. Read `CONTEXTO_ATIVO.md` from RAIZ root
2. Load referenced e-DNA files
3. Load active project context
4. Acknowledge loaded context to user

### 4.3 Session Termination

When termination trigger is detected, AI MUST:

1. Create session summary
2. Save to DATES layer with current date
3. Update `CONTEXTO_ATIVO.md` if needed
4. Propose e-DNA updates if patterns detected
5. Confirm completion to user

### 4.4 Context File Structure

The `CONTEXTO_ATIVO.md` file MUST contain:
```markdown
# Active Context

## Current Focus
[Primary objective or project]

## Active e-DNA References
- [path to relevant e-DNA files]

## Active Projects
- [path to relevant project files]

## Session Priorities
1. [Priority 1]
2. [Priority 2]

## Recent Updates
- [Date]: [Update description]
```

---

## 5. File Format Requirements

### 5.1 Encoding

- All files MUST be UTF-8 encoded
- No BOM (Byte Order Mark)
- Line endings: LF (Unix-style)

### 5.2 Format

- All documentation MUST be in Markdown (.md)
- MUST follow CommonMark specification
- YAML frontmatter is OPTIONAL

### 5.3 Naming Conventions

| Type | Convention | Example |
|------|------------|---------|
| Date files | `YYYY-MM-DD_description.md` | `2026-01-17_meeting.md` |
| e-DNA files | `snake_case.md` | `communication_style.md` |
| Project files | `UPPER_CASE/` for folders | `PROJECT_RAIZ/` |

### 5.4 Maximum File Size

- Individual files SHOULD NOT exceed 50KB
- Large content SHOULD be split into multiple files
- Target: entire RAIZ context loadable in <100K tokens

---

## 6. Non-Revalidation Principle

### 6.1 Definition

Once information is validated and stored in e-DNA layer, it MUST NOT require re-validation in subsequent sessions unless explicitly contradicted.

### 6.2 Implementation

AI systems implementing RAIZ MUST:

1. Treat e-DNA content as pre-validated truth
2. Not question established patterns unless user indicates change
3. Apply e-DNA preferences automatically
4. Only update e-DNA through explicit refinement process

### 6.3 Rationale

This principle:
- Reduces redundant processing
- Maintains consistency across sessions
- Respects user's established identity
- Enables semantic tokenization optimization

---

## 7. Interoperability

### 7.1 Platform Independence

RAIZ is designed to work across:
- Different AI models (Claude, GPT, Gemini, etc.)
- Different interfaces (web, API, local)
- Different operating systems

### 7.2 Universal Format

The use of Markdown ensures:
- Human readability
- Version control compatibility
- No proprietary dependencies
- Easy migration between systems

### 7.3 Token Efficiency

Implementations SHOULD optimize for token efficiency:
- Target: <2,000 tokens for core context load
- Use references instead of duplicating content
- Implement lazy loading for project details

---

## 8. Security Considerations

### 8.1 Data Ownership

- All RAIZ data is owned by the user
- No data should be transmitted without explicit consent
- Local storage is the default and recommended mode

### 8.2 Sensitive Information

- Users SHOULD NOT store passwords or secrets in RAIZ
- Financial details SHOULD be abstracted
- Personal identifiers SHOULD be minimized

### 8.3 Access Control

- RAIZ directories SHOULD have appropriate file permissions
- Encryption is RECOMMENDED for cloud storage
- Backup procedures SHOULD be documented

---

## 9. Future Work

### 9.1 Semantic Tokenization

Future versions will define:
- Token format for validated knowledge blocks
- Compression algorithms for e-DNA
- Caching mechanisms for AI systems

### 9.2 RAIZ ID Standard

Proposed unique identifier system:
- Format: `RAIZ-[COUNTRY]-[YEAR]-[SEQUENCE]`
- Example: `RAIZ-BR-2026-000001`
- Registration and verification procedures

### 9.3 Certification Program

Planned certification for:
- RAIZ-Compatible AI systems
- RAIZ-Certified implementations
- Training and consulting providers

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
