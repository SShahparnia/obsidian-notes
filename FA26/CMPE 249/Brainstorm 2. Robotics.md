

> [!info] Scope Narrower lens than the [[CMPE249_Project_Ideas_Brainstorm|general brainstorm]]: core robotics — SLAM, motion planning, manipulation, mobile-robot navigation, legged locomotion — rather than the broader "Physical AI" sweep (drones, exosuits, agriculture, marine, etc.). Organized by project _type_, matching how the lecture frames the four tracks: **Research** (open question, paper reproduction/extension), **Development** (systems/integration engineering), and **Robotics** (hands-on, real hardware). Pick one lane, or a Research idea paired with its Robotics counterpart for a two-phase (sim → real) project.

## Related

- [[CMPE249_Lecture1_Introduction]]
- [[CMPE249_Project_Ideas_Brainstorm]]

---

## Research

_Open questions. Reproduce a recent paper, run a matched-budget comparison, or evaluate where an approach breaks — output is a claim + evidence, not just a demo._

### R1. SLAM robustness in dynamic, crowded scenes

Dynamic-environment SLAM is still an open problem — recent work like **RGD-SLAM** (Gaussian-splatting SLAM for dynamic environments, ScienceDirect 2026) and **VAR-SLAM** attacks it with different tricks (semantic filtering, adaptive weighting). Reproduce one baseline (e.g., ORB-SLAM3 + a dynamic-object filter) and a newer variant, then benchmark both on a scene with heavy pedestrian/object motion — report where trajectory drift actually comes from, not just an aggregate ATE number.

### R2. Learned vs. classical motion planning, matched budget

Compare a learned planner (diffusion-based or RL) against classical planners (RRT*, CHOMP, STOMP) on cluttered manipulation or navigation tasks under the _same_ compute/data budget, and report which wins on which metric (success rate, planning time, path smoothness) — directly applies Lecture 1's "is the baseline matched-budget?" reading heuristic.

### R3. Zero-shot grasp detection with vision-language foundation models

A 2025–2026 wave of work (**VLAD-Grasp**, **ORACLE-Grasp**) uses vision-language/multimodal models to predict grasp poses on novel objects with no task-specific training. Reproduce one of these and benchmark it against a dedicated grasp network (e.g., GraspNet/AnyGrasp) on objects neither has seen — characterize the failure modes each makes that the other doesn't.

### R4. Does offline pretraining reduce online samples needed for a new manipulation task?

A live research question in robot RL: how much does offline pretraining on existing manipulation datasets actually reduce the online interaction budget needed to learn a _new_ task? Design a controlled experiment — same architecture, with vs. without offline pretraining — and report a sample-efficiency curve rather than a single final number.

### R5. Collaborative multi-robot SLAM under communication constraints

Investigate collaborative mapping across two or more low-cost robots: how does map consistency degrade as inter-robot communication bandwidth or reliability drops? A clean, scoped research question that only needs simulation (Gazebo/Isaac Sim) plus, optionally, two cheap real robots to validate.

## Development

_Systems/integration engineering — build a working pipeline out of existing components, deploy it, and measure it honestly (latency, drift, success rate) rather than just showing it run once._

### D1. Full ROS 2 Nav2 stack on a real mobile robot

Integrate the **Nav2** navigation stack (localization, costmaps, planners, recovery behaviors) end-to-end on a real low-cost robot (TurtleBot3/4-class), tune it against your specific sensor suite, and benchmark it (success rate, time-to-goal, recovery frequency) against a published Nav2 baseline in both static and dynamic-obstacle settings.

### D2. Perception-to-grasp pipeline with MoveIt 2

Build the full pipeline — camera → object detection/segmentation → grasp-pose estimation → **MoveIt 2** motion planning → execution — on a real or simulated robot arm, and report end-to-end success rate and per-stage latency breakdown (where does the pipeline actually lose time or accuracy?).

### D3. Edge-optimized real-time obstacle avoidance

Take a working perception model and deploy it on a Jetson-powered mobile robot, applying TensorRT/quantization optimization, and report the accuracy-vs-latency-vs-power Pareto curve — a deployment-track project that produces a genuinely reusable engineering artifact.

### D4. Digital-twin / hardware-in-the-loop validation pipeline

Wire up a digital twin (Isaac Sim or Gazebo) so control code can be tested against a simulated version of your real robot before it ever touches hardware, then quantify the sim-to-real gap: how well does "passes in sim" predict "works on the real robot"?

### D5. Multi-sensor fusion localization engineering

Build a camera + IMU + wheel-odometry fusion pipeline (EKF/UKF, or a small learned fusion network) on a real robot and evaluate localization drift over long runs (tens of minutes) compared to any single sensor alone.

