# SVBench: Evaluation of Video Generation Models on Social Reasoning

## Introduction

Recent text-to-video generation models have achieved remarkable progress in visual realism, motion fidelity, and text–video alignment. However, these models remain fundamentally limited in their ability to generate socially coherent behavior. Unlike humans—who effortlessly infer intentions, beliefs, emotions, and social norms from brief visual cues—current video generation models tend to render literal scenes without capturing the underlying causal or psychological logic.

While modern diffusion- and transformer-based architectures can synthesize dynamic scenes with striking realism and reproduce complex motion patterns and multi-agent interactions, they struggle to represent **why** people act the way they do—failing to capture the latent beliefs, intentions, emotions, and norms that structure real human interactions.

**SVBench** addresses this critical gap by introducing the first benchmark specifically designed to evaluate social reasoning capabilities in video generation models. Grounded in findings from developmental and social psychology, our benchmark organizes thirty classic social cognition paradigms into seven core dimensions:

- **Mental State Inference** - Understanding beliefs and theory of mind
- **Goal-Directed Action** - Recognizing intentional behaviors and goals  
- **Joint Attention & Perspective** - Following gaze and understanding perspectives
- **Social Coordination** - Turn-taking and collaborative behavior
- **Emotion & Prosocial Behavior** - Emotion recognition and helping behaviors
- **Social Norms & Spacing** - Personal space and social conventions
- **Multi-Agent Social Strategy** - Complex multi-agent interactions

Our benchmark reveals substantial performance gaps in current video generation systems: while modern models excel in surface-level plausibility, they systematically fail in **intention recognition**, **belief reasoning**, **joint attention**, and **prosocial inference**.
<p align="center">
  <img src="asset/intro.png" width="600">
</p>
<p align="center"><i></i></p>


