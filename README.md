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
  <a href="#blogs">Blogs &amp; perspectives</a> &nbsp; · &nbsp;
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

<a id="icl"></a>

### ICL · In-Context Learning

Learning new embodied behaviors from demonstrations, trajectories, and interaction
histories presented at inference time. Priorities include demonstration selection,
sensorimotor context, and generalization to new tasks and scenes.

| Date | Paper | Title | Links | Learning Mechanism |
| :--- | :--- | :--- | :--- | :--- |
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
| 2026-10 | **RoboRSI** | RoboRSI: Stable, efficient, and reusable robot self-evolution in complex real-world environments. | [Paper](https://arxiv.org/abs/2610.12424) · [Project](https://lab.noematrix.ai/blog/2-roborsi/) · [Code](https://github.com/nssmd/RoboRSI) | Uses execution feedback to diagnose and locally revise a hierarchical skill tree, validate updates, and consolidate stable skill sequences for reuse. |

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
| 2026-07 | **WAM-TTT** | WAM-TTT: Steering World-Action Models by Watching Human Play at Test Time | [Paper](https://arxiv.org/abs/2607.06988) | Adapts lightweight memory from unlabeled human videos using video prediction while keeping the pretrained world-action model frozen. |
| 2026-02 | **TTT-Parkour** | TTT-Parkour: Rapid Test-Time Training for Perceptive Robot Parkour | [Paper](https://arxiv.org/abs/2602.02331) | Reconstructs unfamiliar terrain from RGB-D observations, fine-tunes a locomotion policy in simulation, and transfers the adapted policy to humanoid parkour. |

<p align="right"><a href="#contents">↑ Back to contents</a></p>

<a id="code-world-model"></a>

### Code World Model

Executable representations of an external world's state and dynamics. Priorities
include program induction from interaction, persistent world state, model revision,
and using executable models for planning or visual simulation.

| Date | Paper | Title | Links | Modeling Mechanism & Setting |
| :--- | :--- | :--- | :--- | :--- |
| 2026-08 | **Code World Model** | Code World Model: Coding Agent as World Brain | [Paper](https://arxiv.org/abs/2608.25927) | Uses a coding agent to maintain world state and evolution rules, then conditions video generation on a compiled proxy representation; demonstrated in interactive visual worlds. |
| 2024-02 | **WorldCoder** | WorldCoder, a Model-Based LLM Agent: Building World Models by Writing Code and Interacting with the Environment | [Paper](https://arxiv.org/abs/2402.12275) | Builds and revises Python world models from environment interactions, linking model synthesis to planning; evaluated on gridworlds and task-planning environments. |

<p align="right"><a href="#contents">↑ Back to contents</a></p>

---

## Blogs

Perspectives, technical deep dives, and research notes across the four directions.
The initial collection below focuses on RSI and self-evolving agents.

| Date | Title | Author / Organization | Links |
| :--- | :--- | :--- | :--- |
| 2026-08-06 | Building Physical RSI Beyond the Known World | MirroS Team | [Blog](https://mirros.ai/research/building-physical-rsi-beyond-the-known-world) |
| 2026-07-04 | Harness Engineering for Self-Improvement | Lilian Weng | [Blog](https://lilianweng.github.io/posts/2026-07-04-harness/) |
| 2026-06-08 | The What & When of Self-Evolving Agents | Xinming Tu | [Blog](https://xinmingtu.cn/blog/2026/self-evolving-agents/) |
| Not listed | PhysicalRSI: Recursive Self-Harness for Scaling Embodied Skills | Not listed | [Blog](https://yanming03.github.io/PhysicalRSI/) |

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
