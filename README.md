<a id="top"></a>

<h1 align="center">Frontier Embodied AI</h1>

<p align="center">
  <strong>In-Context Learning · Recursive Self-Improvement · Test-Time Training · Code World Model</strong><br>
  A curated collection of papers, code, and perspectives on embodied agents that learn from context,
  improve through experience, adapt at test time, and reason with executable world models.
</p>

<p align="center">
  <a href="https://awesome.re"><img src="https://awesome.re/badge.svg" alt="Awesome"></a>
  <a href="#icl"><img src="https://img.shields.io/badge/Explore-ICL-527AA3?style=flat-square&amp;labelColor=253449" alt="In-Context Learning"></a>
  <a href="#rsi"><img src="https://img.shields.io/badge/Explore-RSI-7D5CC6?style=flat-square&amp;labelColor=253449" alt="Recursive Self-Improvement"></a>
  <a href="#ttt"><img src="https://img.shields.io/badge/Explore-TTT-A98032?style=flat-square&amp;labelColor=253449" alt="Test-Time Training"></a>
  <a href="#code-world-model"><img src="https://img.shields.io/badge/Explore-Code%20World%20Model-1FA7A3?style=flat-square&amp;labelColor=253449" alt="Code World Model"></a>
</p>

<p align="center">
  <a href="#research-map">Research map</a> &nbsp; · &nbsp;
  <a href="#papers">Papers</a> &nbsp; · &nbsp;
  <a href="#paper-collections">Paper collections</a> &nbsp; · &nbsp;
  <a href="#blogs">Blogs &amp; perspectives</a> &nbsp; · &nbsp;
  <a href="#astra-in-the-real-world">Astra in the real world</a> &nbsp; · &nbsp;
  <a href="#contributing">Contribute</a>
</p>

## Contents

<table>
  <tr>
    <td width="50%" valign="top">
      <h3>01 · In-Context Learning</h3>
      <p>Acquire new behaviors from demonstrations and interaction histories supplied as context.</p>
      <p><a href="#icl"><strong>Explore ICL →</strong></a></p>
    </td>
    <td width="50%" valign="top">
      <h3>02 · Recursive Self-Improvement</h3>
      <p>Turn execution feedback into reusable skills and stronger learning processes.</p>
      <p><a href="#rsi"><strong>Explore RSI →</strong></a></p>
    </td>
  </tr>
  <tr>
    <td width="50%" valign="top">
      <h3>03 · Test-Time Training</h3>
      <p>Update policies, representations, or adaptive memory using deployment-time experience.</p>
      <p><a href="#ttt"><strong>Explore TTT →</strong></a></p>
    </td>
    <td width="50%" valign="top">
      <h3>04 · Code World Model</h3>
      <p>Represent world state and dynamics as executable code for simulation and planning.</p>
      <p><a href="#code-world-model"><strong>Explore Code World Model →</strong></a></p>
    </td>
  </tr>
</table>

## Research Map

The collection connects four mechanisms for building adaptable embodied agents.
Robot learning is the central application; interactive environments and foundational
methods are included when they directly inform these mechanisms.

| Direction | Central question | What changes? | Typical evidence |
| :--- | :--- | :--- | :--- |
| **ICL — In-Context Learning** | Can an agent learn a new behavior from examples in its context? | Demonstrations, retrieved experience, or interaction history; policy parameters remain fixed during adaptation. | Generalization to new tasks from a small number of contextual demonstrations. |
| **RSI — Recursive Self-Improvement** | Can an agent use its own outcomes to improve capabilities it will reuse? | Skills, policies, data collection, evaluators, or the improvement process across iterations. | Repeated feedback–revision–validation cycles and reuse of acquired capabilities. |
| **TTT — Test-Time Training** | Can an agent learn from the environment it encounters at deployment? | Selected parameters, adapters, or fast-weight memory through a training objective. | Adaptation to new tasks, observations, terrain, or dynamics at test time. |
| **Code World Model** | Can an agent build and execute a model of how its world evolves? | Programs representing state, transitions, rules, or rewards. | Executable predictions, consistency with observations, and downstream planning or simulation. |

**Reading guide.** Papers are grouped by their main mechanism and listed newest first,
using the first public paper date. These directions can overlap: a self-improvement
loop may use TTT to adapt and a code world model to evaluate candidate actions.
The RSI section includes embodied self-improvement systems and supporting mechanisms;
each entry states what is actually revised. Code world model entries identify their
evaluation setting so that interactive-world results remain distinct from robot experiments.

