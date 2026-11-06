# ContextForge application fixture

This repository contains the RAG application and evaluation configuration used by the ContextForge service demo. Install the ContextForge GitHub App on this repository to receive pull request checks.

## Contents

- `sample-rag-app/` — reference RAG application and Docker Compose stack
- `contextforge.gemini.yml` — evaluation config for Gemini
- `contextforge.yml` — evaluation config for OpenAI
- `contextforge.local-judge.yml` — local judge example
- `benchmark/` — frozen evaluation cases and sample baselines

The sample app is a reference implementation. Replace it with your RAG application while keeping the ContextForge app contract: `GET /health` and `POST /query` returning an answer and retrieved contexts. Update `contextforge.yml` to point at your Compose file, service, dataset, judge and thresholds. Keep API keys in environment variables; never commit them to these YAML files.

## Local validation

From the ContextForge service checkout, install and build the CLI, then validate a config in this repository:

```sh
pnpm install --frozen-lockfile
pnpm build
node pipeline/packages/cli/dist/bin.js validate --config /path/to/ContextForge-application/contextforge.gemini.yml
```

For the local GitHub App demo, configure the service checkout's `.env` with this repository name and its absolute local path. See the service repository README for the full setup.
