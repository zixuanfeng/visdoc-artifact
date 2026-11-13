# VisDoc

VisDoc restructures open-source onboarding documentation into an interactive
task tree. This repository brings the React interface, Python generation
pipeline, saved example outputs, and research utilities into one code release.

## Repository layout

| Directory | Contents |
| --- | --- |
| [`frontend/`](frontend/) | React interface from `EPICLab/visdoc_framework/visdoc_react`. |
| [`backend/`](backend/) | Main Flask application and generation pipeline from `EPICLab/visual_doc_demo`. |
| [`backend/static/cached_results/`](backend/static/cached_results/) | Saved task-tree outputs for Transformers, Flutter, and Node.js. |
| [`backend/segmenter/`](backend/segmenter/) | Segmentation implementation and associated research files. |
| [`backend/test_segmenter/`](backend/test_segmenter/) | Segmentation evaluation scripts and ground-truth files. |
| [`legacy/openai-backend/`](legacy/openai-backend/) | Earlier experimental backend retained from `visdoc_framework`; not the backend used by the setup below. |
| [`docs/`](docs/) | Source provenance and preserved upstream documentation. |

Use `backend/app.py` together with `frontend/`. The frontend calls the backend
at `http://127.0.0.1:8080`; the React development server uses port 3000.

## Setup

Clone or download this repository. Run the following commands from its root,
using two terminals. The upstream backend README specifies Python 3.9.6; the
frontend uses React 18.3.1 and requires Node.js with npm. The original dependency
lists and frontend lockfile are preserved.

### 1. Start the backend

```bash
cd backend
python3 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt

export OPENAI_API_KEY='your-openai-api-key'
export GITHUB_TOKEN='your-github-token'

python app.py
```

On Windows PowerShell, activate with `.venv\Scripts\Activate.ps1` and set the
variables with `$env:OPENAI_API_KEY='...'` and `$env:GITHUB_TOKEN='...'`.

The generation pipeline uses OpenAI APIs and GitHub's API. The current GitHub
client includes the supplied token in its request headers. Use your own
credentials and keep them out of Git. Generation may incur API charges and may
download NLP resources or model weights. Inspecting the saved JSON outputs
does not require API credentials or API calls.

Start the backend from the `backend/` directory: its research code uses relative
paths for model files, downloaded documents, and generated outputs.

### 2. Start the frontend

In a second terminal, from the repository root:

```bash
cd frontend
npm ci
npm start
```

Open `http://localhost:3000`.

### 3. Inspect an example or generate a tree

The existing interface loads saved outputs when a submitted link contains
`transformers` or `flutter`. For example, submit:

```text
https://github.com/huggingface/transformers/blob/main/CONTRIBUTING.md
```

Other links are sent to `/fetch_and_analyze` for generation. Use a GitHub file
URL that identifies the contributing document. These behaviors are inherited
from the original interface; consolidating the repositories does not regenerate
the saved materials or change the generation method.

The backend also includes an earlier Flask-rendered interface. The React
application above is the main task-tree interface in this consolidated release.

## Research files and scope

- [Transformers saved output](backend/static/cached_results/transformers.json)
- [Flutter saved output](backend/static/cached_results/flutter.json)
- [Node.js saved output](backend/static/cached_results/node.json)
- [Segmentation evaluation files](backend/test_segmenter/)
- [Segmentation implementation](backend/segmenter/)
- [Prompt definitions](backend/code_from_visdoc/prompts_store.py)

The classifier, experimental scripts, source-document snapshots, and saved
generation outputs are retained in their original relative locations. This
keeps the code and data available for inspection without reorganizing the
pipeline internals.

The frontend checks for optional walkthrough videos under
`frontend/public/assets/videos/<repository>/<video-title>.mp4`. Those video
files were not present in the two source snapshots. This consolidation does not
add a recording or narration service or provide new video assets.

## Provenance and validation

The application code and research assets were imported without modification.
The consolidation adds a shared README and directory structure, preserves the
earlier backend separately, and resolves two upstream README names that differ
only in capitalization. See [source provenance](docs/ORIGINS.md) and the
[file manifest](docs/source-manifest.json) for source commits and checksums.

This is an artifact-organization revision. The original dependency versions are
retained; a successful file-integrity or syntax check does not establish that
the full generation pipeline runs on every current environment. Validation
performed for this release is recorded in [VALIDATION.md](docs/VALIDATION.md).

## Licensing and attribution

Both source repositories identify their code as MIT-licensed in their READMEs;
those declarations are preserved under [docs/upstream/](docs/upstream/).
Existing third-party notices, including the
[segmentation license](backend/segmenter/LICENSE), are retained. Copied project
documentation and other third-party material retain their original notices.
Source histories and contributor records remain available through the original
repository links in [ORIGINS.md](docs/ORIGINS.md).
