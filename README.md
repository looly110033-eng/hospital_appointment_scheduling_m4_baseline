# Hospital Appointment Scheduling — Single-Agent Baseline

This repository contains the project's Single-Agent (SA) baseline notebook for hospital appointment scheduling. The notebook includes two experiments:

- **Experiment 1 — Easy / Static:** 20 doctors and 100 appointment requests, with an end-to-end verification block for the M4 live demonstration.
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
6. Open `Hospital_Appointment_Scheduling_FULL_PROJECT.ipynb` and choose **Kernel → Restart Kernel and Run All Cells** (menu wording may vary by Jupyter version).

The notebook generates the experiment inputs and results as CSV files under `shared_experiment_inputs/`. Run all cells from the beginning in order so that every dataset and function is defined before it is used.

Suggested sequence:

1. **0:00–0:40 — Task and setup:** State that this is a rule-based Single-Agent baseline and that the demo uses the Easy / Static environment.
2. **0:40–1:40 — Inputs:** Show the generated doctor, patient, request, and time-slot datasets.
3. **1:40–3:00 — Scheduler:** Briefly show the scheduling logic and the resulting appointment schedule.
4. **3:00–4:20 — Validation and metrics:** Show the constraint-validation results and baseline evaluation.
5. **4:20–5:00 — M4 verification:** Run/show the `Live Demo Verification — Easy / Static Baseline` block and point to the assertion confirming that all 100 requests are accounted for, all 100 are scheduled, and there are zero reported constraint violations.

For a live presentation, have the notebook open and the kernel ready. If starting from a fresh kernel, run the cells in order; do not run the verification block before the earlier cells that create its inputs and schedule.

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

- `Hospital_Appointment_Scheduling_FULL_PROJECT.ipynb` — the full notebook, including both experiments and the M4 end-to-end verification block.
- `README.md` — setup, execution, experiment overview, and live-demo instructions.
- `requirements.txt` — Python package dependencies.
- `.gitignore` — excludes local environments, notebook checkpoints, and generated outputs.
- `M4_LIVE_DEMO_GUIDE.md` — a short presentation checklist.
