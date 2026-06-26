---
name: fast-reader
description: "High-efficiency document analyzer for code, logs, manuals, and reports. Use when the user asks to read, summarize, analyze, or extract key points from large documents, aiming to save context tokens while retaining core insights."
when_to_use: "Trigger when the user uploads a large text file, asks for a document summary, wants to find specific errors in logs, or requests an analysis of a project plan/test report without reading the entire file."
allowed-tools: Read, Grep, Glob
---

# Fast Reader: High-Efficiency Document Analyzer

## Core Philosophy
Do not read documents linearly. Treat document analysis like "mining for gold": extract high-value structural information first, and only dive into details when strictly necessary. This prevents context window bloat and reduces token consumption.

## Execution Workflow

### Phase 1: Structural Reconnaissance (Pre-reading)
Before reading the full content, establish a mental map of the document:
1. **Identify Document Type**: Quickly determine if it's Code, Logs, Manual, Plan, or Test Report.
2. **Extract Skeleton**: Read ONLY the first 50 lines, the last 20 lines, and all headers/titles. 
3. **Formulate Hypothesis**: Based on the skeleton, deduce the document's core purpose and structure.

### Phase 2: Targeted Extraction (Skimming & Scanning)
Apply different strategies based on the document type:

- **For Code**: 
  - Skip boilerplate and imports. 
  - Focus strictly on exported functions, class definitions, and core business logic.
- **For Logs / Error Reports**:
  - Use `Grep` to search for keywords: `ERROR`, `FATAL`, `Exception`, `Traceback`, `WARN`.
  - Read only the surrounding 5 lines of matched keywords to get context. Ignore standard `INFO`/`DEBUG` noise.
- **For Manuals / Plans / Test Reports**:
  - Apply the 80/20 rule: Focus entirely on Executive Summaries, Conclusions, Risk Assessments, and Action Items.
  - Skip lengthy background introductions, repetitive examples, and known baseline information.

### Phase 3: Synthesis & Output (Post-reading)
Generate a highly structured, concise summary for the user. Never output raw copied text. Use this exact format:

##  Core Summary
[1-3 sentences explaining what this document is and its ultimate goal]

## ️ Key Highlights / Findings
- [Bullet point 1: Most critical takeaway or finding]
- [Bullet point 2: Important structural change or metric]
- [Bullet point 3: Actionable item or unresolved issue]

## ️ Risks / Action Items (If applicable)
- [Specific error to fix, missing test case, or next step required]

##  Token-Saving Note
[Briefly mention what parts of the document were intentionally skipped to save context, e.g., "Skipped 500 lines of boilerplate setup code and standard INFO logs."]