## Demos
<div style="display: flex; justify-content: center;">
<table align="center">
  <!-- Row 1 -->
  <tr>
    <td><video src="asset/video/EXP_010-9-easy.mp4" width="280" controls autoplay loop muted></video></td>
    <td><video src="asset/video/EXP_011-1-hard.mp4" width="280" controls autoplay loop muted></video></td>
    <td><video src="asset/video/EXP_012-1-hard.mp4" width="280" controls autoplay loop muted></video></td>
  </tr>
  <tr>
    <td align="left"><b>Prompt:</b> A marble is at the bottom of a tall, narrow tube on a table. Two tools are available nearby: a long, thin stick and a short, thick stick. A child first holds their hand up against the side of the tube to gauge its height, and then extends their hand towards the area where the two sticks are placed.<br><b>Ground Truth:</b> Child will pick the long thin stick.<br><b>Question:</b> Does the child pick the long thin stick?</td>
    <td align="left"><b>Prompt:</b> A woman directs her gaze toward a red toy on the floor. A boy is beside her, looking at the woman.<br><b>Ground Truth:</b> Boy will look at the red toy on the floor.<br><b>Question:</b> Does the boy look at the red toy on the floor?</td>
    <td align="left"><b>Prompt:</b> On a table are two open boxes, one red and one blue. A woman is extending her finger to point at the blue box. A child is looking at the woman's hand.<br><b>Ground Truth:</b> Child will look in the blue box.<br><b>Question:</b> Does the child look in the blue box?</td>
  </tr>
  <!-- Row 2 -->
  <tr>
    <td><video src="asset/video/EXP_014-1-hard.mp4" width="280" controls autoplay loop muted></video></td>
    <td><video src="asset/video/EXP_014-4-hard.mp4" width="280" controls autoplay loop muted></video></td>
    <td><video src="asset/video/EXP_014-7-hard.mp4" width="280" controls autoplay loop muted></video></td>
  </tr>
  <tr>
    <td align="left"><b>Prompt:</b> A woman holds a colorful toy next to her face. A child is nearby.<br><b>Ground Truth:</b> The woman and the child will shift their gaze back and forth between the toy and each other's faces, establishing coordinated joint attention.<br><b>Question:</b> What is the pattern of looking behavior between the woman and the child in relation to the toy and each other?</td>
    <td align="left"><b>Prompt:</b> A woman and a boy are sitting on the floor with a small toy between them.<br><b>Ground Truth:</b> The woman and the boy will maintain coordinated joint attention, repeatedly shifting their gaze between the toy and each other.<br><b>Question:</b> How do the woman and boy coordinate their attention between the toy and each other?</td>
    <td align="left"><b>Prompt:</b> A woman and a boy are standing face-to-face, and the woman holds a toy car between them.<br><b>Ground Truth:</b> The woman and the boy will engage in reciprocal, back-and-forth gazes and interactions between the toy and each other's faces.<br><b>Question:</b> How do the woman and the boy interact with each other in relation to the toy?</td>
  </tr>
  <!-- Row 3 -->
  <tr>
    <td><video src="asset/video/EXP_016-4-hard.mp4" width="280" controls autoplay loop muted></video></td>
    <td><video src="asset/video/EXP_018-2-medium.mp4" width="280" controls autoplay loop muted></video></td>
    <td><video src="asset/video/EXP_019-5-medium.mp4" width="280" controls autoplay loop muted></video></td>
  </tr>
  <tr>
    <td align="left"><b>Prompt:</b> A man and a woman are seated opposite one another at a table. The woman speaks a short sentence, pauses, and then turns her head to look directly at the man.<br><b>Ground Truth:</b> Man speaks next.<br><b>Question:</b> Does the man speak next?</td>
    <td align="left"><b>Prompt:</b> On the floor of a room, there are red and blue rings. A boy is standing before them, appearing to hesitate about which one to choose. At this moment, a nearby woman first looks at the boy, then clearly points her finger at the red ring on the floor.<br><b>Ground Truth:</b> The boy will walk towards the red ring based on the woman's cue.<br><b>Question:</b> Does the boy walk towards the red ring based on the woman's cue?</td>
    <td align="left"><b>Prompt:</b> A man and a woman are positioned next to each other. The woman emits a loud laugh, and the man, his attention drawn by the sound, turns his head in her direction.<br><b>Ground Truth:</b> The man and boy adopt happy expressions (smile/laugh).<br><b>Question:</b> Do the man and the boy adopt happy expressions, such as smiling or laughing?</td>
  </tr>
  <!-- Row 4 -->
  <tr>
    <td><video src="asset/video/EXP_020-2-medium.mp4" width="280" controls autoplay loop muted></video></td>
    <td><video src="asset/video/EXP_021-3-hard.mp4" width="280" controls autoplay loop muted></video></td>
    <td><video src="asset/video/EXP_022-1-easy.mp4" width="280" controls autoplay loop muted></video></td>
  </tr>
  <tr>
    <td align="left"><b>Prompt:</b> A man holding a stack of books stands in front of a closed cabinet door. A woman is nearby.<br><b>Ground Truth:</b> The woman will infer he cannot open the door and will open it for him.<br><b>Question:</b> What is the woman likely to do?</td>
    <td align="left"><b>Prompt:</b> A girl is crying on a park bench. A dropped ice cream cone is on the ground nearby. A woman is sitting on the other end of the bench.<br><b>Ground Truth:</b> The woman will notice the crying girl and offer comfort.<br><b>Question:</b> Describe the most likely interaction between the woman and the girl.</td>
    <td align="left"><b>Prompt:</b> At the edge of a mud puddle, so expansive that one must step into it to retrieve anything from the middle, a child is unable to retrieve his toy. The boy is wearing clean cloth shoes, but the man is wearing clean but waterproof shoes. The boy looks at a man in clean shoes, also standing at the edge, and points at the toy.<br><b>Ground Truth:</b> The man will step into the mud to retrieve the toy, getting his shoes dirty.<br><b>Question:</b> What will the man do about the toy?</td>
  </tr>
  <!-- Row 5 -->
  <tr>
    <td><video src="asset/video/EXP_023-2-medium.mp4" width="280" controls autoplay loop muted></video></td>
    <td><video src="asset/video/EXP_024-2-medium.mp4" width="280" controls autoplay loop muted></video></td>
    <td><video src="asset/video/EXP_028-5-medium.mp4" width="280" controls autoplay loop muted></video></td>
  </tr>
  <tr>
    <td align="left"><b>Prompt:</b> A woman is sitting on an empty park bench. A man sits down right next to her. She gets a tense, uncomfortable feeling.<br><b>Ground Truth:</b> The woman will shift away from the man to increase her personal space.<br><b>Question:</b> What is the woman's most likely next action?</td>
    <td align="left"><b>Prompt:</b> A woman is next in line at a coffee counter. A man walks up and stands in front of her, and she stares at the back of his head with a frown.<br><b>Ground Truth:</b> The woman will verbally correct the man, telling him to go to the back of the line.<br><b>Question:</b> What is the woman likely to do?</td>
    <td align="left"><b>Prompt:</b> An opaque screen stands in the middle of a table. A child on one side is reaching and fumbling, trying to find a toy on the other side. An adult, who can see the toy, is opposite them.<br><b>Ground Truth:</b> The adult will hand the toy to the child, knowing the child cannot see it.<br><b>Question:</b> What is the most effective way for the adult to help?</td>
  </tr>
