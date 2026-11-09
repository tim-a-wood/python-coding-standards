# Python Engineering Coding Standard

A lightweight, reference-based coding standard for Python engineering tools. Established guidance is linked rather than duplicated; only engineering-specific requirements are defined locally.

**[Read the standard](STANDARD.md)**

## Using this in another repository

1. Copy [templates/AGENTS.md](templates/AGENTS.md) to the root of your target repository as `AGENTS.md`.
2. Make sure the coding agent can read the [canonical standard](STANDARD.md) on GitHub. If network access is restricted, supply the standard file directly.
3. If using Ruff, merge [templates/pyproject.toml](templates/pyproject.toml) into the target project's existing configuration rather than replacing it.
4. Ask the agent to apply the standard, report deviations, and state which checks passed or could not run.

An `AGENTS.md` in **this** repository does not automatically govern other repositories.

## Suggested checks for target projects

```shell
python -m pip install ruff pytest
ruff check .
ruff format --check .
pytest
```

Respect the target project's established environment and test commands when available.

## Example agent prompt

> Read https://github.com/tim-a-wood/python-coding-standards/blob/main/STANDARD.md before making Python changes. Follow the linked upstream standards and the engineering-specific requirements, subject to higher-priority project requirements. Identify any justified deviations, and report lint, formatting, and relevant test results. If the document is inaccessible, say so rather than claiming compliance.

This standard is intended for general engineering software. It does not establish DO-178C or other certification compliance.
