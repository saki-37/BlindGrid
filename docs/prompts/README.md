# Initial system-prompt exports

Ten complete UTF-8 exports cover five settings and two grids. Files retain the bytes of the prepared exports, including Unicode arrows and warning symbols. Each digest matches the preserved [export manifest](prompt_manifest.json).

| Setting | 4 × 3 grid, 30 steps | 5 × 6 grid, 45 steps |
|---|---|---|
| minimal | [Prompt](minimal_4x3_initial_system.txt) | [Prompt](minimal_5x6_initial_system.txt) |
| baseline | [Prompt](baseline_4x3_initial_system.txt) | [Prompt](baseline_5x6_initial_system.txt) |
| efficient | [Prompt](efficient_4x3_initial_system.txt) | [Prompt](efficient_5x6_initial_system.txt) |
| spatial_cot | [Prompt](spatial_cot_4x3_initial_system.txt) | [Prompt](spatial_cot_5x6_initial_system.txt) |
| freetext_memory | [Prompt](freetext_memory_4x3_initial_system.txt) | [Prompt](freetext_memory_5x6_initial_system.txt) |

## Provenance and use

These are initial system-prompt reconstructions exported from the available code snapshot, with empty history and a starting coordinate of `(0, 0)`. The engineered settings show the first decision, including the valid moves and boundary information for that position. The two grid versions substitute the grid dimensions, coordinate bounds, and total step budget.

The main evaluation preserves responses, actions, coordinates, and histories for 1,420 nonfailed trajectories. Complete original request messages are unavailable for all attempts. The exports therefore document the recoverable implementation and initial wording, rather than certify the exact request text for every historical run.

A complete interaction also supplies the question, current image, subsequent messages, and retained history. Engineered settings update position, step, and memory fields. Minimal uses a fixed system instruction plus conversation history. Consult the [protocol notes](../protocol.md) for the history rule and boundary-feedback behavior.

The exports preserve legacy instruction/schema differences discussed in the paper. Their wording has not been rewritten to match the archived executor's field-based memory extraction. This allows readers to examine the original instructions alongside the implementation description.

## Integrity

`prompt_manifest.json` lists the SHA-256 digest of each text file. Recompute a file's SHA-256 digest and compare it with its entry to check that the downloaded bytes match this export. The root [release manifest](../../release_manifest.json) also records these files and the accompanying documentation.
