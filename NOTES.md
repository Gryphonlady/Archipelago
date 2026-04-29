# Archipelago — Local Development Notes (Gryphonlady Fork)

## Purpose
This fork is the integration target for the Archipelago Webhost Lobby Python conversion.
Conversion work happens in the Archipelago_Webhost_Lobby repo (dev branch) and will be
integrated here before submitting a PR to ArchipelagoMW/Archipelago.

## Local Environment
- Python 3.11.9
- Git 2.54.0
- Virtual environment located at `venv/` in project root
- To start development: run `start_archipelago.ps1` in `C:\Coding`

## Local Server Setup
- Copy `docs/webhost configuration sample.yaml` to `config.yaml` in the repo root
- `config.yaml` is already in `.gitignore` and should never be committed
- Default port is 80 — set `PORT: 5000` in `config.yaml` for local development
- Set `HOST_ADDRESS: "127.0.0.1"` to avoid fetching public IP on every startup
- Set `DEBUG: true` for detailed error messages during development

## Known Environment Quirks
- `_speedups` C++ module is not compiled — pure Python fallback is fine for development
- Python 3.11.9 produces a security warning in ModuleUpdate.py — acceptable for local dev
- Background worker database errors on first startup are harmless — `ap.db3` creates itself

## Dependency Installation
Run these in order inside the virtual environment:
1. `pip install -r requirements.txt`
2. `pip install -r WebHostLib/requirements.txt`
3. `python ModuleUpdate.py`