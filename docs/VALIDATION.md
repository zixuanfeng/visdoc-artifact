# Consolidation validation

Checked on 12 November 2026.

| Check | Result |
| --- | --- |
| Imported source-file integrity | All 733 imported files match their source-snapshot SHA-256 checksums. |
| Application changes | No imported application code, prompts, model files, or research assets changed. |
| Case-insensitive checkout | No destination filenames collide after case folding. |
| Python syntax | All 76 imported `.py` files parse under Python 3.12. This does not execute them or verify their dependencies. |
| Frontend dependency metadata | `package.json` dependencies match the root dependencies in the original `package-lock.json`. |
| Saved outputs | Transformers, Flutter, and Node.js JSON files parse and contain both `content` and `flow`. |
| New documentation links | Relative links in the new README and provenance documentation resolve. |

## Not exercised during consolidation

The full Python dependency installation, React build, live generation pipeline,
external API calls, model downloads, multimedia generation, and end-to-end
interface behavior were not run. This release reorganizes the existing research
artifact; it does not claim new runtime validation or a new evaluation study.

The original repositories are linked in [ORIGINS.md](ORIGINS.md). Imported-file
checksums are recorded in [source-manifest.json](source-manifest.json).
