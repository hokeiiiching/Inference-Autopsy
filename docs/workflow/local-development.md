# Local Development

## Purpose

Define local setup expectations.

## Reference When

Use when onboarding or setting up the repository.

## AI Agents Must Obey

Keep setup simple and cross-platform where practical.

## Expected Setup

```bash
python -m venv .venv
source .venv/bin/activate
pip install -e ".[dev]"
pytest
ruff check .
mypy autopsy
```

On Windows PowerShell:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -e ".[dev]"
pytest
ruff check .
mypy autopsy
```

## Local Fake Endpoint

Integration tests should use a local fake OpenAI-compatible endpoint rather
than live provider calls.

