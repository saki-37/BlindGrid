# BlindGrid

**Diagnosing Visual Evidence Acquisition and Binding under Local Observation**

Jiazheng Liu, Wanpeng Zhang, and Zongqing Lu  
COLM 2026 Workshop on Efficient Reasoning · [OpenReview record](https://openreview.net/forum?id=MjJALedynI) · [中文说明](README_zh.md)

BlindGrid studies how multimodal large language models acquire and use visual evidence when they can see only one image patch at a time. A model moves between adjacent grid cells, retains observations as text, and decides when to submit an answer. Recorded trajectories connect answer quality to the regions visited, information retained, and attributes or relations assigned to the queried target.

## Available materials

**Initial public release: documentation and prompt exports.** Materials will be added progressively, with this table tracking what is available.

| Material | Status and entry point |
|---|---|
| Repository organization | Available: [directory guide](docs/STRUCTURE.md) |
| Protocol and history-retention notes | Available: [protocol](docs/protocol.md) |
| Ten complete initial system-prompt exports | Available: [prompt index and provenance](docs/prompts/README.md), covering five settings and two grids |
| File integrity information | Available: [release manifest](release_manifest.json) and [prompt hashes](docs/prompts/prompt_manifest.json) |
| Questions, references, and final scoring rules | Planned |
| Scored records, trajectories, and offline aggregation tools | Planned |
| Additional sensitivity analyses and figure sources | Planned |
| Exact image sources, access information, and patch metadata | Planned |
| Final paper PDF and citation file | Planned; the submission record is linked above |

The prompt files are byte-preserved exports from the available code snapshot. They reconstruct initial instructions and retain their original wording. Their [provenance notes](docs/prompts/README.md#provenance-and-use) explain how they relate to saved runs and subsequent messages.

## Evaluation scope

| Evaluation | Scope in the paper | Purpose |
|---|---|---|
| Main evaluation | 1,500 attempts on ten questions about two artworks | Compare models, prompt and history settings, and grid configurations |
| Visual controls | 360 episodes using Real, Blank, and Oracle conditions | Examine outcomes with sequential local views, black images, and selected patches |
| Additional images | 64 episodes on 16 questions about five further images | Compare baseline and minimal prompts on additional questions |

Answer quality is the primary outcome. Execution status, steps, and resource use provide complementary information. The complete material release will identify the denominator and comparison-group membership for each reported summary.

## Getting started

1. Read the [protocol](docs/protocol.md) for observations, actions, budgets, and retained history.
2. Compare the five settings using the [prompt index](docs/prompts/README.md).
3. Consult the [directory guide](docs/STRUCTURE.md) for the remaining material groups and their planned locations.

The offline bundle will be added as a complete directory, preserving its internal paths and integrity checks. Verified commands and expected outputs will accompany it. The current release supports inspection of the protocol and initial prompts. Dataset-level recomputation becomes available when the saved records and tools are added.

## Reproduction scope

The planned offline release will support recomputation from saved records without model API access. Its prepared starting bundle covers the main evaluation, control comparisons, additional-image summaries, and Figure 2 data and plotting source. The published copy will receive its own verification against the final paper.

Fresh model runs form a separate workflow whose outcomes depend on model availability and stochastic sampling. Initial prompts, subsequent messages, history construction, image preprocessing, and execution rules all contribute to an interaction.

## Image sources and reuse

Image source and patch metadata will be added with exact source or version references, attribution, crop information, and access routes. The initial release contains text documents and prompt exports. Any future image assets and figure crops will have their applicable attribution and reuse terms recorded alongside them.

Repository licensing terms are pending. Code, data, and third-party image terms will be stated explicitly as the material release is completed.
