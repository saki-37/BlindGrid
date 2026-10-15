# Repository organization

The initial public release contains the following files:

```text
BlindGrid/
├── README.md
├── README_zh.md
├── release_manifest.json
└── docs/
    ├── STRUCTURE.md
    ├── protocol.md
    └── prompts/
        ├── README.md
        ├── prompt_manifest.json
        └── <setting>_<grid>_initial_system.txt  (ten files)
```

## Planned material groups

| Location | Planned content | Reader use |
|---|---|---|
| `docs/scoring.md` | Final rubric, answer labels, execution outcomes, denominators, and paired-group definitions | Understand how answers and summaries are evaluated |
| `docs/image_sources.csv` | Exact sources and versions for seven images, access routes, dimensions, hashes, and crop/grid information | Identify and reconstruct the image inputs where supported |
| `docs/reuse.md` | Data and image attribution and reuse terms | Check the applicable terms for each material group |
| `reproducibility/` | Complete existing offline bundle, including its own README, questions, records, trajectories, tools, and reference outputs | Recompute the supported summaries from saved data |
| `analyses/` | Verified final-paper sensitivity comparisons beyond the bundle's coverage | Trace additional comparisons to their inputs and outputs |
| `figures/` | Figure sources and supporting assets selected for distribution | Follow per-figure input and build instructions |
| `paper/` | Final clean PDF and paper-to-material version mapping | Read the paper corresponding to the material release |
| `CITATION.cff` | Final paper and repository citation | Cite the work |
| `LICENSE` | Selected repository licensing terms | Identify the code reuse terms |

These planned entries will be added when their contents are ready. The root README tracks availability.

## Preserve the offline bundle's internal structure

The prepared offline bundle will be imported as a complete `reproducibility/` directory. Its own README, relative paths, reference outputs, and integrity manifests will remain together. Analyses and figure scripts will use documented paths to those records.

The prompt files already published under `docs/prompts/` provide an early reading entry point. When the full bundle arrives, its corresponding exports will be checked for byte equality and their relationship documented. The bundle will remain the source for scored records.

## Connect cases and figures to saved episodes

Each illustrative case will identify its saved episode and the relevant steps. The three owl trajectories will have separate entries, and the baseline episode reused across figures will keep the same identity. Figure notes will distinguish the annotated reader reference from the patches shown to the model.

## Image source information

The source table will cover The Garden of Earthly Delights, The Tower of Babel, Crosswalk, The Coronation of Napoleon, The Last Supper, Dulle Griet, and Land O'Lakes. It will record exact source titles and versions from the saved assets and their provenance.

Each row will specify an image identifier, attribution, source page, exact version or download reference, dimensions, file hash, crop/grid description, access route, and applicable reuse terms. Exact source identification is particularly important for names such as Crosswalk and Land O'Lakes.

## File verification

The root `release_manifest.json` lists all distributed files except itself, with their byte counts and SHA-256 hashes. The prompt directory also preserves the original export manifest. Subsequent material releases will update these records and report which offline computations and figure-generation steps have been verified.
