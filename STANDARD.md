# Python Engineering Coding Standard

**Version:** 1.0  
**Scope:** Python used for engineering calculations, analysis, automation, data processing, and supporting applications.

This is a lightweight, reference-based coding standard. It does **not** reproduce upstream style guides or impose a software certification process.

## 1. Referenced guidance

Apply the following sources to their stated topics. Read the linked guidance as needed; do not copy its text into project rules.

| Subject | Reference | Application |
| --- | --- | --- |
| Python style, naming, imports, layout | [PEP 8](https://peps.python.org/pep-0008/) | Baseline coding conventions |
| Public API documentation and docstrings | [PEP 257](https://peps.python.org/pep-0257/) | Docstring conventions |
| Practical scientific-software development | [Scientific Python Development Guide](https://learn.scientific-python.org/development/) | Proportionate project organization, typing, documentation, and development practices |
| Testing principles | [Scientific Python testing recommendations](https://learn.scientific-python.org/development/principles/testing/) | Appropriate unit, integration, and public-interface tests |
| Style/tool configuration | [Scientific Python style guide](https://learn.scientific-python.org/development/guides/style/) | Automated formatting and linting practices |

**Implementation tools (not additional coding standards):** [Ruff](https://docs.astral.sh/ruff/) for formatting/linting and [pytest](https://docs.pytest.org/) for testing. A starter configuration is supplied at `templates/pyproject.toml`.

## 2. Engineering-specific requirements

These requirements supplement the references only where engineering tools need explicit treatment.

**ENG-01 — Calculation interfaces.** For inputs and outputs representing physical quantities, make units, reference conditions, sign conventions, and applicable validity domains unambiguous at public interfaces. Document important numerical assumptions.

**ENG-02 — Invalid and infeasible results.** Define and handle invalid inputs, out-of-domain values, non-convergence, and infeasible solutions explicitly. Do not silently substitute plausible-looking results, clamp values, or suppress failures unless that behavior is intentional, documented, and tested.

**ENG-03 — Numerical verification.** Tests of consequential calculations must include independently established expected results, representative boundaries, and justified numerical tolerances. Do not derive all expected outputs from the implementation under test. Select the extent of testing according to the tool's intended use and risk.

**ENG-04 — Reproducibility.** Results intended for engineering decisions must be reproducible from recorded inputs, configuration, relevant algorithm/data versions, and any random seeds. Keep computation deterministic when practical.

**ENG-05 — Separation of concerns.** Keep engineering calculation logic independently testable from UI, file handling, network access, and report generation where practical. Do not add abstractions or architectural layers without a clear benefit.

## 3. Enforcement and exceptions

- Adopt Ruff and pytest using the minimal example configuration in `templates/pyproject.toml`. Merge it into an existing project configuration; do not replace working project settings wholesale.
- Default checks: `ruff check .`, `ruff format --check .`, and `pytest` (using the project's defined test environment).
- Treat automated checks as a minimum, not evidence that engineering results are correct.
- Apply changes to the touched scope; avoid unrelated reformatting and opportunistic refactoring.
- A deviation requires a short, reviewable reason in the change/PR or the project's documented exception register. Do not use blanket suppressions merely to pass checks.

**Order of precedence:** Applicable safety/regulatory requirements and approved project verification plans > project-specific documented requirements/configuration > Section 2 > referenced guidance. Resolve conflicting instructions explicitly, rather than guessing.

**Limit:** Conformance with this standard alone does not establish fitness for a safety-critical application, DO-178C compliance, validation, or certification credit.
