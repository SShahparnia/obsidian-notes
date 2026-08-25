
---
## Course Philosophy

> [!quote] Not a traditional course "Research-first, systems + learning, open frontier."

- **R — Research-first**: read recent papers, reproduce core ideas, identify limitations, design improvements — not just memorize established pipelines.
- **S — Systems + learning**: autonomy is a systems problem — #sensing, #perception, #prediction, #planning, #control, data engines, simulation, safety, deployment all interact.
- **F — Open frontier**: many topics unresolved — end-to-end safety, world-model validation, [[VLA-grounding|VLA grounding]], long-tail robustness, trustworthy physical reasoning.

**Audience:** grad students + practicing engineers who want depth, not a survey-only overview.

**Assignments emphasize research artifacts**: critical reviews, small reproductions, ablations, proposal writing, final projects.

> [!tip] Key idea A good project may be a **negative result** if it is carefully designed, measured, and interpreted.

**Course goal:** learn how to ask research-grade questions about intelligent and autonomous systems.

## Course Framing

- Not a static survey — a **research-oriented map** of fast-moving autonomous systems.
- **Open-ended by design** — students read papers, reproduce systems, critique results, build demos.
- **Graduate depth** — emphasis on architectures, failure modes, data engines, evaluation protocols, deployment tradeoffs (not just textbook algorithms).
- **Industry relevance** — reasoning about latency, safety, data, simulation, real hardware constraints.

## History

### Timeline

