# Repolex Knowledge Graph of simonw/yaml-to-sqlite

RDF knowledge graph data for [simonw/yaml-to-sqlite](https://github.com/simonw/yaml-to-sqlite), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [rlex](https://github.com/repolex-ai/rlex) query tool:

```bash
cargo install --git https://github.com/repolex-ai/rlex
```

Verify the install:

```bash
rlex --help
```

**rlex is designed to be used primarily by LLMs in a terminal.** Start up your favorite AI assistant and ask it to use rlex. It handles the SPARQL — you just ask questions in plain English.

To load this repo's data:

```bash
rlex download simonw/yaml-to-sqlite
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 1405bc83c8f2d4d8cd772ccacc340754f22b153e
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 1405bc83c8f2d4d8cd772ccacc340754f22b153e
│           └── chunk-001.nq.gz
├── blob
│   ├── 097151e5be4603c5b416537ff691b0ef4db0473a.nq.gz
│   ├── 15a81eb104027fd2d8a2be6d4514cb68ad80e777.nq.gz
│   ├── 261eeb9e9f8b2b4b0d119366dda99c6fd7d35c64.nq.gz
│   ├── 7137aa5dc92dd5547e3ba14e655c6c8c6f0f9eae.nq.gz
│   ├── a3b51aa4e08b5f1a471c8dadcc704a44d1fa9270.nq.gz
│   ├── bcf099bcdef2830e9ca0b59daf78d0f6fb2902e8.nq.gz
│   ├── df13fc50cb3419b8c0ea7e72f69adc478bd3f2e9.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   └── ee09230f7298246c3ded0925f027e7187e025069.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 1405bc83c8f2d4d8cd772ccacc340754f22b153e.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 17 files
```

| Directory | What it contains |
|-----------|-----------------|
| `blob/` | Per-file AST graphs, content-addressed by git blob SHA. Each file in the source repo gets its own graph. |
| `aggregate/ast/` | Combined AST graph per parsed commit. Merges all blob graphs for a snapshot of the entire codebase at that point. |
| `aggregate/lsp/` | Language Server Protocol enrichment: resolved symbols, definitions, references, and type information. |
| `aggregate/dataflow/` | Interprocedural data flow edges between functions and modules. |
| `aggregate/repolex/` | Combined graph (AST + LSP + dataflow) per commit. |
| `commit/` | Git commit metadata (author, date, message, parent links). |
| `branch/` | Branch metadata. |
| `tag/` | Tag metadata. |
| `filetree/` | File tree snapshots per commit (which files existed and their blob SHAs). |
| `audit/` | Code architecture and graph audit reports per commit. |

## Source repository

[simonw/yaml-to-sqlite](https://github.com/simonw/yaml-to-sqlite)

---
*Parsed on 2026-10-15 by [repolex](https://repolex.ai)*
