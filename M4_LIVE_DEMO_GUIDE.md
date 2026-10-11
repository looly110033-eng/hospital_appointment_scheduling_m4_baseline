# M4 Live Demo — 5-Minute Checklist

## Before the demo
- Open `Hospital_Appointment_Scheduling_FULL_PROJECT.ipynb`.
- Restart the kernel and run the notebook cells in order, or prepare the notebook with the outputs from a successful full run.
- Keep the Easy / Static experiment and its `Live Demo Verification — Easy / Static Baseline` block easy to locate.

## Demo sequence

- **0:00–0:40 — Objective:** Explain that this is a rule-based Single-Agent baseline for appointment scheduling.
- **0:40–1:40 — Inputs:** Show the doctor, patient, appointment-request, and time-slot data.
- **1:40–3:00 — Scheduling:** Show the scheduling logic and generated schedule.
- **3:00–4:20 — Evaluation:** Show the validation and baseline metrics.
- **4:20–5:00 — End-to-end check:** Show the M4 verification output and the passing assertion.

## Evidence to point out
- Total requests: 100
- Scheduled: 100
- Unscheduled: 0
- Constraint violations: 0
- All requests accounted for: `True`
- End-to-end verification: `True`

Keep the explanation focused on the baseline's completed task and validation. The complex/dynamic experiment is included in the same notebook as the broader evaluation; it does not need to be walked through in detail during this five-minute demo.
