# SonarQube Agentic Workflow — Usage Directive (MUST FOLLOW)

## GUIDE Phase — Before Generating Code
1. Call `get_guidelines` for project context and coding standards.
2. Locate existing code with `search_by_signature_patterns` or
   `search_by_body_patterns`. Do this before exploring files directly —
   they will speed up the process.
3. Read implementation with `get_source_code`.

When changing architecture or dependencies:
- Check `get_current_architecture` and `get_intended_architecture`.
- Analyze impact using:
  - `get_upstream_call_flow` / `get_downstream_call_flow` — trace method calls.
  - `get_references` — find all usages.
  - `get_type_hierarchy` — check inheritance.

## VERIFY Phase — After Generating Code
1. Read Phase: Load current state of relevant source files.
2. Analysis Phase: Call `run_advanced_code_analysis` with:
   - filePath: Project-relative path.
   - branchName: Active development branch.
   - `fileScope`: `MAIN` or `TEST` depending on the code type.
3. Evaluation & Remediation:
   - Call `show_rule` for every issue.
   - Mandatory fix any issue with `impacts[].severity` of HIGH or BLOCKER,
     or any issue with `impacts[].softwareQuality` of SECURITY.
4. Verification: Re-run analysis after fixes to confirm resolution and
   no regressions.