## Robotics

_Hands-on, real (or budget-real) hardware. These need a physical robot but not an expensive one — several current platforms make this genuinely affordable for a student project._

### H1. LeRobot SO-101 teleop → imitation learning → real deployment

Hugging Face's **SO-101** is a fully open-source, 3D-printable 6-axis arm running well under $200 in parts, built specifically for the imitation-learning workflow: teleoperate it with a leader-follower pair to collect demonstrations, fine-tune a small policy (ACT or SmolVLA) on that data, and evaluate success rate on a real pick-and-place task with the physical arm. Probably the most accessible real-hardware manipulation project available right now.

### H2. TurtleBot3-class autonomous exploration and mapping

Program a small differential-drive robot to autonomously explore and build a map of an unknown indoor space (frontier exploration or a learned exploration policy), and evaluate coverage-over-time against a baseline exploration strategy.

### H3. Budget open-source quadruped, terrain-adaptive walking

Low-cost open-source quadruped kits (e.g., MangDang's Mini Pupper, Petoi's OpenCat/Bittle line) put real legged-robot hardware within a course-project budget. Deploy a trained RL locomotion policy on the physical robot and test generalization to terrain it wasn't trained on, compared against the kit's default scripted gait.

### H4. Small multi-robot swarm, real communication constraints

Build and program a handful of inexpensive differential-drive robots to execute a coordinated task (coverage, formation-keeping, or simple search) — and unlike the sim-only swarm ideas in the general brainstorm, this version has to deal with real Wi-Fi/Bluetooth latency and packet loss between robots, which is often where swarm coordination actually breaks.

### H5. Real-arm dexterous pick-and-sort system

Combine grasp detection (pair with Research idea R3) with a real LeRobot/SO-101 arm to sort a mixed bin of objects by category — a full-system integration project that stresses perception, planning, and execution together rather than any one piece in isolation.

---

## How to pick

> [!tip] A natural two-phase project Several Research ideas pair cleanly with a Robotics one: prototype/validate in sim first (R2, R3, R5), then move the winning approach onto real hardware (H1, H4, H5) for the second half of the semester. That structure also maps directly onto the lecture's "Reproduce → Diagnose → Extend" research workflow.

> [!note] Budget reality check H1/H5 (SO-101 arm) and H3 (budget quadruped kit) are realistic on a personal or small-team budget (roughly $100–$400 in hardware). H2/H4 need access to a lab's TurtleBot-class robots or a small fleet of cheap differential-drive bases — check what SJSU's Autonomous System Lab already has before buying anything.

## Sources consulted (Aug 2026)

- [RGD-SLAM: Robust Gaussian splatting SLAM for dynamic environments](https://www.sciencedirect.com/science/article/abs/pii/S0031320326000348)
- [VAR-SLAM: Visual Adaptive and Robust SLAM for Dynamic Environments](https://arxiv.org/html/2510.16205v1)
- [VLAD-Grasp: Zero-shot Grasp Detection via Vision-Language Models](https://arxiv.org/abs/2511.05791)
- [ORACLE-Grasp: Zero-Shot Affordance-Aligned Robotic Grasping using Large Multimodal Models](https://link.springer.com/article/10.1007/s11370-026-00707-4)
- [Robot Grasping Simulation in 2026 — overview](https://medium.com/@creed_1732/robot-grasping-simulation-in-2026-the-last-hard-problem-in-manipulation-is-finally-cracking-d0d6a417e181)
- [Efficient Model-Based RL for Robot Control via Online Learning](https://arxiv.org/html/2510.18518v1)
- [Making Offline Model-Based RL Work on Real Robots](https://openreview.net/forum?id=rbNOhbdQ0v)
- [Hugging Face LeRobot — GitHub](https://github.com/huggingface/lerobot)
- [Hugging Face launches the SO-101 — Hackster.io](https://www.hackster.io/news/hugging-face-launches-the-so-101-an-upgraded-low-cost-3d-printable-autonomous-robot-arm-532360f441eb)
- [MangDang QuadrupedRobot — open-source ROS robot dog kit](https://github.com/mangdangroboticsclub/QuadrupedRobot)
- [PetoiCamp OpenCat-Quadruped-Robot](https://github.com/PetoiCamp/OpenCat-Quadruped-Robot)
- [ROS2-Powered Autonomous Navigation for TurtleBot3: Integrating Nav2 Stack — IEEE](https://ieeexplore.ieee.org/document/10779642/)
- [Autonomous navigation of ROS2-based TurtleBot3 in static/dynamic environments](https://link.springer.com/article/10.1007/s41870-025-02500-5)