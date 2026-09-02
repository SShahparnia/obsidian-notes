# AI Ethics in Robotics — Idea Reference (Meeting w/ Prof. Wu)

  

Two sections: (A) standalone AI-ethics-in-robotics directions, not tied to her group's paper; (B) concrete ways to extend her group's existing paper (*_Standards-Aligned Ethical Gating and Decision Telemetry for LLM-Assisted Mobile Robot Navigation_*, IEEE BigDataService 2026). Each idea has what it is, why it fits a 295A/295B two-semester project, and a rough technical approach.

  

---

  

## A. Standalone AI Ethics Directions

  

### A1. Fairness/Bias Audit for Robot Behavior Around People

****What:**** Test whether a robot treats people differently based on perceptible attributes — stopping distance, speed, path deflection, deference behavior — depending on who's around it (appearance, group size, apparent age, etc.).

****Why it fits:**** Applies algorithmic-fairness methodology (audit, disparity metrics, statistical testing) to *_embodied_* robot behavior instead of a screen-based classifier — genuinely under-studied territory, and a natural sibling to the fairness-audit framing we explored for the BAC idea, without the enforcement-consequence baggage.

****Approach:**** Simulated (Webots/Gazebo) or real small-robot trials with varied human-avatar/actor conditions; log behavior deltas; statistical significance testing across conditions; then evaluate mitigation (behavior-normalization constraints).

****Two-semester shape:**** 295A = build the audit harness + pilot study; 295B = scale trials, add mitigation, human-subjects validation if feasible.

  

### A2. Adversarial Robustness of Ethical Decision-Making

****What:**** Attack the *_inputs_* an ethics-gated robot relies on — spoofed signage, manipulated sensor data, prompt-injection via perceived scene text — and test whether an attacker can force it to violate its own stated ethical constraints.

****Why it fits:**** A safety/security crossover that's timely and distinct from anything published in this space yet; directly relevant to "AI changes fast" since prompt-injection-style attacks are a moving target.

