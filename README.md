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

## Overview
<p align="center">
  <img src="asset/pipeline.png" width="1200">
</p>
<p align="center"><i>Figure 1: SVBench framework overview</i></p>

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

---

**Paper:** CVPR 2026 Submission #16418  
**Title:** SVBench: Evaluation of Video Generation Models on Social Reasoning
