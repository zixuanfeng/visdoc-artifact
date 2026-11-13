# Source provenance

This artifact was assembled on 12 November 2026 from these public repository
snapshots:

| Source | Commit | Destination |
| --- | --- | --- |
| [EPICLab/visdoc_framework](https://github.com/EPICLab/visdoc_framework) | [`3ca9ea2f9a2ec1b3b2b87646f0c2e7ada7b45613`](https://github.com/EPICLab/visdoc_framework/commit/3ca9ea2f9a2ec1b3b2b87646f0c2e7ada7b45613) | `visdoc_react/` → `frontend/`; `backend/` → `legacy/openai-backend/` |
| [EPICLab/visual_doc_demo](https://github.com/EPICLab/visual_doc_demo) | [`375058169f33df563349f35d3231187526efba37`](https://github.com/EPICLab/visual_doc_demo/commit/375058169f33df563349f35d3231187526efba37) | Repository contents → `backend/` |

The source histories, original authorship, issues, and pull requests remain in
the original repositories. This release imports their tracked file snapshots;
it does not claim to migrate their complete Git histories or issue trackers.

## Packaging changes

- One top-level README explains both components and their connection.
- New component READMEs point to the shared setup instructions.
- Original README files and the framework's root ignore file are preserved
  under `docs/upstream/`.
- The two backend README names, which differ only in capitalization, have
  distinct descriptive filenames under `docs/upstream/`.
- The earlier experimental backend is retained under `legacy/openai-backend/`.
- macOS `.DS_Store` files are omitted. No application code, prompts, model
  files, ground truth, or cached generation outputs are otherwise removed.
- A shared `.gitignore` excludes local credentials, environments, dependencies,
  and build products from future commits.

[source-manifest.json](source-manifest.json) maps every imported file to its
original path, Git blob ID, byte size, and SHA-256 checksum. It also records
omitted Finder metadata. All original license notices are preserved.