</table>
</div>

## Overview
<p align="center">
  <img src="asset/pipeline.png" width="1000">
</p>
<p align="center"><i> SVBench framework overview</i></p>

### Pipeline Framework

SVBench employs a fully **training-free, agent-based pipeline** to construct and evaluate social reasoning tasks for video generation. The framework consists of two main stages:

#### Agent-Based Generation Stage

This stage transforms abstract psychological paradigms into concrete, video-ready prompts through three specialized agents:

1. **Experiment Understanding Agent**
   - Processes psychological experiment descriptions
   - Distills underlying social reasoning mechanisms
   - Creates structured conceptual blueprints with key concepts, test points, and ground truths
   - Ensures downstream generation is grounded in cognitive constructs rather than superficial details

2. **Prompt Synthesis Agent**
   - Translates abstract cognitive paradigms into visually grounded scenarios
   - Generates action-oriented descriptions using only observable behaviors
   - Ensures temporal feasibility (5–10 second clips)
   - Creates concrete instantiations with specific entities and contexts
   - Maintains separation between action descriptions and expected outcomes

3. **Critic Agent**
   - Enforces conceptual neutrality by removing interpretive language
   - Detects and eliminates ground-truth leakage
   - Generates difficulty-controlled variants (easy, medium, hard) by manipulating social cues
   - Provides structured feedback for iterative refinement
   - Ensures validated, difficulty-controlled prompts for each experiment

#### Agent-Based Evaluation Stage

Generated videos are assessed using a Vision-Language Model (VLM) judge across **five discrete, interpretable dimensions**:

- **D1: Core Paradigm Replication** - Correctness of psychological phenomenon instantiation
- **D2: Prompt Faithfulness** - Adherence to specified agents, objects, and scenes
- **D3: Social Coherence** - Causal and social plausibility of agent behaviors
- **D4: Social Cue Effectiveness** - Quality of perceptual cues (gaze, gestures, etc.)
- **D5: Video Plausibility** - Visual stability baseline (isolates generation vs. reasoning failures)

Each dimension is scored as a binary {0, 1}, with the overall score computed as the average: **S_overall = (1/5) × Σ D_k**

This discrete evaluation approach enhances robustness by framing assessment as unambiguous factual questions, aligning more closely with human categorical judgments and substantially reducing inter-trial variance.

### Key Features

✅ **First benchmark for social reasoning in video generation**  
✅ **Grounded in developmental and social psychology**  
✅ **30 classic experiments spanning 7 core social cognition dimensions**  
✅ **Fully training-free, scalable pipeline**  
✅ **Difficulty-controlled scenario generation**  
✅ **Interpretable 5-dimensional evaluation framework**  
✅ **Comprehensive evaluation of 7 state-of-the-art video generation models**

### Benchmark Results

Our extensive evaluation across seven state-of-the-art video generation systems reveals:

- **Top performers** (Sora2-Pro: 79.6%, Veo-3.1: 72.4%) show strong implicit priors for human motion causality and intention-driven interactions
- **Mid-tier models** (Hailuo02-S: 56.4%, Kling2.5-Turbo: 52.2%) struggle with coordinated multi-agent behavior and abstract social inference
- **Open-source models** (HunyuanVideo: 30.8%, LongCat-Video: 39.2%, LTX-1.0: 27.6%) operate at substantially lower performance levels
- **Critical gap**: Models excel at physical reasoning but lack explicit mechanisms for social reasoning

These findings highlight the fundamental distinction between perceptual realism and socially coherent behavior, revealing where current generation systems succeed or fundamentally fail in generating socially intelligent video content.

