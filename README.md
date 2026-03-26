# myskills

Personal Codex skills repository for AI-assisted engineering, architecture, frontend, backend, debugging, and workflow automation.

This repository mirrors the current contents of `~/.codex/skills` and is intended as a backup, distribution source, and long-term versioned storage for reusable skills.

## What Is In This Repo

Each skill lives in its own directory and normally contains:

- `SKILL.md`
  The main trigger and workflow definition.
- `agents/openai.yaml`
  Optional UI metadata for the skill.
- `references/`
  Reference material loaded only when needed.
- `scripts/`
  Helper scripts used by the skill.
- `assets/`
  Static files such as templates or icons.

There is also a `.system/` directory containing system-level skills bundled into the local Codex environment.

## Notable Skills

- `evolutionary-constraint-engineering`
  Turns vague intent into validated constraints before implementation. Useful for ambiguous, high-stakes, or cross-module work.
- `test-driven-development`
  Enforces red-green-refactor before implementation.
- `verification-before-completion`
  Requires fresh evidence before claiming success.
- `systematic-debugging`
  Structured debugging workflow for hard failures and flaky behavior.
- `frontend-skill`
  Visual design discipline for stronger frontend output.

## Repository Layout

```text
myskills/
├── .system/
├── brainstorming/
├── evolutionary-constraint-engineering/
├── frontend-skill/
├── systematic-debugging/
├── test-driven-development/
├── verification-before-completion/
└── ...
```

## How To Use

### Option 1: Replace local skills with this repo

Clone the repository and sync it into your local Codex skills directory.

```bash
git clone https://github.com/QZYWQ/myskills.git
cp -a myskills/. ~/.codex/skills/
```

### Option 2: Pull updates into an existing local copy

```bash
cd myskills
git pull
cp -a . ~/.codex/skills/
```

## Maintenance Notes

- This repository is a versioned snapshot of the local Codex skills directory.
- Python cache files are ignored via `.gitignore`.
- When creating or modifying a skill, validate it before pushing.

Example validation:

```bash
python3 ~/.codex/skills/.system/skill-creator/scripts/quick_validate.py ~/.codex/skills/<skill-name>
```

## Recommended Workflow For New Skills

1. Create or edit the skill locally in `~/.codex/skills/`.
2. Validate the skill.
3. Sync changes into this repository.
4. Commit and push.

## License

This repository contains a mix of personal skills and bundled upstream/system skills. Check the individual skill directories for any bundled license files when redistribution matters.
