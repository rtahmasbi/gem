# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**GEM** (Golang, Bazel, Gazelle) — a multi-language Bazel monorepo with Go and Python components. Go module: `github.com/rasooltahmasbi/gem`, Go 1.25.

## Build System

This repo uses **Bazel** as the primary build system with Gazelle for BUILD file generation.

```bash
# Run a component
bazel run //opal:opal
bazel run //quartz:quartz

# Build
bazel build //...

# Test
bazel test //...

# Regenerate BUILD files after adding/moving Go or Python files
bazel run :gazelle

# Update Python requirements lock file
bazel run :requirements.update

# Validate requirements lockfile is in sync
bazel test :requirements_test
```

## Architecture

Monorepo with language-specific subdirectories, each as an independent Bazel target:

- **`opal/`** — Go application (`go_binary`)
- **`quartz/`** — Python application (`py_binary`)
- **`amber/`** — Reserved, currently empty

Go dependencies (declared in `go.mod`, resolved by Bazel/Gazelle) include extensive cloud SDKs: Google Cloud (BigQuery, Cloud SQL, Pub/Sub, Secret Manager, etc.) and AWS (Lambda, DynamoDB, S3, Bedrock, etc.), plus gRPC/protobuf and CEL.

## Key Conventions

- After adding Go imports or new `.go`/`.py` files, run `bazel run :gazelle` to update `BUILD.bazel` files — do not edit them manually.
- Python dependencies go in `requirements.txt`; run `bazel run :requirements.update` after changes to regenerate the lock file.
