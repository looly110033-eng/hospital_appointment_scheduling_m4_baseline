# Hospital Appointment Scheduling — Single-Agent Baseline

This repository contains the project's Single-Agent (SA) baseline notebook for hospital appointment scheduling. The notebook includes two experiments:

- **Experiment 1 — Easy / Static:** 20 doctors and 100 appointment requests.
- **Experiment 2 — Complex / Dynamic:** 40 doctors, 3,298 initial appointment requests, and 290 dynamic events covering cancellations, doctor unavailability, new appointment requests, and doctor schedule changes.

The implementation is a deterministic, rule-based scheduler. It does not call an external LLM or API.

## Requirements

- Python 3.10 or newer
- Jupyter Notebook or JupyterLab
- pandas

## Setup and run

1. Download or clone this repository.
2. Open a terminal in the repository folder.
3. Create and activate a virtual environment (recommended).

   **macOS / Linux**
   ```bash
   python3 -m venv .venv
   source .venv/bin/activate
   ```

   **Windows (PowerShell)**
   ```powershell
   py -m venv .venv
   .\.venv\Scripts\Activate.ps1
   ```

4. Install the dependencies:
   ```bash
   python -m pip install -r requirements.txt
   ```
5. Start Jupyter:
   ```bash
   jupyter notebook
   ```
6. Open `hospital_appointment_scheduling_m4_baseline and choose **Kernel → Restart Kernel and Run All Cells** (menu wording may vary by Jupyter version).

The notebook generates the experiment inputs and results as CSV files under `shared_experiment_inputs/`. Run all cells from the beginning in order so that every dataset and function is defined before it is used.

## Experiments and exported data

The notebook exports shared input datasets and baseline outputs to separate folders:

- `shared_experiment_inputs/experiment_1_easy_static/`
- `shared_experiment_inputs/experiment_2_complex_dynamic/`

These files are generated when the relevant export cells run. They are not required to be committed to the repository because the notebook generates them. For a fair later SA-versus-MAS comparison, use the same exported input cases and applicable constraints for both systems; do not compare results produced from different generated cases.

## Expected checks from the notebook

The following results were observed when the submitted notebook was executed from the first cell to the last in a Python environment with pandas and Jupyter/IPython available:

- **Experiment 1:** 100 requests; 100 scheduled; 0 unscheduled; 0 reported constraint violations; the end-to-end M4 verification passes.
- **Experiment 2 initial schedule:** 3,298 requests; 3,113 scheduled; 185 unscheduled; 0 reported constraint violations.
- **Experiment 2 after dynamic events:** 3,318 active requests; 3,107 scheduled; 211 active requests unscheduled; 0 reported final constraint violations. The event summary reports 290 events in total.

These are baseline outputs, not a claim that the MAS outperforms the baseline. The notebook itself implements and evaluates the Single-Agent baseline.

## Repository contents

- `hospital_appointment_scheduling_m4_baseline — the full notebook, including both experiments.
- `README.md` — setup, execution, experiment overview.
- `requirements.txt` — Python package dependencies.
- `.gitignore` — excludes local environments, notebook checkpoints, and generated outputs.
