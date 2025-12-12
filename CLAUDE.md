# QLever - Claude Code Project Guide

## Project Overview

QLever (pronounced "Clever") is a high-performance RDF graph database implementing the SPARQL 1.1 standard. It can efficiently query very large datasets with hundreds of billions of triples on commodity hardware.

**This is a fork of the upstream repository at `ad-freiburg/qlever`.**

## Important: Fork-Specific Instructions

- **All PRs should target this fork (`danbri/qlever`), NOT the upstream repository.**
- When creating pull requests, ensure the base repository is set to `danbri/qlever`.
- Do not submit PRs to `ad-freiburg/qlever` unless explicitly instructed.

## Repository Structure

```
src/           - Main C++ source code
test/          - Test files (mirrors src/ structure)
benchmark/     - Benchmark utilities
docs/          - Documentation
e2e/           - End-to-end tests
examples/      - Example files
misc/          - Miscellaneous utilities
```

## Build System

- **Build system:** CMake
- **Package manager:** Conan (see `conanfile.txt`)
- **Compiler requirements:** C++17 or later, GCC or Clang

### Building

```bash
# Standard build
mkdir build && cd build
cmake .. -DCMAKE_BUILD_TYPE=Release
make -j$(nproc)

# Run tests
ctest --output-on-failure
```

## Key Binaries

- `IndexBuilderMain` - For loading and indexing RDF data
- `ServerMain` - For running the SPARQL query server

## Code Style

- Uses `.clang-format` for C++ formatting
- Pre-commit hooks available (`.pre-commit-config.yaml`)
- Run format check: follow the format-check workflow

## Testing

- Unit tests in `test/` directory
- End-to-end tests in `e2e/` directory
- CI runs via GitHub Actions (see `.github/workflows/`)

## Dependencies

Key dependencies (managed via Conan):
- Boost
- ICU
- Various compression libraries

## Useful Links

- [QLever Wiki](https://github.com/ad-freiburg/qlever/wiki)
- [QLever CLI (qlever-control)](https://github.com/ad-freiburg/qlever-control)
- [Live demos](http://qlever.cs.uni-freiburg.de)
