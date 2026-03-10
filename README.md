# FastF1 Playground

This repository is an exploratory project for telemetry/data-driven F1 analytics built around the `FastF1` Python library and public F1 APIs (Ergast etc.).

## Goal

- Gain hands-on experience with telemetry and race data APIs.
- Practice software engineering best practices in a small project.
- Build a showcase for internships/opportunities with data exploration, visualization, and reusable code.

## Repo structure

- `pyproject.toml` - project metadata, dependencies, and packaging setup (Poetry format).
- `modules/plot_results_tracker.py` - scripted example that fetches F1 race results, transforms to matrix format, and renders heatmap.
- `notebooks/plot_results_tracker.ipynb` - notebook version of the heatmap workflow from `modules` (Ergast + Plotly).
- `notebooks/example_fastf1_signalrclient.ipynb` - quick FastF1 session demo (`2024 Monza Q/R`) with lap-level data.

## What’s implemented

### `plot_results_tracker`
- Uses `fastf1.ergast.Ergast` API to load a full season schedule and race results.
- Supports sprint races in addition to main race data.
- Builds a wide table where rows are drivers and columns are races, with points per cell.
- Sorts drivers by total points and plots a heatmap with `plotly.express.imshow`.

### `example_fastf1_signalrclient`
- Instantiates `fastf1` sessions for qualifying/race.
- Loads session data and demonstrates basic API calls:
  - results
  - lap data
  - fastest lap selection
  - per-driver slices
  - event metadata and weather.

## Dependencies

As documented in `pyproject.toml`:
- Python >= 3.10
- `fastf1`, `pandas`, `numpy`
- Visualization: `plotly`, `matplotlib`, `seaborn`
- Notebook environment: `jupyter`, `notebook`, `ipykernel`
- Dev tooling: `black`, `ruff`

##  Usage

1. Create and activate a virtual environment:

   ```powershell
   python -m venv .venv
   .\.venv\Scripts\Activate.ps1
   poetry install
   ```

2. Run module script(optional. You can use the notebooks for interactive mode):

   ```powershell
   python modules\plot_results_tracker.py
   ```

3. Launch notebooks:

   ```powershell
   jupyter lab
   ```

   # OR

   ```powershell
   jupyter notebook
   ```

## Git ignore notes

- `.gitignore` includes `/.ipynb_checkpoints`, `/.vscode`, and `poetry.lock`.
- If these paths are already tracked, remove them from index.

## Next steps (extension ideas)

- add API key / rate-limit handling for Ergast/fastf1 endpoints.
- incorporate live telemetry and real-time graph updates.
- write unit tests for data transformation and edge cases.
- set up CI (GitHub Actions) for linting and notebook checks.

---

*This is a learning-focused sandbox while building towards production-grade telemetry tooling and a portfolio story.*
