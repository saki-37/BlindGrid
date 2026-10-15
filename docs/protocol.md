# Protocol and retained history

This note summarizes the paper's task and evaluation protocol and the archived implementation used for prompt reconstruction. The [prompt index](prompts/README.md) provides the complete initial system instructions and their provenance.

## Observations, movement, and budgets

Grid dimensions are reported as columns × rows. At each step, the model sees its current patch and chooses `UP`, `DOWN`, `LEFT`, `RIGHT`, or `ANSWER`. An accepted move reveals an adjacent patch. Earlier observations are retained as text, and the model receives no global image view during sequential exploration.

| Grid | Number of patches | Step budget |
|---|---:|---:|
| 4 × 3 | 12 | 30 |
| 5 × 6 | 30 | 45 |

One step includes an observation and an action decision. In the archived executor, invalid actions and rejected boundary moves consume a step without changing position. Boundary feedback can provide the current coordinates and grid bounds. An accepted `ANSWER` on the last permitted step counts as answered.

## Five prompt and history settings

| Setting | Instruction and output features | Retained-history presentation |
|---|---|---|
| `minimal` | Free-text actions or an explicit `ANSWER:`. Initial instructions include the grid and total budget. | Full previous assistant responses in conversation, with earlier images replaced by text placeholders. |
| `baseline` | Structured observation, action, and answer fields, with basic exploration and memory-integration instructions. | Structured memory entries. |
| `efficient` | Answer-when-ready instructions, plus `edge_status`, `relevance`, and `key_info`. | Structured memory entries. |
| `spatial_cot` | Explicit spatial reasoning and the efficient setting's extra fields, plus `reasoning`. | Structured memory entries. |
| `freetext_memory` | Answer-when-ready instructions and `edge_status`. Its output schema omits `relevance` and `key_info`. | Memory entries rendered as a text list with coordinates. |

All four engineered settings routinely receive current coordinates and step numbers. Minimal omits those routine fields, while boundary-rejection feedback can still reveal coordinates.

For engineered settings, the archived memory-extraction rule selects nonempty `memory`, otherwise `key_info`, otherwise the first 300 characters of `observation`. All nonempty entries accumulate. The 300-character limit applies to that observation fallback. Explicit memory, key information, and minimal's conversation history use their respective retention rules above.

The prompt files preserve legacy wording. Baseline and freetext_memory mention automatic saving of `relevance` and `key_info` even though those fields are absent from their output schemas. Efficient and spatial_cot instruct that only YES/MAYBE-relevant patches are saved, while the archived executor applies the field-based extraction rule without enforcing that relevance filter. These differences matter when interpreting a trajectory.

## Evaluation groups

The main evaluation combines five models, five prompt settings, two grids, three repetitions, and ten questions about two artworks, giving 1,500 attempts. The requested model aliases are `gpt-5.4`, `claude-sonnet-4-6`, `gemini-3-flash-preview`, `qwen3-vl-30b-a3b-instruct`, and `grok-4.1`. These are requested API identifiers. Immutable upstream model versions are not established for all saved attempts.

The 360 visual-control episodes cross ten questions, GPT and Claude, two grids, three repetitions, and three conditions:

- **Real:** sequential local views with the baseline prompt.
- **Blank:** same-sized black images, with the question and navigation protocol preserved.
- **Oracle:** selected target and context patches presented together with coordinates and a direct-answer instruction. The reference answer remains evaluator-only.

Oracle changes evidence selection, simultaneous presentation, memory demands, and answer instructions together.

The additional-image evaluation compares baseline and minimal using GPT and Claude on 16 questions across five further images. One run per model, question, and prompt gives 64 episodes, using a 4 × 3 grid and a 30-step limit.

## Answers and execution outcomes

Answer quality is the primary outcome. Semantic correctness and executor acceptance are recorded separately: an explicit answer can be semantically correct even when the historical executor did not accept an `ANSWER` action. Technical failures have missing semantic labels and are included in all-attempt denominators. Paired comparisons use their stated complete groups.

The scored-record release will include the final item-specific rubric, outcome fields, and exact group membership. The present note supplies context for reading the initial prompt exports.