|Year|Milestone|
|---|---|
|2018|Course began as **CMPE297 Autonomous Driving**|
|2018|Apollo 3.0 Launch Event — education partnership with SJSU ([video](https://www.youtube.com/watch?v=Q9EOIu5xRfU))|
|2020|Approved as permanent course number **CMPE249**|
|2020|Ford Greenfield Labs collaboration|
|2023|Added to MS AI Program|
|2024–2026|Scope expanded: autonomous driving → general **Intelligent Autonomous Systems**|

**Major collaborators:**

- **Apollo** open-source platform — "Android of the autonomous driving industry"; received permission from the Chinese government to test self-driving tech on roads (2018).
- **Ford Greenfield Labs**
- **SJSU Autonomous System Lab**

## Mental Model — Physical AI

> [!abstract] Core definition Autonomous systems are **Physical AI systems**: they perceive the world, reason under uncertainty, act in real time, and learn from feedback.

**The five-stage loop:**

1. **Perception** — multi-sensor scene understanding
2. **Prediction** — agents, intent, uncertainty
3. **Planning** — goals, constraints, risk
4. **Control** — stable real-time execution
5. **Learning loop** — data, simulation, evaluation

> [!important] Key theme — the bottleneck keeps moving
> 
> - **2015:** perception accuracy & deep learning compute
> - **2020:** multi-sensor fusion, BEV geometry, fleet-scale data
> - **2024:** end-to-end policies, large multimodal models
> - **2025–2026:** world models, physical AI, agentic data engines

### Beyond Cars: The Era of Embodied AI

Shift from hand-coded reactive rulesets → **learned world dynamics**:

- **Perceive** — ingest raw multi-modal streams (camera, LiDAR, kinematics) continuously
- **Predict** — learn physics/rules of reality to anticipate next frame/object state/trajectory
- **Act** — execute decisions from internal simulations / imagined rollouts before touching real hardware
- **Synthesize** — generate rare/counterfactual edge cases to solve the data bottleneck

**Three domains of Physical AI:**

- **Autonomous Vehicles** — dynamic, high-speed, open environments; extreme safety criticality; multi-agent interaction; mapping constraints
- **Humanoid Robotics** — unstructured indoor environments; high DoF; generalized motor skills; delicate interaction
- **Industrial Autonomy** — real-time vision inspection, automated manufacturing; sub-millisecond edge inference; repetitive precision

### Unification of AI Architectures

Boundaries between NLP, computer vision, and robotics control theory are dissolving. **[[Vision-Language-Action models|Vision-Language-Action (VLA)]] models** let a single foundation model ingest a visual scene, understand natural-language instructions, and output low-level tokenized actions — unifying the "brain" that steers a vehicle or commands a robotic arm.

## Big Picture — Why Learn Autonomous Driving

- "Mother of all AI projects" — [Tim Cook / TechCrunch, 2017](https://techcrunch.com/2017/06/13/tim-cook-says-apples-car-project-is-the-mother-of-all-ai-projects/)
- CES has become the world's biggest car show ([PCMag, 2023](https://www.pcmag.com/news/car-tech-at-ces-2023-is-all-about-streaming-gaming-autonomous-driving))
- **Advancing innovation** — AI, computer vision, sensor fusion, ML, robotics
- **Interdisciplinary skills** — engineering + CS + data science
- **Industry demand** — transformation toward AVs needs skilled engineers
- **Research & development** — perception, decision-making, V2V communication

### Companies in the space (from slide roster)

AImotive, Apex.AI, Apollo (Baidu), Apple, Aurora, AutoX, Beep, Black Sesame Technologies, BlueSpace.ai, Bosch, Cruise, Gatik AI, Helm.ai, Imagry, May Mobility, Mercedes-Benz, Mobileye, Motional, NIO, Nissan, Nullmax, Nuro, NVIDIA, Plus.ai, Pony.ai, Qualcomm, Ridecell, SAIF, Telenav, Tesla, Valeo, Vueron, Waymo, WeRide, Woven Planet, XMotors.ai, Zoox

### Silicon Valley clusters

- **NVIDIA, Tesla**
- **Mountain View:** Applied Intuition, Nuro, Waymo
- **Foster City:** Zoox
- **San Jose:** WeRide, AutoX.ai, Azuga, Mark Motors, Rivian, Sibros
- **Palo Alto:** Nauto, Open Motors
- **Cupertino:** Plus.ai
- **Fremont:** Pony.ai
- **Santa Clara:** Seres
- **Sunnyvale:** Baidu

## Industry Momentum

**From roads to robotics:**

- **Next-gen robotaxis** — Tesla Cybercab; Zoox bidirectional public deployment → purpose-built, steering-wheel-free hardware
- **Humanoids in the workforce** — Figure AI (Figure 02 in BMW plants), Unitree (low-cost G1) proving commercial viability
- **Hardware–software synergy** — both constrained by the same bottlenecks: scalable GPU compute, high-quality real-world data collection, robust end-to-end neural network training

## Course Learning Outcomes

1. Comprehensive grasp of foundational concepts/components of autonomous systems
2. Apply theory to real-world scenarios — mapping, localization, perception, path planning, control
3. Competently employ tools/technologies for autonomous systems; adapt to novel situations
4. Communicate effectively (written + verbal); collaborate well in teams

## Grading

|Component|Weight|
|---|---|
|Quiz|5%|
|Midterm|20%|
|Homework & Assignments|15%|
|Final Exam|30%|
|Team Project (1–3 people)|30%|

## Research Workflow

**How the course project works:**

1. **Read** — paper deep dives, technical context
2. **Reproduce** — minimal code experiments, baselines
3. **Diagnose** — ablations, failure cases, metrics
4. **Extend** — new module, dataset, or analysis
5. **Communicate** — research report + presentation

**Outputs:**

- **Output 1:** short technical memos, paper critiques, experiment logs, model cards, reproducibility reports
- **Output 2:** research question w/ baseline, method, experiments, negative results, clear limitations
- **Output 3:** conference-style final report + technical presentation (not just a demo)

## Project Tracks

> [!warning] Blue Ocean vs. Red Ocean Avoid highly saturated ("red ocean") topics requiring massive compute just to compete. No outdated/"tutorial" topics — check latest SOTA (with code), use AI for novelty-checking. Novel, well-executed projects can become papers at CVPR/NeurIPS/AAAI/ICLR/ICRA/IROS.

|Track|Focus|
|---|---|
|**Algorithm**|Compare/fine-tune/extend models on KITTI, nuScenes, Waymo, Argoverse, BDD100K, or simulated data|
|**System**|Integrate autonomy components with ROS 2, Isaac Sim, Jetson, sensors, real-time inference|
|**Research**|Investigate a frontier question: VLM/VLA, world models, auto-labeling, simulation, safety, agentic workflows|
|**Deployment**|Optimize for latency, memory, quantization, batching, edge compute, multi-sensor sync|

**Deliverables:** proposal, codebase, experiment logs, final report, presentation, demo video

## Project Examples

- **BEV perception** — evaluate BEVFusion / BEVFormer variants, diagnose cross-dataset transfer
- **Occupancy** — compare 3D occupancy prediction under weather, range, sensor sparsity
- **VLM for driving** — use VLMs to explain scenes, verify labels, generate driving rationales
- **VLA robotics** — fine-tune OpenVLA on a small manipulation task or simulated robot
- **World models** — generative simulation to create edge cases, evaluate policy robustness
- **Edge deployment** — deploy detection/VLA components on Jetson/ROS 2, measure real-time constraints

### Suggested research lanes

1. **BEV / fusion** — cross-attention, occupancy, LiDAR-camera fusion, radar fusion, cross-dataset robustness
2. **End-to-end driving** — planning heads, vectorized scene representation, diffusion planning, behavior metrics
3. **World models** — scenario generation, counterfactuals, synthetic data validation, closed-loop evaluation
4. **VLA / robotics** — OpenVLA fine-tuning, robot data, action tokenization, sim-to-real transfer
5. **Agentic autonomy** — tool-using agents for data mining, labeling, simulation, debugging, evaluation
6. **Safety and evaluation** — long-tail metrics, uncertainty, OOD detection, monitors, regression testing, verification

## How to Read a Research Paper

> [!question] Don't just ask "did the numbers improve" — ask what evidence supports the claim
> 
> - **Claim** — what is the one-sentence thesis?
> - **Baseline** — is it strong, recent, matched-budget?
> - **Data** — what distribution, labels, leakage risks exist?
> - **Metric** — does it reflect deployment behavior?
> - **Ablation** — which component actually caused the gain?
> - **Failure** — where does it break, and what does that teach us?

**Mantra:** A good research project makes a careful claim and closes obvious reviewer objections.

## Class Culture

> [!success] What counts as success Clear problem definition, reproducible experiment, meaningful baseline, honest limitations, strong presentation.

> [!failure] What does NOT count Copying tutorials, reporting only screenshots, using closed APIs as the main method, hiding negative results.

**Professional standard:** write as if your work will be read by a reviewer, teammate, or engineering lead.

## Proposal Requirements

First assignment — choose a frontier question. Submit on Canvas by deadline (AI assistance allowed). Four core deliverables:

1. **GitHub repo link** — initial `README.md` with project title, team members, abstract, selected track
2. **Literature & SOTA survey** (GitHub) — summarize 5–10 recent papers/models from the last 1–3 years relevant to the topic
3. **Project proposal document** (Canvas) — problem formulation (domain problem, input/output specs, target metrics/success criteria) + proposed technical approach (architecture, models, data sources, intended modifications)
4. **AI novelty & feasibility audit** (GitHub) — paste AI's evaluation of novelty, "red ocean" risk, oversaturated-area check

---

