---
name: present-plan
description: Transform complex plans, roadmaps, implementation proposals, and multi-stage recommendations into fast, layered visual briefings. Use when a plan contains several stages, dependencies, parallel work, decisions, risks, alternatives, or enough prose that readers may miss important structure; also use when the user asks to visualize, present, narrate, animate, summarize, or make a plan easier to understand quickly.
disable-model-invocation: true
---

# Present Plan

Turn a plan into a navigable mental model. Optimize first for speed and understanding, then preserve depth through optional drill-down.

## Core principles

- Keep one canonical plan model and derive every presentation from it.
- Reveal information progressively: orientation first, path second, details on demand.
- Show relationships spatially instead of repeating prose.
- Preserve consequential uncertainty. Label unknown duration, ownership, confidence, or dependencies rather than inventing them.
- Separate the plan's substance from its presentation. Do not silently change scope, sequence, commitments, or decisions to make the visual cleaner.
- Prefer one strong view over a dashboard of weak views.

## Workflow

1. Establish the source plan. If the user supplied one, treat it as authoritative. If the request asks both to devise and present a plan, develop the plan before formatting it.
2. Read [references/plan-schema.md](references/plan-schema.md). Normalize the source into that model internally; do not expose YAML or JSON unless requested.
3. Identify the plan's dominant structure: sequence, parallel work, branching decisions, transformation, time allocation, or stakeholder tradeoffs.
4. Read [references/format-selection.md](references/format-selection.md) and choose the smallest presentation that makes the dominant structure obvious.
5. Produce the 10-second layer: one outcome sentence and one primary visual.
6. Add the 60-second layer only when useful: a short guided walkthrough, step-through, or narration that follows the same labels and order as the visual.
7. Preserve depth through selection, expansion, or concise follow-up sections. Avoid placing full task descriptions permanently on the main surface.
8. Run the quality gate before responding.

## Default briefing

Use this composition unless the user requests another medium:

- State the intended outcome in one plain sentence.
- Show 3-7 meaningful stages. Group smaller tasks beneath them.
- Emphasize the critical path and show parallel work in aligned lanes.
- Attach decisions and risks to the stage they affect.
- Show the success check at the end of the route.
- Put details behind interaction or short expandable explanations when the surface supports it.

For a static structure that labels and connects the whole plan, use Mermaid. For step-throughs, branching exploration, selected-state detail, or synchronized playback, use the available visualization capability and follow its instructions. Use presentations, audio, or video when the user asks for them or when the delivery setting clearly requires that medium.

## Guided playback

Use playback only when directed attention materially improves comprehension.

- Keep the walkthrough between 30 and 90 seconds when spoken normally.
- Highlight exactly one current stage or relationship at a time.
- Explain purpose and causality, not every task.
- Keep narration synchronized with visible labels.
- Allow pausing and direct stage selection when the medium supports interaction.
- Provide a compact written fallback for audio.

Do not frame a long text-to-speech reading as a podcast. For a conversational briefing, synthesize genuine perspectives from the plan's recorded decisions and tradeoffs; never invent disagreement merely for theater.

## Detail behavior

For each selected stage, reveal at most:

- the stage outcome;
- its key inputs and outputs;
- blocking dependencies;
- the most consequential risk or open decision;
- its success check.

Offer deeper implementation detail only after selection or when explicitly requested. If the surface can send a follow-up to Codex, make selected stages, risks, and decisions discussable.

## Quality gate

Before delivering, verify that:

- the visual can be understood without reading a duplicate paragraph;
- every major stage describes an outcome rather than vague activity;
- arrows encode real dependency or sequence, not decoration;
- parallel work, decision forks, and bottlenecks are visible when present;
- risk and uncertainty appear where they affect the route;
- labels stay identical across visual, narration, and details;
- the first view answers what changes, how it happens, and what could block it;
- no unsupported duration, owner, confidence, or metric was invented;
- the full result remains usable without audio or animation.

## Response discipline

Lead with the briefing rather than explaining how it was generated. Do not announce schemas, rendering tools, or implementation details. Do not include a format comparison unless the user is choosing a medium. Keep prose outside the visual concise and avoid restating visible information.
