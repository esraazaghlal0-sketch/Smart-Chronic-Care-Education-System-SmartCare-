# SmartCare / CareFlow AI

AI-assisted pediatric chronic care assistant (asthma and diabetes), built in n8n as a graduation project. A clinician always makes the final decision. All data in this repository is synthetic.

## The problem
Caregivers of children with chronic diseases receive fragmented support between clinic visits. Our system helps them get clear, source-based guidance and sends anything risky to a clinician for review.

## How the system works
The system is made of five connected n8n workflows:

| # | Workflow | What it does |
|---|----------|--------------|
| 1 | Patient intake and data protection | Collects the caregiver request, validates it, and removes sensitive data |
| 2 | Case extraction and summarisation | Turns the request into a structured case summary |
| 3 | Knowledge and patient guidance | Answers from approved medical sources (RAG) |
| 4 | Routing, human escalation and notifications | Routes by risk level and sends cases to a clinician for approval |
| 5 | Monitoring, evaluation and integration | Logs every run, traces AI calls, scores answers and raises alerts |

## Safety rules
- The AI never diagnoses, prescribes, or changes a dose.
- Higher-risk cases and emergencies go to a clinician for approval before anything reaches a family.
- Personal identifiers are removed before storage.
- No real patient data is used anywhere.

## Evaluation and monitoring (Workflow 5)
- Every AI call is traced in LangSmith.
- A second model (different from the one that writes answers) scores every answer from 1 to 5 on safety, factual accuracy, groundedness, format adherence and bias.
- A dashboard shows judge scores, safety average and minimum, run volume, latency and token cost.
- Alerts are set for safety, bias and hallucination.

## Repository structure
- 3_workflows: exported n8n workflows
- 6_pitch: presentation
- More folders (evaluation, test report, data) will be added as they are completed.

## Current limitations
- Tested only on a small set of synthetic cases.
- Judge scores are early results and have not yet been calibrated against human reviewers.
- Not validated for clinical use.

## Team
Group C
Noha Essam Abdelrahman Mohamed Yaseen (team leader)
Nada Hamdy Mohamed Osman
Asmaa Mohamed Mohamed Ramadan
Ayah Mohamed Zaki Shabana
Esraa Mostafa Attia Zaghlal
