
What I created (prototype & download)

A tiny, explainable demo implementing three core AI Sentinel ideas:

1. Vulnerability Predictor — RandomForest model trained on synthetic code metrics to predict vulnerable modules. (Saved: vuln_clf.pkl, vuln_scaler.pkl.)


2. Anomaly Detector — IsolationForest trained on synthetic API telemetry to flag anomalous API behavior. (Saved: anomaly_iso.pkl.)


3. Exploit Simulator — A heuristic SQL-injection fuzzer that generates likely malicious queries to test detection logic. (exploit_simulator_attempts.csv.)



All artifacts packaged: sentinel_demo.zip


Key outputs shown (from the run)

Vulnerability predictor accuracy ≈ 65.8% on synthetic data (proof-of-concept — can be improved with real datasets).

Anomaly detector correctly flagged the injected anomaly samples (anomaly_score = -1 for anomalies).

Exploit simulator generated queries and heuristically marked potential SQL injections.


What's inside the ZIP

synthetic_code_metrics.csv — synthetic training data.

vuln_clf.pkl, vuln_scaler.pkl — saved vulnerability model + scaler.

vuln_summary.json — metrics and classification report.

synthetic_api_telemetry.csv — synthetic telemetry for anomaly detector.

anomaly_iso.pkl — saved IsolationForest model.

anomaly_test_samples.csv — sample rows showing anomaly predictions.

exploit_simulator_attempts.csv — simulated queries and flags.



How you can build this into a real AI Sentinel

1. Replace synthetic data with real inputs

Ingest: commit metadata, static analysis outputs, dependency manifests, telemetry logs, WAF logs, API gateway logs.

Label: Use historical incidents/patches to label vulnerable vs non-vulnerable code paths.



2. Improve models

Vulnerability Predictor: use LLM code encoders (CodeBERT/CodeT5) + Transformer fine-tuning for code semantics; add static-analysis features.

Anomaly Detector: add time-series models (LSTMs, Transformer time-series), and use federated learning on endpoint agents.

Exploit Simulator: evolve from heuristics to RL-based agent that learns exploit strategies against sandboxed apps.



3. Integrate into CI/CD & Runtime

Run Vulnerability Predictor on each PR/commit and fail builds with high-risk flags.

Run Exploit Simulator in a continuous security-fuzzing sandbox.

Deploy Anomaly Detector at API gateway + application layer to auto-isolate risky sessions.



4. Governance & Safety

Use federated learning for privacy.

Establish human-in-the-loop thresholds to avoid blocking legitimate traffic.

Audit logging + explainability for AI decisions.


