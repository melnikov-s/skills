---
name: deep-dive
description: Use this skill when the user wants a complex explanation, plan, design, proposal, or problem-solving session delivered conversationally one chunk at a time. The chunked-conversation extension creates a lightweight outline, generates each chunk just in time, and lets the user discuss or steer each chunk before continuing.
disable-model-invocation: true
---

# Deep Dive

Use this skill for a chunk-by-chunk conversation rather than a long-form answer.

## Invocation

The user's request follows the skill command. Treat that request as the topic. If the chunked-conversation extension injected controller instructions, those instructions contain the canonical outline, active chunk, and durable decisions from earlier discussion.

## Rules

1. Follow the extension's active chunk exactly. Generate only that chunk.
2. Do not dump, preview, or prewrite the full answer or plan.
3. Generate each chunk just in time from the original request and the latest durable decisions.
4. When the controller requires `deep_dive_deliver`, finish all research and file inspection first, without narrating it or emitting a draft. Then call `deep_dive_deliver` exactly once as the final action, passing only the response body. Do not emit the numbered title yourself; the extension renders it.
5. Never call an item a “chunk” in user-facing text and never display the total number of planned items. The outline can change as the conversation develops.
6. Keep every internal chunk small and conversational: one short paragraph, or two short paragraphs at the absolute most. It should feel like one chat message from a colleague, never a mini-essay or several screens of text.
7. Each internal chunk covers one narrow idea, decision, or reasoning step. If the active objective is too broad, cover its first coherent unit and leave adjacent ideas for separate responses.
8. Avoid subsections, long lists, and extended examples inside one response. Use bullets or code only when indispensable, and keep them tiny.
9. For an explanation, teach one narrow idea at a time: one part of a mental model, mechanism, example, implication, or trade-off as directed by the active objective.
10. For a plan, work through one decision or reasoning step at a time. State only the assumptions, choice, and immediate consequences needed for that step.
11. Do not add boilerplate such as “say continue when ready.” The extension supplies the continue/discuss UI.
12. During a detour, answer only the user's current question or correction. Do not advance the outline or repeat the whole active item.
13. Treat durable summaries as authoritative. When they conflict with the original framing, follow the corrected assumption or decision.
14. Do not mention controller messages, hidden prompts, context collapse, or extension state.
15. Do not claim the deep dive is complete merely because the current item is the last one. The extension marks completion after the user accepts it.

## Without the Extension

If no controller instructions are present, briefly create an internal ordered outline, present only its first chunk, and stop. Continue one chunk at a time when the user asks. Keep any outline concise and do not expose it unless requested.
