# Paper selection and sources

## Accepted additions: 2026-11-06

The maintainer accepted ICL-1, RSI-1, and CWM-1 from the November 5 review batch.

| Direction | First submission | Latest version reviewed | Paper | Primary evidence and official resources |
| :--- | :--- | :--- | :--- | :--- |
| ICL | 2026-10-20 | v2, 2026-11-03 | [D-Skill: Distilling Teacher Knowledge through Agent Skills](https://arxiv.org/abs/2610.28914) | [Method and experiments](https://arxiv.org/html/2610.28914v2) · [Code](https://github.com/shuo-yuan/D-Skill) |
| RSI | 2026-11-02 | v1, 2026-11-02 | [Physical Experience Builds Continual Spatial World Models](https://arxiv.org/abs/2611.04016) | [Method and experiments](https://arxiv.org/html/2611.04016v1) |
| CWM | 2026-11-03 | v1, 2026-11-03 | [PyRUA-DataFarm: LLM Agent as a Cost-Efficient Teleoperator for Real-Ready Robot Data](https://arxiv.org/abs/2611.05320) | [Method and experiments](https://arxiv.org/html/2611.05320v1) · [Code](https://github.com/DAGroup-PKU/PyRUA-Lean/tree/DataFarm) |

- **D-Skill** constructs textual skills offline from paired traces and deploys them as context with fixed model weights. ALFWorld evaluation uses 134 text-environment test games. Its October 20 first submission makes it a supplemental candidate, with the November 3 revision reviewed.
- **Spatial Change Memory** updates reusable spatial relations and parameters within a known dynamics family. Evidence comes from physics-grounded simulation, with hardware maze validation proposed as future work.
- **PyRUA-DataFarm** separates executable simulation dynamics from video appearance generation. Policies trained on generated data are evaluated on one dual-arm platform across five tasks. Unobserved physical parameters are assumed and randomized.

## Expanded scope and accepted additions: 2026-11-03

The maintainer expanded the ICL section to **ICL & Embodied Agentic RL** and explicitly
requested these four papers. This includes multi-turn reinforcement learning for robot
planners and code policies, SFT + RL post-training, and closely related harness/distillation
methods. ICL still means contextual adaptation with fixed policy weights; training-time
RL is distinct from deployment-time TTT. Existing entries are retained.

| First submission | Latest version reviewed | Paper | Primary evidence and official resources |
| :--- | :--- | :--- | :--- |
| 2026-10-30 | v1, 2026-10-30 | [TinyAstral: Transferring Self-Evolving Harnesses to Tiny Generalist Manipulation Agents](https://arxiv.org/abs/2610.41216) | [Method and experiments](https://arxiv.org/html/2610.41216v1) · [Project](https://garfield-kh.github.io/TinyAstral/) · [Code](https://github.com/Garfield-kh/TinyAstral) |
| 2026-10-29 | v1, 2026-10-29 | [CaPtain: A Pipeline for Post-Training Code-as-Policy Robot Agents](https://arxiv.org/abs/2610.40799) | [Method and experiments](https://arxiv.org/html/2610.40799v1) · [Project](https://waltstephen.github.io/captain/) · [Code](https://github.com/waltstephen/CaPtain) |
| 2026-10-26 | v2, 2026-10-27 | [Pretraining Knows What, Simulation Teaches How: Compositional Generalization in a Sim-Trained Robot Agent](https://arxiv.org/abs/2610.35817) | [Method and experiments](https://arxiv.org/html/2610.35817v2) · [Project](https://zero-real.github.io/) |
| 2026-10-20 | v2, 2026-10-21 | [AgenticRoboRL: Bringing Coding-Agent Post-Training to Agentic Robotics](https://arxiv.org/abs/2610.28589) | [Method and experiments](https://arxiv.org/html/2610.28589v2) · [Project](https://l-codingspace.github.io/AgenticRoboRL/) · [Code](https://github.com/L-CodingSpace/AgenticRoboRL) |

- **TinyAstral** is included as a supporting harness-evolution and distillation method,
  with an RSI cross-tag. Only the harness changes during evolution; student weights
  change during subsequent distillation. Its main closed-loop evaluations are simulated;
  auxiliary real-robot training data does not establish hardware deployment performance.
- **CaPtain** trains a code-writing VLM with SFT and multi-turn RL. The physical critic
  reads privileged simulator state only during training. Hardware transfer follows
  simulation-only adaptation; it is not presented as test-time parameter learning.
- **ZAP** trains a 27B VLM using self-mined successful simulation traces and GRPO.
  Evaluation includes real bimanual manipulation and transfer to a single-arm Franka.
  The no-real-robot-data claim applies to robot training data, not general VLM pretraining.
  The project links a paper repository; no policy-training code release is asserted here.
- **AgenticRoboRL** updates planner weights with SFT and multi-turn RL while retaining
  fixed execution components. Evidence is from simulation, including LIBERO-PRO/Plus
  and RPent/CaP-X; no physical-robot validation is claimed.

## Accepted additions: 2026-10-29

Two papers from the 2026-10-29 review batch were explicitly accepted by the maintainer:
RSI-1 (Rollback) and CWM-1 (Real2Gym). Dates and descriptions were checked against
the original arXiv abstracts and full papers; official project and code links were
checked on 2026-10-29. Existing entries are retained.

| Direction | First submission | Latest version reviewed | Paper | Primary evidence and official resources |
| :--- | :--- | :--- | :--- | :--- |
| RSI | 2026-10-26 | v1, 2026-10-26 | [Rollback: Experience Backtracking in World Models for Policy Improvement](https://arxiv.org/abs/2610.36068) | [Method and experiments](https://arxiv.org/html/2610.36068v1) · [Project](https://rollback-wm.github.io/) |
| Code World Model | 2026-09-29 | v1, 2026-09-29 | [Real2Gym: Building Gyms from Videos, Bringing Skills to Robots](https://arxiv.org/abs/2609.37089) | [Method and experiments](https://arxiv.org/html/2609.37089v1) · [Project](https://real2gym.github.io/) · [Real2Sim code](https://github.com/real2gym/Real2Gym) · [Agent code](https://github.com/real2gym/R2G_Agent) |

- **Rollback:** Counterfactual world-model rollouts provide action-level supervision
  for policy improvement; real trajectories update the video world model through
  LoRA fine-tuning and distribution matching distillation. The paper evaluates block
  extraction, ball tossing, and tabletop curling on real robots. Its RSI relevance is
  continual policy/world-model co-improvement; it does not demonstrate recursive
  modification of the improvement algorithm. The reported improvement setup uses
  48 H200 GPUs. No official code link was found on the project page at review time.
- **Real2Gym:** Video-derived Blender/MuJoCo worlds support executable physical
  interactions and action-feasibility checks, beyond static scene reconstruction.
  Evidence includes DROID/EgoDex reconstruction, simulated manipulation, and four
  tasks on a real Franka robot. The agent's underlying model weights remain frozen.
  The released R2G_Agent covers the C0 continuous stage-code execution path; its
  README states that it neither loads prior-task procedures nor builds a persistent
  experience library. The broader experience accumulation described in the paper
  should therefore be distinguished from the released implementation. Real2Gym was
  a 30-day-window supplement in this batch, not a newly submitted October paper.

## Initial selection: 2026-10-20

Reviewed on **2026-10-20** (Asia/Shanghai).

This update adds **20 distinct papers: five each for ICL, RSI, TTT, and Code World Model**.
The previous nine papers and four blogs are retained. Selection favors recent, relevant
work found in the collections below; it is a curated batch, not an exhaustive ranking
of the newest papers in each field.

Collection lists were used to discover candidates. Each selected arXiv abstract page
was read to check its current title, first-submission date, method, and evaluation setting.
Descriptions in the README were written from those primary sources. Project links were
included when linked by the paper; a project or repository link does not imply a complete
code release. Results are author-reported, and no experiments were independently reproduced.

## Collection snapshots

Dates below are the latest default-branch commit timestamps converted to Asia/Shanghai.
Snapshot links preserve the source list even when a rolling digest changes.

| Collection | Latest commit date | Snapshot |
| :--- | :--- | :--- |
| [asimfish/awesome_ICL](https://github.com/asimfish/awesome_ICL) | 2026-09-08 | [README at d36bc15](https://github.com/asimfish/awesome_ICL/blob/d36bc1548c876dec701dab5f26a64d8db26472a0/README.md) |
| [asimfish/awesome_robo_ttt](https://github.com/asimfish/awesome_robo_ttt) | 2026-09-09 | [README at 92eec01](https://github.com/asimfish/awesome_robo_ttt/blob/92eec01bfa9e48f1cd2eca190c380eb190c947cb/README.md) |
| [BraveBoBo/awesome-in-context-learning--in-robot](https://github.com/BraveBoBo/awesome-in-context-learning--in-robot) | 2026-10-20 | [README at 70ef1ec](https://github.com/BraveBoBo/awesome-in-context-learning--in-robot/blob/70ef1ec8dc7de29f83abb1da490d56d6f4672b4a/README.md) |
| [cocacola-lab/awesome-embodied-rsi](https://github.com/cocacola-lab/awesome-embodied-rsi) | 2026-10-14 | [README at 36f6eeb](https://github.com/cocacola-lab/awesome-embodied-rsi/blob/36f6eeb3b30e6f7374719e91268758f1b39105f6/README.md) |
| [Oliverbansk/Awesome-Test-Time-Robot-Learning](https://github.com/Oliverbansk/Awesome-Test-Time-Robot-Learning) | 2026-09-30 | [README at 25f47b1](https://github.com/Oliverbansk/Awesome-Test-Time-Robot-Learning/blob/25f47b1ca3b3ef45dea0f4a3d189bc836e64a58a/README.md) |
| [pinkbubblebubble/awesome-rsi](https://github.com/pinkbubblebubble/awesome-rsi) | 2026-10-19 | [README at 2d2c7f6](https://github.com/pinkbubblebubble/awesome-rsi/blob/2d2c7f6778b528f1ddc75865d52b83968030fa38/README.md) |
| [yifliu3/awesome-code-world-models](https://github.com/yifliu3/awesome-code-world-models) | 2026-10-13 | [README at 54f2a44](https://github.com/yifliu3/awesome-code-world-models/blob/54f2a44eedf728df87402292803dee26de9acc71/README.md) |

## ICL: five additions

| First submission | Paper | Discovery collection |
| :--- | :--- | :--- |
| 2026-10-19 | [GPT-6 Astra Is a Native Visuo-Tactile Policy for Contact-Rich Manipulation](https://arxiv.org/abs/2610.26846) | [BraveBoBo/awesome-in-context-learning--in-robot](https://github.com/BraveBoBo/awesome-in-context-learning--in-robot/blob/70ef1ec8dc7de29f83abb1da490d56d6f4672b4a/README.md) |
| 2026-08-31 | [Zeva: In-Context Causal Learning for Generalizable Embodied Manipulation](https://arxiv.org/abs/2608.30880) | [asimfish/awesome_ICL](https://github.com/asimfish/awesome_ICL/blob/d36bc1548c876dec701dab5f26a64d8db26472a0/README.md) |
| 2026-08-26 | [Zero-WAM: In-Context World-Action Modeling from Human Videos for Open-Ended Task Generalization](https://arxiv.org/abs/2608.26103) | [asimfish/awesome_ICL](https://github.com/asimfish/awesome_ICL/blob/d36bc1548c876dec701dab5f26a64d8db26472a0/README.md) |
| 2026-08-26 | [RA-VLA: Retrieval-Augmented VLA for Test-Time Adaptation](https://arxiv.org/abs/2608.25585) | [Oliverbansk/Awesome-Test-Time-Robot-Learning](https://github.com/Oliverbansk/Awesome-Test-Time-Robot-Learning/blob/25f47b1ca3b3ef45dea0f4a3d189bc836e64a58a/README.md) |
| 2026-07-22 | [HOST: Robots Acquire Manipulation Skills in Seconds from a Single Human Video](https://arxiv.org/abs/2607.20033) | [asimfish/awesome_ICL](https://github.com/asimfish/awesome_ICL/blob/d36bc1548c876dec701dab5f26a64d8db26472a0/README.md) |

## RSI: five additions

| First submission | Paper | Discovery collection |
| :--- | :--- | :--- |
| 2026-10-14 | [AdaRSI: On-Demand Recursive Self-Improvement for Embodied Agents](https://arxiv.org/abs/2610.20474) | [pinkbubblebubble/awesome-rsi](https://github.com/pinkbubblebubble/awesome-rsi/blob/2d2c7f6778b528f1ddc75865d52b83968030fa38/README.md) |
| 2026-10-08 | [Embodied Turing Machines: Stateful Code for Robot Recursive Self-Improvement](https://arxiv.org/abs/2610.12369) | [pinkbubblebubble/awesome-rsi](https://github.com/pinkbubblebubble/awesome-rsi/blob/2d2c7f6778b528f1ddc75865d52b83968030fa38/README.md) |
| 2026-09-28 | [Self-Evolving Coding Agents: From Digital Programs to Physical-World Intelligence](https://arxiv.org/abs/2609.35432) | [cocacola-lab/awesome-embodied-rsi](https://github.com/cocacola-lab/awesome-embodied-rsi/blob/36f6eeb3b30e6f7374719e91268758f1b39105f6/README.md) |
| 2026-09-26 | [RoboFoundry: System-as-Policy Evolution for Self-Learning Embodied Agents](https://arxiv.org/abs/2609.32862) | [cocacola-lab/awesome-embodied-rsi](https://github.com/cocacola-lab/awesome-embodied-rsi/blob/36f6eeb3b30e6f7374719e91268758f1b39105f6/README.md) · [pinkbubblebubble/awesome-rsi](https://github.com/pinkbubblebubble/awesome-rsi/blob/2d2c7f6778b528f1ddc75865d52b83968030fa38/README.md) |
| 2026-09-24 | [HarnessPAI: An Evolving Harness for Physical AI](https://arxiv.org/abs/2609.29166) | [cocacola-lab/awesome-embodied-rsi](https://github.com/cocacola-lab/awesome-embodied-rsi/blob/36f6eeb3b30e6f7374719e91268758f1b39105f6/README.md) · [pinkbubblebubble/awesome-rsi](https://github.com/pinkbubblebubble/awesome-rsi/blob/2d2c7f6778b528f1ddc75865d52b83968030fa38/README.md) |

## TTT: five additions

| First submission | Paper | Discovery collection |
| :--- | :--- | :--- |
| 2026-08-10 | [VANE: Reliable Test-Time Training for Vision-Language-Action Models via Future Visual Representation Prediction](https://arxiv.org/abs/2608.09448) | [asimfish/awesome_robo_ttt](https://github.com/asimfish/awesome_robo_ttt/blob/92eec01bfa9e48f1cd2eca190c380eb190c947cb/README.md) |
| 2026-07-16 | [RoboTTT: Context Scaling for Robot Policies](https://arxiv.org/abs/2607.15275) | [Oliverbansk/Awesome-Test-Time-Robot-Learning](https://github.com/Oliverbansk/Awesome-Test-Time-Robot-Learning/blob/25f47b1ca3b3ef45dea0f4a3d189bc836e64a58a/README.md) · [asimfish/awesome_ICL](https://github.com/asimfish/awesome_ICL/blob/d36bc1548c876dec701dab5f26a64d8db26472a0/README.md) · [asimfish/awesome_robo_ttt](https://github.com/asimfish/awesome_robo_ttt/blob/92eec01bfa9e48f1cd2eca190c380eb190c947cb/README.md) |
| 2026-07-01 | [FAR: Failure-Aware Retry for Test-Time Recovery and Continual Policy Improvement](https://arxiv.org/abs/2607.01111) | [Oliverbansk/Awesome-Test-Time-Robot-Learning](https://github.com/Oliverbansk/Awesome-Test-Time-Robot-Learning/blob/25f47b1ca3b3ef45dea0f4a3d189bc836e64a58a/README.md) |
| 2026-06-02 | [TTT-VLA: Test-Time Latent Prompt Optimization for Vision-Language-Action Models](https://arxiv.org/abs/2606.03127) | [asimfish/awesome_robo_ttt](https://github.com/asimfish/awesome_robo_ttt/blob/92eec01bfa9e48f1cd2eca190c380eb190c947cb/README.md) |
| 2026-01-11 | [On-the-Fly VLA Adaptation via Test-Time Reinforcement Learning](https://arxiv.org/abs/2601.06748) | [Oliverbansk/Awesome-Test-Time-Robot-Learning](https://github.com/Oliverbansk/Awesome-Test-Time-Robot-Learning/blob/25f47b1ca3b3ef45dea0f4a3d189bc836e64a58a/README.md) · [asimfish/awesome_robo_ttt](https://github.com/asimfish/awesome_robo_ttt/blob/92eec01bfa9e48f1cd2eca190c380eb190c947cb/README.md) |

## Code World Model: five additions

| First submission | Paper | Discovery collection |
| :--- | :--- | :--- |
| 2026-10-08 | [AgentGarten: Code Worlds for Evolving Agents](https://arxiv.org/abs/2610.12374) | [yifliu3/awesome-code-world-models](https://github.com/yifliu3/awesome-code-world-models/blob/54f2a44eedf728df87402292803dee26de9acc71/README.md) |
| 2026-10-08 | [Memento 3: Model-Based Recursive Self-Improvement through Reflective Rulebooks](https://arxiv.org/abs/2610.11794) | [yifliu3/awesome-code-world-models](https://github.com/yifliu3/awesome-code-world-models/blob/54f2a44eedf728df87402292803dee26de9acc71/README.md) · [pinkbubblebubble/awesome-rsi](https://github.com/pinkbubblebubble/awesome-rsi/blob/2d2c7f6778b528f1ddc75865d52b83968030fa38/README.md) |
| 2026-09-28 | [EMPIRIC: Experiment-Driven Learning of Residual World Models for Robot Planning](https://arxiv.org/abs/2609.35047) | [yifliu3/awesome-code-world-models](https://github.com/yifliu3/awesome-code-world-models/blob/54f2a44eedf728df87402292803dee26de9acc71/README.md) |
| 2026-09-22 | [Code Plans, Diffusion Renders: Open-Ended Generative World Modeling](https://arxiv.org/abs/2609.26458) | [yifliu3/awesome-code-world-models](https://github.com/yifliu3/awesome-code-world-models/blob/54f2a44eedf728df87402292803dee26de9acc71/README.md) |
| 2026-09-09 | [Programmable World Model](https://arxiv.org/abs/2609.10540) | [yifliu3/awesome-code-world-models](https://github.com/yifliu3/awesome-code-world-models/blob/54f2a44eedf728df87402292803dee26de9acc71/README.md) |

## Classification notes

- **ICL:** RA-VLA uses retrieval and in-context imitation despite “Test-Time Adaptation” in its title. Zeva uses persistent interaction memory with frozen policy weights. The Astra visuo-tactile paper reports simulated contact-rich manipulation, not physical-robot validation.
- **RSI:** These entries update persistent agent components, but do not all modify the improvement algorithm itself. AdaRSI combines harness revision with selective VLA fine-tuning; COAP and HarnessPAI improve reusable code across iterations.
- **TTT:** RoboTTT updates fast weights; VANE and TTT-VLA optimize prompts; TT-VLA uses test-time reinforcement learning; FAR adapts from failure preferences during retries and separately trains on successful recoveries. Pure search, sampling, and retrieval were not counted as TTT additions.
- **Code World Model:** EMPIRIC includes physical-robot experiments. AgentGarten, Memento 3, CoDeR, and PWM study simulated or interactive worlds. Memento 3 also relates to RSI but is listed once, under its executable world-model mechanism.
- **Dates:** HOST's first arXiv submission is July 22, 2026; the later August public release date used in some collections is not its first-submission date. The README displays months; the tables here preserve exact dates.


## User-selected blog: 2026-10-23

- [Astra Beyond Tabletop: Into the Home](https://www.gt-rail.com/blog/astra-beyond-tabletop/#title), Yuchen Zheng et al., Georgia Tech RAIL. Added to **Blogs / Astra in the Real World** at the user's request.
- The original article describes 24 household tasks on a real Hello Robot Stretch 4 in a lab apartment, with task outcomes and reasoning-effort/depth ablations. The entry is a blog evaluation; the page's citation supplies 2026 but no exact publication date.