---

## Papers

**2026-10-20 update:** Added five papers per direction (20 new entries), prioritizing
recent work relevant to embodied learning and executable worlds. Titles, first-submission
dates, and mechanisms were checked against the original papers. See the
[selection and source record](SOURCES.md) for the collection-to-paper mapping.

<a id="icl"></a>

### ICL · In-Context Learning

Learning new embodied behaviors from demonstrations, trajectories, and interaction
histories presented at inference time. Priorities include demonstration selection,
sensorimotor context, and generalization to new tasks and scenes.

| Date | Paper | Title | Links | Learning Mechanism |
| :--- | :--- | :--- | :--- | :--- |
| 2026-10 | **Astra Visuo-Tactile** | GPT-6 Astra Is a Native Visuo-Tactile Policy for Contact-Rich Manipulation | [Paper](https://arxiv.org/abs/2610.26846) | Uses few-shot context and visual/tactile RGB observations for closed-loop contact-rich control; evaluated on simulated UniVTAC and OpenViTac tasks, with physical-robot validation left for future work. |
| 2026-08 | **Zeva** | Zeva: In-Context Causal Learning for Generalizable Embodied Manipulation | [Paper](https://arxiv.org/abs/2608.30880) | Encodes executed actions and resulting state changes into causal memory, retrieving relevant interactions as context for a frozen policy; evaluated in simulation and real-world manipulation. |
| 2026-08 | **Zero-WAM** | Zero-WAM: In-Context World-Action Modeling from Human Videos for Open-Ended Task Generalization | [Paper](https://arxiv.org/abs/2608.26103) · [Project](https://robbyant-research.github.io/Zero-WAM/) | Conditions a causal video-action model on human demonstration videos, using an in-context future-prediction training objective to support unseen-task execution without parameter updates; evaluated in simulation and real robots. |
| 2026-08 | **RA-VLA** | RA-VLA: Retrieval-Augmented VLA for Test-Time Adaptation | [Paper](https://arxiv.org/abs/2608.25585) | Retrieves behavior-aligned demonstrations and grounds their use in action generation for training-free adaptation; evaluated on LIBERO and a real UR5e robot. |
| 2026-07 | **HOST** | HOST: Robots Acquire Manipulation Skills in Seconds from a Single Human Video | [Paper](https://arxiv.org/abs/2607.20033) | Follows a single human video through progress estimation, predicted robot observations, and action generation to acquire manipulation skills at inference time. |
| 2026-03 | **ICLR** | ICLR: In-Context Imitation Learning with Visual Reasoning | [Paper](https://arxiv.org/abs/2603.07530) | Augments demonstration prompts with visual reasoning traces of future trajectories and predicts actions autoregressively; evaluated in simulation and real-world manipulation. |
| 2024-08 | **ICRT** | In-Context Imitation Learning via Next-Token Prediction | [Paper](https://arxiv.org/abs/2408.15980) · [Project](https://icrt.dev/) | Conditions a robot transformer on demonstrated image–action–state trajectories to execute new tasks with fixed policy parameters; evaluated on a real Franka robot. |
| 2024-03 | **KAT** | Keypoint Action Tokens Enable In-Context Imitation Learning in Robotics | [Paper](https://arxiv.org/abs/2403.19578) · [Project](https://www.robot-learning.uk/keypoint-action-tokens) | Encodes visual keypoints and action trajectories as tokens, enabling a pretrained language model to imitate a few demonstrations on real-world manipulation tasks. |

<p align="right"><a href="#contents">↑ Back to contents</a></p>

<a id="rsi"></a>

### RSI · Recursive Self-Improvement

Embodied agents that collect experience, diagnose outcomes, revise capabilities,
and validate improvements for subsequent tasks. Priorities include reusable skill
libraries, autonomous feedback, and improvements to the learning loop itself.

| Date | Paper | Title | Links | Improvement Mechanism |
| :--- | :--- | :--- | :--- | :--- |
| 2026-10 | **AdaRSI** | AdaRSI: On-Demand Recursive Self-Improvement for Embodied Agents | [Paper](https://arxiv.org/abs/2610.20474) | Revises skills and harnesses first, then diagnoses persistent sub-step failures and selectively fine-tunes the VLA using self-collected demonstrations; evaluated in RoboCasa365 simulation. |
| 2026-10 | **COAP** | Embodied Turing Machines: Stateful Code for Robot Recursive Self-Improvement | [Paper](https://arxiv.org/abs/2610.12369) | Uses coding agents to iteratively extend a shared state-tracking and control library, enabling reuse across tasks with no VLM or VLA in the runtime loop; evaluated on 42 simulated RoboDojo tasks. |
| 2026-10 | **RoboRSI** | RoboRSI: Stable, efficient, and reusable robot self-evolution in complex real-world environments. | [Paper](https://arxiv.org/abs/2610.12424) · [Project](https://lab.noematrix.ai/blog/2-roborsi/) · [Code](https://github.com/nssmd/RoboRSI) | Uses execution feedback to diagnose and locally revise a hierarchical skill tree, validate updates, and consolidate stable skill sequences for reuse. |
| 2026-09 | **Physical Coding** | Self-Evolving Coding Agents: From Digital Programs to Physical-World Intelligence | [Paper](https://arxiv.org/abs/2609.35432) | Represents task state and execution as world and policy code, converting verified robot traces into reusable tools, memory, and training data; studied in RoboCasa365, physics tasks, and dual-arm robot experiments. |
| 2026-09 | **RoboFoundry** | RoboFoundry: System-as-Policy Evolution for Self-Learning Embodied Agents | [Paper](https://arxiv.org/abs/2609.32862) · [Project](https://jingsongliang.com/robofoundry) | Turns execution failures into validated updates to context management, persistent memory, and hierarchical skills, promoting recurring changes into a reusable agent system; evaluated in simulation and across real robots. |
| 2026-09 | **HarnessPAI** | HarnessPAI: An Evolving Harness for Physical AI | [Paper](https://arxiv.org/abs/2609.29166) · [Project](https://darwin-agent.github.io/HarnessPAI) | Revises executable programs across rollouts using outcome feedback and distills failures into reusable skills; evaluated across simulated embodiments and used to collect data for subsequent policy fine-tuning. |

See also the [RSI blogs and perspectives](#blogs) for discussions of self-improvement
harnesses and physical learning loops.

<p align="right"><a href="#contents">↑ Back to contents</a></p>

<a id="ttt"></a>

### TTT · Test-Time Training

Learning during deployment through explicit optimization of policies, representations,
or adaptive memory. Priorities include self-supervised objectives, fast weights,
and adaptation from observations or human demonstrations.

| Date | Paper | Title | Links | Adaptation Mechanism |
| :--- | :--- | :--- | :--- | :--- |
| 2026-09 | **T²Mem** | T²Mem: Learning Test-Time Memory for Robotics | [Paper](https://arxiv.org/abs/2609.36720) · [Project](https://yzliu84.github.io/T2MEM-project/) | Compresses observation history into fast-weight memory through online self-supervised updates for memory-dependent manipulation; evaluated on RoboMME. |
| 2026-08 | **VANE** | VANE: Reliable Test-Time Training for Vision-Language-Action Models via Future Visual Representation Prediction | [Paper](https://arxiv.org/abs/2608.09448) | Optimizes context-conditioned prompts using future visual-representation prediction, validating candidate updates against later observations before committing them; evaluated on SimplerEnv embodiments. |
| 2026-07 | **RoboTTT** | RoboTTT: Context Scaling for Robot Policies | [Paper](https://arxiv.org/abs/2607.15275) · [Project](https://research.nvidia.com/labs/gear/robottt/) | Compresses long visuomotor histories into fast weights updated by gradient descent at inference, supporting human-video imitation and long-horizon real-robot manipulation. |
| 2026-07 | **FAR** | FAR: Failure-Aware Retry for Test-Time Recovery and Continual Policy Improvement | [Paper](https://arxiv.org/abs/2607.01111) · [Project](https://hoar012.github.io/FAR-Project) | Adapts policies using failure-contrastive preferences during retries, combines this with action perturbations, and reuses successful recoveries for continual training; evaluated in simulated and real manipulation. |
| 2026-07 | **WAM-TTT** | WAM-TTT: Steering World-Action Models by Watching Human Play at Test Time | [Paper](https://arxiv.org/abs/2607.06988) | Adapts lightweight memory from unlabeled human videos using video prediction while keeping the pretrained world-action model frozen. |
| 2026-06 | **TTT-VLA** | TTT-VLA: Test-Time Latent Prompt Optimization for Vision-Language-Action Models | [Paper](https://arxiv.org/abs/2606.03127) | Optimizes only latent prompts from deployment interactions using a self-supervised proxy objective while freezing the underlying policy; evaluated on single- and multi-embodiment SimplerEnv tasks. |
| 2026-02 | **TTT-Parkour** | TTT-Parkour: Rapid Test-Time Training for Perceptive Robot Parkour | [Paper](https://arxiv.org/abs/2602.02331) | Reconstructs unfamiliar terrain from RGB-D observations, fine-tunes a locomotion policy in simulation, and transfers the adapted policy to humanoid parkour. |
| 2026-01 | **TT-VLA** | On-the-Fly VLA Adaptation via Test-Time Reinforcement Learning | [Paper](https://arxiv.org/abs/2601.06748) | Uses dense task-progress rewards to update VLA policies through test-time reinforcement learning while retaining pretrained priors; evaluated in simulated and real-world deployment settings. |

<p align="right"><a href="#contents">↑ Back to contents</a></p>

<a id="code-world-model"></a>

### Code World Model

Executable representations of an external world's state and dynamics. Priorities
include program induction from interaction, persistent world state, model revision,
and using executable models for planning or visual simulation.

| Date | Paper | Title | Links | Modeling Mechanism & Setting |
| :--- | :--- | :--- | :--- | :--- |
| 2026-10 | **AgentGarten** | AgentGarten: Code Worlds for Evolving Agents | [Paper](https://arxiv.org/abs/2610.12374) · [Project](https://mirros-lab.github.io/agent-garten) | Combines program-defined simulation state and interaction rules with a shared neural renderer, enabling agents to practice in interactive code worlds and refine inherited playbooks. |
| 2026-10 | **Memento 3** | Memento 3: Model-Based Recursive Self-Improvement through Reflective Rulebooks | [Paper](https://arxiv.org/abs/2610.11794) | Compiles revisable rulebooks into executable world models and accepts updates after fidelity checks and transition replay; evaluated on ARC-AGI-3 and Atari Pong with a frozen LLM. |
| 2026-09 | **EMPIRIC** | EMPIRIC: Experiment-Driven Learning of Residual World Models for Robot Planning | [Paper](https://arxiv.org/abs/2609.35047) · [Project](https://yichao-liang.github.io/empiric) | Extends a physics engine with synthesized programs for missing mechanisms, estimating parameters through Bayesian inference and revising models through experiments; evaluated in five simulated domains and real-robot manipulation. |
| 2026-09 | **CoDeR** | Code Plans, Diffusion Renders: Open-Ended Generative World Modeling | [Paper](https://arxiv.org/abs/2609.26458) · [Project](https://becauseimbatman0.github.io/CoDeR) | Coordinates agent roles to construct executable world rules and dynamics, with video models rendering persistent state; studied in interactive visual worlds with autonomous evolution and multiple entities. |
| 2026-09 | **PWM** | Programmable World Model | [Paper](https://arxiv.org/abs/2609.10540) · [Project](https://alaya-lab.github.io/pwm) · [Code](https://github.com/AlayaLab/pwm) | Executes programs over persistent entity states and transition rules, compiling state-augmented 3D boxes into video-model controls; evaluated on programmable game worlds and CombatStateBench. |
| 2026-08 | **Code World Model** | Code World Model: Coding Agent as World Brain | [Paper](https://arxiv.org/abs/2608.25927) | Uses a coding agent to maintain world state and evolution rules, then conditions video generation on a compiled proxy representation; demonstrated in interactive visual worlds. |
| 2024-02 | **WorldCoder** | WorldCoder, a Model-Based LLM Agent: Building World Models by Writing Code and Interacting with the Environment | [Paper](https://arxiv.org/abs/2402.12275) | Builds and revises Python world models from environment interactions, linking model synthesis to planning; evaluated on gridworlds and task-planning environments. |

<p align="right"><a href="#contents">↑ Back to contents</a></p>

---

## Paper Collections

Discovery sources reviewed on **2026-10-20**. These lists have different scopes;
entries above are selected by mechanism and verified against their original papers.
The [source record](SOURCES.md) links the exact collection snapshots used.

| Direction | Collections | Coverage used here |
| :--- | :--- | :--- |
| **ICL** | [Awesome Embodied ICL](https://github.com/asimfish/awesome_ICL) · [Robot ICL digest](https://github.com/BraveBoBo/awesome-in-context-learning--in-robot) | Human-video prompting, interaction memory, and recent robot ICL papers. |
| **RSI** | [Awesome Embodied RSI](https://github.com/cocacola-lab/awesome-embodied-rsi) · [Awesome RSI](https://github.com/pinkbubblebubble/awesome-rsi) | Persistent skill, harness, code, and policy improvement in embodied agents. |
| **TTT / ICL** | [Awesome Test-Time Robot Learning](https://github.com/Oliverbansk/Awesome-Test-Time-Robot-Learning) · [Awesome Robot TTT](https://github.com/asimfish/awesome_robo_ttt) | Deployment-time optimization, fast-weight memory, failure-driven adaptation, and contextual retrieval. |
| **Code World Model** | [Awesome Code World Models](https://github.com/yifliu3/awesome-code-world-models) | Executable dynamics, persistent world state, programmatic simulation, and planning. |

<p align="right"><a href="#contents">↑ Back to contents</a></p>

---

## Blogs

Perspectives, technical deep dives, and research notes on embodied learning and
real-world agent evaluations.

### RSI and Self-Evolving Agents

| Date | Title | Author / Organization | Links |
| :--- | :--- | :--- | :--- |
| 2026-08-06 | Building Physical RSI Beyond the Known World | MirroS Team | [Blog](https://mirros.ai/research/building-physical-rsi-beyond-the-known-world) |
| 2026-07-04 | Harness Engineering for Self-Improvement | Lilian Weng | [Blog](https://lilianweng.github.io/posts/2026-07-04-harness/) |
| 2026-06-08 | The What & When of Self-Evolving Agents | Xinming Tu | [Blog](https://xinmingtu.cn/blog/2026/self-evolving-agents/) |
| Not listed | PhysicalRSI: Recursive Self-Harness for Scaling Embodied Skills | Not listed | [Blog](https://yanming03.github.io/PhysicalRSI/) |

### Astra in the Real World

Real-robot evaluations of Astra as a policy for physical interaction.

| Date | Title | Author / Organization | Links |
| :--- | :--- | :--- | :--- |
| 2026 | Astra Beyond Tabletop: Into the Home | Yuchen Zheng et al. / Georgia Tech RAIL | [Blog](https://www.gt-rail.com/blog/astra-beyond-tabletop/#title) |

Evaluates zero-shot mobile manipulation with Hello Robot Stretch 4 across 24
household tasks in a lab apartment, using relative joint and base commands.
Reports task outcomes, reasoning-effort and wrist-depth ablations, and recurring
limitations in fine manipulation, cross-step dependencies, collision avoidance,
and execution efficiency.

<p align="right"><a href="#contents">↑ Back to contents</a></p>

---

## Contributing

Suggestions and pull requests are welcome.

- Choose **ICL**, **RSI**, **TTT**, **Code World Model**, or **Blogs**. For work spanning directions, place it under the main contribution and describe the connection.
- Include the full title, first public publication date, and original paper or blog link. Add official project and code links when available.
- Explain the mechanism in one sentence: what the agent learns or updates, what feedback it uses, and where it is evaluated.
- Distinguish real-robot experiments, simulation, and other interactive environments. Describe demonstrated capabilities precisely.
- Keep entries newest first within each section; use **Not listed** for unknown dates or authors.

<!-- Paper entry template — replace placeholders with verified information:
| YYYY-MM | **Short name** | Full paper title | [Paper](URL) · [Project](URL) · [Code](URL) | Mechanism, feedback, and evaluation setting. |

Blog entry template:
| YYYY-MM-DD | Full blog title | Author / Organization | [Blog](URL) |
-->

---

<p align="center">
  <strong>Frontier Embodied AI</strong><br>
  Learning from context. Improving through experience. Adapting at test time. Modeling worlds with code.<br><br>
  <a href="#top">Back to top ↑</a> &nbsp; · &nbsp;
  <a href="https://github.com/wangskyone/awesome-VLA-WAM">Awesome VLA–WAM</a>
</p>
