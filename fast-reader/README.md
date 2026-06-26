
# Fast Reader: High-Efficiency Document Analyzer

##  Overview
**Fast Reader** is a specialized skill for Claude Code designed to revolutionize how AI processes large documents. By translating human "speed-reading techniques" into AI execution logic, it is optimized for analyzing codebases, system logs, technical manuals, project plans, and test reports.

Leveraging **Progressive Disclosure** and **On-Demand Retrieval**, Fast Reader precisely targets high-value information. It ensures zero loss of critical insights while significantly minimizing Context Window and Token consumption.

##  Key Features
- ** Structural Reconnaissance**: Rejects linear reading. Prioritizes extracting the document skeleton (headers, summaries, conclusions) to build a global mental map instantly.
- ** Scenario-Based Scanning**:
  - **Code**: Skips boilerplate and imports; focuses strictly on exported functions and core business logic.
  - **Logs**: Utilizes `Grep` to intercept `ERROR`, `Exception`, and `Traceback` keywords, automatically filtering out standard `INFO` noise.
  - **Reports/Manuals**: Applies the 80/20 rule. Extracts executive summaries, risks, and action items while skipping lengthy background introductions.
- ** Token Optimization**: Drastically reduces token overhead through strict tool limitations and structured output constraints.
- ** Standardized Output**: Enforces a concise template: Core Summary ️ Key Highlights ️ Risks/Action Items. Eliminates AI fluff and raw text copying.

##  Quick Start
1. Save the skill file to your project directory: `.claude/skills/fast-reader/SKILL.md`
2. Trigger the skill in Claude Code using commands like:
   - `/fast-reader Analyze the core logic of src/core/engine.ts`
   - `/fast-reader Summarize yesterday's deployment logs and find all errors`
   - `Quickly read this PRD and extract the core feature requirements`

## ️ Ideal Use Cases
- Onboarding to legacy codebases and grasping the architecture quickly.
- Incident response: locating root causes in massive log files.
- Reviewing extensive technical proposals or QA test reports to extract actionable conclusions.



---