****Approach:**** Build/adapt an ethics-gated robot pipeline (can reuse published architectures like RobEthiChor or Wu's own paper as the *_target system_*, without extending it as your contribution); design attack scenarios; measure attack success rate; propose and test defenses (input validation, cross-checking, anomaly detection).

****Two-semester shape:**** 295A = target system + attack taxonomy + initial attacks; 295B = defenses + evaluation + generalization across attack types.

  

### A3. Value Elicitation & Reconciliation for Assistive/Caregiving Robots

****What:**** Instead of one designer hard-coding "ethical," build a system that elicits and reconciles competing values from multiple real stakeholders — e.g., patient wants autonomy, family wants safety, institution wants liability protection.

****Why it fits:**** Shifts the question from "is the gate correct" to "whose values does the gate encode," a genuinely open and under-engineered problem in robot ethics.

****Approach:**** Structured preference-elicitation interface; conflict-resolution/negotiation logic; simulated multi-stakeholder scenarios; evaluate against stakeholder satisfaction / fairness-of-compromise metrics.

****Two-semester shape:**** 295A = elicitation interface + reconciliation logic; 295B = scenario suite, human-subject stakeholder study, refinement.

  

### A4. Accountability & Audit-Trail Design for Multi-Stakeholder Autonomous Fleets

****What:**** For delivery robots/drones in public space, build and evaluate an audit/compliance system against real regulatory frameworks (NIST AI RMF, EU AI Act-style robotics provisions) — can your system actually produce evidence sufficient to answer "who's accountable" after an incident?

****Why it fits:**** More systems/policy-engineering flavored; directly usable output (a compliance framework) beyond a research demo.

****Approach:**** Define an incident taxonomy; build structured logging/evidence pipeline; run simulated incident scenarios; score against a regulatory-completeness checklist.

****Two-semester shape:**** 295A = incident taxonomy + logging pipeline; 295B = simulated incident campaign + compliance evaluation + gap analysis.

  

### A5. Human Trust & Comprehension of Autonomous-System Explanations

****What:**** A human-subjects study: give people a robot's decision logs/justifications and measure whether they can actually predict its behavior, calibrate trust appropriately, or catch a bad decision.

****Why it fits:**** Tests whether "transparency" as usually implemented (structured logs, justification text) actually works on real humans — a claim most robot-ethics papers assert but rarely test empirically, including Wu's own.

****Approach:**** Recruit participants; present decision logs from a working (real or simulated) ethics-gated system; measure prediction accuracy, trust calibration, error-detection rate; compare log formats/designs.

****Two-semester shape:**** 295A = system + log formats + pilot study design; 295B = full human-subjects study + analysis.

  

### A6. Long-Horizon Consistency of Ethical Behavior

****What:**** Does an LLM-governed robot make the same call in materially identical situations across many repeated encounters over time, or does behavior drift/become inconsistent (e.g., across sessions, after context changes, under model updates)?

****Why it fits:**** Sequential/repeated-interaction consistency is barely studied — most ethics benchmarks are single-shot dilemmas, not the "does it behave the same way every Tuesday" question a real deployment faces.

****Approach:**** Build a repeated-scenario test harness; run the same/near-identical scenario many times across sessions, contexts, and model versions; quantify consistency with statistical measures; investigate drift causes.

****Two-semester shape:**** 295A = harness + initial consistency measurement; 295B = drift-cause investigation + stabilization techniques.

  

### A7. Faithfulness of Ethical Justifications

****What:**** A robot logs "why" it made a decision — but is that justification actually causally related to what happened internally, or just a plausible-sounding story generated after the fact?

****Why it fits:**** Directly imports the LLM-interpretability research question of explanation faithfulness into robot ethics — a rigorous, technically deep contribution rather than an application paper.

****Approach:**** Design causal-intervention tests (perturb inputs the justification claims mattered, see if the decision actually changes); compare justification content against ground-truth decision drivers; build a faithfulness metric.

****Two-semester shape:**** 295A = faithfulness-testing methodology + pilot on one system; 295B = apply across multiple architectures/scenarios, propose faithfulness-improving techniques.

  

### A8. Ethics of Robot Data Collection from Bystanders

****What:**** Robots' cameras/sensors capture people who never consented to being observed. Design and evaluate privacy-preserving perception built in from the start (on-device redaction, selective retention, purpose-limited processing) rather than bolted on as a "privacy zone" sign.

****Why it fits:**** Complements Wu's paper's privacy-zone framing (which is about *_where_* the robot may go) with the *_sensing/data_* side of privacy (what it captures and keeps about people it passes) — a genuinely different technical layer.

****Approach:**** Build/adapt a perception pipeline with privacy-preserving techniques (blurring, on-device-only processing, differential retention); evaluate privacy-utility tradeoff (task performance vs. bystander information exposure).

****Two-semester shape:**** 295A = pipeline + baseline privacy-utility measurement; 295B = technique comparison + refined tradeoff analysis.

  

### A9. Equity of Access to Assistive/Service Robots

****What:**** Which populations or neighborhoods actually get access to beneficial robotics deployments (assistive care, delivery, safety monitoring) — a distributional/equity question about deployment, not robot behavior itself.

****Why it fits:**** Keeps a social-justice thread alive (echoing the original BAC idea's spirit) applied to robotics instead, which is squarely Wu's domain.

****Approach:**** Literature/data review of existing service-robot deployment patterns (where documented); simulate or model deployment-allocation policies; propose and evaluate equity-aware allocation strategies.

****Two-semester shape:**** More policy/data-analysis heavy — 295A = landscape study + data model; 295B = allocation-policy simulation + evaluation. (Best fit if the team wants a lighter-engineering, heavier-analysis project.)

  

### A10. Regulatory-Compliance-as-Code

****What:**** Translate standards (IEEE 7001, BS 8611, NIST AI RMF) into automatically checkable runtime constraints/tests, and evaluate how much real coverage that gives you versus what can't be captured mechanically.

****Why it fits:**** A systems-building contribution with immediate practical value — a reusable toolkit rather than a one-off study — and speaks directly to Wu's own standards-alignment framing.

****Approach:**** Parse/encode standards clauses into checkable rules; build a runtime monitor/test-generation tool; apply to an existing ethics-gated system (could even be Wu's own architecture as the *_test subject_*); report coverage and gaps.

****Two-semester shape:**** 295A = rule encoding + monitor for a subset of clauses; 295B = broaden coverage + apply to multiple systems + gap analysis.

  

---

  

## B. Extensions of Wu's Group's Existing Paper

  

*_Paper: Pandit, Singh, Galiya, Wu — "Standards-Aligned Ethical Gating and Decision Telemetry for LLM-Assisted Mobile Robot Navigation" (IEEE BigDataService 2026). Architecture: schema-constrained LLM proposal → Safety & Privacy Gate → conservative Arbiter merge → structured telemetry. Tested Phi-3.5-mini only, 4 scenarios (corridor, pop-in obstacle, privacy boundary, privacy-vs-urgency dilemma), 2,400 Gazebo trials, zero safety violations._*

  

### B1. Cross-Model Generalization

****What:**** They tested exactly one LLM (Phi-3.5-mini). Swap in several current models — a frontier hosted model, newer small on-device models — and test whether their central claim ("safety comes from the governance layers, not the LLM") holds across models, and how model choice affects acceptance rate, reasoning quality, and latency.

****Why it fits:**** Directly answers Wu's own framing to us ("AI changes so rapidly") and is explicitly *_not_* addressed in their paper — the single biggest open gap.

****Approach:**** Reproduce their pipeline (spec is detailed enough to rebuild); swap the LLM Agent module across 3–5 models; rerun the same 4 scenarios; compare acceptance rate, latency, and reasoning-quality metrics against their published numbers.

  

### B2. Broaden the Ablation

****What:**** Their no-LLM-judgment ablation was only 20 runs on Scenarios 1–2. Extend it to full-scale runs across all four scenarios, including the privacy and dilemma ones — this is literally in their own future-work list.

****Why it fits:**** Low-risk, well-scoped, guaranteed-relevant contribution; a good "safe" component to pair with a riskier idea.

****Approach:**** Reuse their ablation surrogate design (or a spectrum of surrogates, see B3); run at full 600-trial scale on S3/S4; compare against published S1/S2 ablation results.

  

### B3. A Graded Ablation Spectrum

****What:**** Instead of one degenerate "always propose GO" surrogate, build a spectrum of surrogate advisors (random, mildly reckless, mildly overcautious, adversarial) to characterize exactly how much LLM quality matters, rather than one binary comparison.

****Why it fits:**** More rigorous than the original ablation; turns "the gate saves you from a terrible LLM" into "here's the full curve of how gate performance depends on advisor quality."

****Approach:**** Define a parameterized surrogate-quality space; run each surrogate through the full pipeline across all 4 scenarios; plot safety/efficiency metrics as a function of advisor quality.

  

### B4. Continuous Control

****What:**** Replace the discrete GO/SLOW/STOP action space with continuous velocity commands — a stated limitation in their paper.

****Why it fits:**** A real engineering lift with a clear technical contribution (redesigning the gate/arbiter math for continuous rather than discrete actions).

****Approach:**** Redefine the Safety & Privacy Gate and Arbiter's conservative-merge rule for continuous velocity; rerun scenarios; compare safety/smoothness metrics against the discrete baseline.

  

### B5. Richer Ethical Scenarios Mapped to Unused Standards Clauses

****What:**** They covered privacy and urgency. IEEE 7001/BS 8611/NIST AI RMF also cover consent, dignity, fairness, and explainability — design new Gazebo scenarios that actually exercise those.

****Why it fits:**** Directly extends their standards-alignment framing, which is their paper's most distinctive feature, into clauses they didn't test.

****Approach:**** Map specific standards clauses to concrete scenario designs (e.g., a consent scenario — robot must obtain and respect a revocable go-ahead; a dignity scenario — robot behavior around a person who can't easily move); implement and evaluate using their existing telemetry framework.

  

### B6. Multi-Robot Extension (bridges both of Wu's interests)

****What:**** Their S4 has a "rear-follower robot" but no real multi-robot negotiation. Extend the governance pipeline so multiple robots, each running their own gate/arbiter, have to reconcile conflicting ethical calls with each other.

****Why it fits:**** The one idea that legitimately spans *_both_* of Wu's stated interests (AI ethics *_and_* long-running multi-robot work) in a single project — worth floating explicitly if the team wants one unified topic instead of choosing between her two suggestions.

****Approach:**** Extend the single-robot architecture to N robots with a negotiation layer (could draw on RobEthiChor-style negotiation protocols) sitting between each robot's local arbiter and a shared resource/space; design multi-robot conflict scenarios; measure agreement rate, safety, and negotiation latency at increasing team sizes.

  

### B7. Human-Trust Evaluation of the Telemetry

****What:**** Their whole pitch is auditability — actually test that claim with human evaluators reading the decision logs, rather than asserting it.

****Why it fits:**** Same idea as A5, but scoped specifically to *_their_* telemetry design — a direct, testable validation (or falsification) of their paper's stated contribution.

****Approach:**** Recruit evaluators; present their telemetry format (final action, provenance, override type, justification) for real logged decisions; measure whether evaluators can correctly identify why a given action was taken or spot an inappropriate override.

  

### B8. Cross-Simulator Validation / Toward Hardware

****What:**** Their own next step: validate in Isaac Sim with domain randomization, then a small physical-robot demo with real sensor noise instead of clean simulated LIDAR.

****Why it fits:**** The most "expected" extension — safest to propose, but also the least novel; good as a secondary/supporting contribution rather than the whole project.

****Approach:**** Port the architecture to Isaac Sim; add domain randomization (lighting, sensor noise, obstacle variety); if hardware is available, run a small subset of scenarios on a physical robot and compare sim-to-real gap.

  

---

  

## Quick Reference: Strongest Candidates for a 2-Semester Project

  

- ****Best standalone pick:**** A2 (adversarial robustness) or A1 (fairness/bias audit) — both have real technical depth and are genuinely unclaimed territory.

- ****Best paper-extension pick:**** B1 (cross-model generalization) — most directly answers what Wu told us, well-scoped, guaranteed relevant.

- ****Best "combine both of her interests" pick:**** B6 (multi-robot extension of her own architecture).