---

---
---
## Research / Algorithm Track — Perception & Planning

### 1. World-model-generated edge cases for perception stress-testing

Use an open/accessible world model (e.g., reproduce ideas from **Waymo's World Model**, built on Genie-3-style generative video and launched Feb 2026, or **Wayve GAIA-3**) to synthesize rare/counterfactual driving scenes, then measure how much a BEV or occupancy model's accuracy degrades on the synthetic long-tail vs. standard splits.

### 2. Occupancy prediction under sensor sparsity and weather

Cross-dataset evaluation (nuScenes ↔ Waymo Open ↔ Argoverse 2) of a 3D occupancy network under simulated LiDAR dropout, reduced camera FOV, and adverse weather — a robustness/ablation report rather than a new SOTA chase.

### 3. VLM-generated driving rationale — faithfulness audit

Test whether a VLM's natural-language explanation of a planning decision is _faithful_ to the planner's actual internal signals, or a plausible-sounding confabulation — targets the "trustworthy physical reasoning" open frontier from Lecture 1.

### 4. Radar-heavy or radar-camera-only perception in adverse weather

2026 has seen a wave of new sensor hardware — **Seyond's solid-state LiDAR series** (CES 2026) and **RoboSense's RS-Fusion-P6** solid-state LiDAR perception stack for L4 driving — but radar remains the most weather-robust modality. Build/evaluate a 4D-radar-only or radar-camera fusion 3D detector and compare against LiDAR-based baselines specifically in fog/rain scenes.

## Research / System Track — VLA & Robot Manipulation

### 5. Edge VLA fine-tuning and latency/power profiling on Jetson Thor

Fine-tune a small open VLA — **SmolVLA** or **OpenVLA** — deploy on NVIDIA's new **Jetson Thor** edge boards, and report an accuracy-vs-latency-vs-power Pareto curve with quantization ablations.

### 6. Low-cost humanoid teleop data collection + VLA generalization study

Collect a small teleoperated demo dataset using **NVIDIA Isaac GR00T**'s newly opened academic reference humanoid platform, fine-tune SmolVLA/OpenVLA, and measure generalization to held-out poses/lighting.

### 7. "Video generators as robot policies" reproduction

Recent work (Columbia's _Video Generators are Robot Policies_, and Figure AI's **Project Go-Big** on internet-scale humanoid pretraining with direct human-to-robot transfer) argues that video-generation models can act as implicit policies. Reproduce a small-scale version and measure how much internet-video pretraining improves few-shot manipulation on one real/sim task.

### 8. Latent action pretraining from unlabeled video (LAPA-style)

Pretrain a latent-action model from unlabeled human demonstration video (à la **LAPA**), then fine-tune with a small labeled action dataset; compare data-efficiency against training a VLA purely from action-labeled data.

### 9. Sim-to-real transfer benchmark for industrial inspection

Train a vision-inspection policy in Isaac Sim, deploy to a real or edge-simulated rig, and measure the sim-to-real accuracy gap plus real-time inference constraints — fits the lecture's "Industrial Autonomy" (sub-millisecond edge inference) framing.

## Legged & Aerial Robotics

### 10. Torque-driven RL for quadruped locomotion — reproduction + ablation

Reproduce the torque-driven (vs. position-control) RL locomotion approach from **arXiv:2607.18365** (July 2026) in Isaac Sim or MuJoCo, ablate reward terms, and evaluate terrain generalization vs. a position-control baseline.

### 11. Legged robot robustness to actuator degradation

Inject simulated actuator wear/failure into a legged locomotion policy's training and evaluate robustness vs. a nominal policy — a safety-flavored extension of current quadruped RL literature.

### 12. Vision-only drone navigation in GPS-denied, cluttered environments

Benchmark a lightweight learned policy for obstacle avoidance and navigation without GPS against classic SLAM-based baselines — an active area per _Drones_ journal's August 2026 special issue on navigation and mission planning.

### 13. Event-camera-based high-speed perception for drones or ground robots

Neuromorphic/event cameras (Prophesee, Sony, iniVation) promise microsecond-latency, near-darkness sensing at a fraction of the data of RGB. Build a small event-camera obstacle-detection pipeline and compare latency/robustness against a standard RGB pipeline for fast maneuvering — 2026 has seen a fresh wave of event-vision-for-robotics reviews (IEEE, late 2025–2026) making this a timely, under-explored track in the AV/robotics curriculum.

## Safety, Security & Agentic Autonomy

### 14. LLM-driven safety-assertion generation for automotive ADAS

Reproduce/extend **SafeGen** (arXiv:2606.25296, June 2026): use an LLM to auto-generate functional-safety assertions and evaluate fault-criticality on an open ADAS codebase or simulated ECU.

### 15. Multi-agent LLM framework for automotive cybersecurity

Inspired by **CyberLLM** (arXiv:2608.06651, Aug 2026): build a small multi-agent LLM system that detects and responds to simulated attacks on a vehicle's CAN-bus/V2X interface in a testbed.

### 16. Runtime verification / temporal-logic monitors for autonomy stacks

Implement a lightweight runtime-enforcement layer that checks an autonomy stack's actions against temporal-logic safety specs at runtime, and measure the safety/utility tradeoff it introduces — connects to 2026 work on runtime verification for LLM/agent safety and to Lecture 1's "monitors, regression testing, verification" safety lane.

### 17. Agentic auto-labeling / data-mining pipeline

Build a tool-using LLM-agent pipeline (in the spirit of the AIDE data engine) that mines an unlabeled video set, proposes rare-event labels via a VLM, and self-critiques low-confidence labels before human review.

## Swarm & Multi-Robot Systems

### 18. Foundation-model-guided robot swarm for disaster response

Coordinate a small simulated swarm via a shared foundation-model "supervisor" for a search-and-rescue-style coverage task, and compare against classical swarm algorithms (flocking, ORCA) on coverage time and collision rate — 2026 has an active line of work on foundation models for robot swarms (_Science Robotics_) and swarm-based disaster response.

### 19. Multi-agent negotiation in simulated intersections

Simulate multiple LLM- or RL-driven agents negotiating right-of-way at an unsignaled intersection (CARLA/SUMO or a lightweight custom sim) and evaluate safety/efficiency vs. a rule-based baseline.

## Field, Marine & Logistics Autonomy

### 20. Autonomous crop-monitoring perception-to-action pipeline

Build a small field-robot navigation + weed/pest-detection pipeline that triggers a downstream action, evaluated on a public ag-vision dataset — frame it against the task types used in the 2026 Farm Robotics Challenge.

### 21. AI-aided AUV navigation under sensor drift

Reproduce ideas from _AI-Aided Advancements in Autonomous Underwater Vehicle Navigation_ (arXiv:2605.04672, May 2026): evaluate a learned navigation/localization correction module against dead-reckoning drift in simulated underwater conditions.

### 22. Multi-robot warehouse fleet coordination under uncertainty

Simulate a fleet of warehouse robots with a learned coordination policy vs. classical task scheduling, measuring throughput/collision tradeoffs as order volume and congestion scale — tracks the 2026 wave of AI-driven warehouse-robotics deployments.

### 23. Long-haul autonomous trucking edge-case benchmark

Build/evaluate a scenario dataset of highway edge cases (construction zones, merges, adverse weather) inspired by **Torc Robotics'** 2026 push toward autonomous-trucking commercialization, and benchmark a planner's behavior against them.

## High-Speed Autonomous Racing

### 24. High-speed racing planner benchmark at the limits of handling

Using public **Indy Autonomous Challenge** methods/software or a racing simulator (F1TENTH-style), benchmark a learned racing policy against a classical MPC controller at the edge of the vehicle's handling envelope — ties to the "racetrack to highway" high-speed-autonomy theme (Forbes, Feb 2026) and IAC's 2026 season at Laguna Seca.

---

## How to pick

> [!tip] Novelty check (per Lecture 1 proposal requirement) For whichever idea you shortlist: (1) pull 5–10 papers/models from the last 1–3 years, (2) run an AI novelty/feasibility audit and paste the critique into your proposal repo, (3) make sure the compute budget is realistic for a semester — prefer fine-tuning/evaluation over training from scratch.

> [!note] Least/most hardware-dependent Purely simulation/dataset-based ideas (#1–4, #10–11, #16, #19, #22–24) need no physical robot. Ideas involving real deployment (#5–6, #9, #12–13, #17, #20) need at least a Jetson-class board, a small robot/drone, or a camera rig — check lab access before committing.

## Sources consulted (Aug 2026)

- [Best VLA Models 2026 guide](https://www.roboticscenter.ai/vla-models/best-2026)
- [SmolVLA — Hugging Face](https://huggingface.co/blog/smolvla)
- [OpenVLA GitHub](https://github.com/openvla/openvla)
- [Waymo World Model announcement](https://waymo.com/blog/2026/02/the-waymo-world-model-a-new-frontier-for-autonomous-driving-simulation/)
- [Waymo World Model built on Genie 3 — MarkTechPost](https://www.marktechpost.com/2026/02/06/waymo-introduces-the-waymo-world-model-a-new-frontier-simulator-model-for-autonomous-driving-and-built-on-top-of-genie-3/)
- [Wayve GAIA-3 launch](https://wayve.ai/press/wayve-launches-gaia3/)
- [NVIDIA Jetson Thor announcement — NVIDIA Blog](https://blogs.nvidia.com/blog/jetson-thor-robotics-edge-ai-agent/)
- [NVIDIA Isaac GR00T academic reference humanoid](https://nvidianews.nvidia.com/news/nvidia-open-humanoid-robot-reference-design)
- [NVIDIA Alpamayo 1 for AVs — CES 2026](https://interestingengineering.com/ai-robotics/nvidia-autonomous-ai-ces-2026)
- [AIDE: Automatic Data Engine for Object Detection](https://www.labellerr.com/blog/revolutionizing-autonomous-driving-a-deep-dive-into-aide/)
- [3D Occupancy Perception survey (GitHub)](https://github.com/HuaiyuanXu/3D-Occupancy-Perception)
- [Humanoid robots in 2026 — what's actually deployed](https://www.technology.org/2026/07/18/humanoid-robots-in-2026-what-is-actually-deployed/)
- [Seyond debuts solid-state LiDAR series — CES 2026](https://www.automotiveworld.com/news/seyond-debuts-solid-state-lidar-series-at-ces-2026/)
- [RoboSense RS-Fusion-P6 solid-state lidar for L4](https://autotechinsight.spglobal.com/news/5269779/robosense-launches-rs-fusion-p6-solid-state-lidar-perception-solution-for-level-4-autonomous-driving)
- [Torc Robotics — autonomous trucking commercialization, May 2026](https://roboticsandautomationnews.com/2026/05/08/inside-torc-robotics-how-autonomous-trucking-is-moving-toward-commercial-reality/101319/)
- [Towards Torque-Driven RL for Quadruped Locomotion — arXiv:2607.18365](https://arxiv.org/html/2607.18365v1)
- [SafeGen: LLM-Driven Assertion Generation — arXiv:2606.25296](https://arxiv.org/abs/2606.25296)
- [CyberLLM: Multi-Agent LLM Framework for Automotive Cybersecurity — arXiv:2608.06651](https://arxiv.org/abs/2608.06651)
- [Safety Testing LLM Agents at Scale — arXiv:2607.01793](https://arxiv.org/abs/2607.01793)
- [Runtime Verification and Temporal Logic for AI Agent Safety](https://zylos.ai/research/2026-03-15-runtime-verification-temporal-logic-ai-agent-safety/)
- [AI-Aided Advancements in AUV Navigation — arXiv:2605.04672](https://arxiv.org/abs/2605.04672)
- [World Model for Robot Learning: A Comprehensive Survey — arXiv:2605.00080](https://arxiv.org/html/2605.00080v1)
- [MIT News — Human-machine teaming dives underwater, Apr 2026](https://news.mit.edu/2026/human-machine-teaming-dives-underwater-0414)
- [DARPA "Deep Thoughts" AUV solicitation, Apr 2026](https://defensescoop.com/2026/04/24/darpa-autonomous-underwater-vehicle-auv-program-deep-thoughts/)
- [Figure AI — Project Go-Big: Internet-Scale Humanoid Pretraining](https://www.figure.ai/news/project-go-big)
- [Video Generators are Robot Policies — Columbia University](https://videopolicy.cs.columbia.edu/assets/video_policy.pdf)
- [LAPA: Latent Action Pretraining](https://latentactionpretraining.github.io/)
- [Drones journal — Aug 2026 issue, navigation/mission-planning special issue](https://www.mdpi.com/2504-446X/10/8)
- [Event Cameras in 2026 — Prophesee, Sony, iniVation](https://internet-pros.com/blog/event-cameras-neuromorphic-vision-sensors-2026/)
- [Applications of Neuromorphic/Event Camera in Robotics — IEEE survey](https://ieeexplore.ieee.org/document/11275912/)
- [Foundation models will revolutionize robot swarms — Science Robotics](https://www.science.org/doi/10.1126/scirobotics.adz1543)
- [Swarm Robotics 2026: Coordinated AI for Disaster Response](https://robocloud-dashboard.vercel.app/learn/blog/swarm-robotics-2026)
- [Farm Robotics Challenge — 2026 participants](https://www.farmroboticschallenge.ai/2026participants)
- [Autonomous Farming Robots: 7 Trends for 2026](https://farmonaut.com/precision-farming/autonomous-farming-robots-7-game-changing-trends-for-2026)
- [AI Warehouse Robots Reshaping Logistics in 2026](https://www.traxtech.com/ai-in-supply-chain/ai-warehouse-robots-transforming-logistics-2026?hs_amp=true)
- [Indy Autonomous Challenge — Laguna Seca 2026](https://www.indyautonomouschallenge.com/laguna-seca-2026)
- [High Speed Autonomy — From Racetrack to Highway, Forbes, Feb 2026](https://www.forbes.com/sites/sabbirrangwala/2026/02/17/high-speed-autonomyfrom-racetrack-to-highway/)