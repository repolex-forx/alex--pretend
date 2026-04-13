# Repolex Knowledge Graph of alex/pretend

RDF knowledge graph data for [alex/pretend](https://github.com/alex/pretend), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [lexq](https://github.com/repolex-ai/lexq) query tool using [uv](https://docs.astral.sh/uv/getting-started/installation/).

If you have uv installed, just copy/paste this into your terminal:

```bash
uv tool install git+https://github.com/repolex-ai/lexq
```

This installs lexq onto your system, in your user context. Verify the install:

```bash
lexq --help
```

**lexq is designed to be used primarily by LLMs in a terminal.** Start up your favorite LLM and ask it to use the lexq tool. It's that easy!

To load this repo's data:

```bash
lexq download alex/pretend
```

This will automatically download essential data files from the last parsed commit. Consult `lexq --moreinfo` for other options, including downloading multiple commits, blobs, etc.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── e7f26ad7dbcb4a02a4995aade4743aad47656b27
│   │       └── chunk-001.nq.gz
│   ├── lsp
│   │   └── e7f26ad7dbcb4a02a4995aade4743aad47656b27.nq.gz
│   └── repolex
│       └── e7f26ad7dbcb4a02a4995aade4743aad47656b27
│           └── chunk-001.nq.gz
├── blob
│   ├── 1fc2ee40cb0662aafb518154df9679c812737340.nq.gz
│   ├── 398ff08afa472330844404ccef1b7d49fcc17c5e.nq.gz
│   ├── 4745674ab7c6862a62359937144c5a1a23d01e25.nq.gz
│   ├── 5e4090017a9bec5de60a745d17007a9e95f31a43.nq.gz
│   ├── 74c99f73341f35e4039e1e9715fa0ed34cb5b8d7.nq.gz
│   ├── 888e189052ed6668264bc3457627d0ce942e72d1.nq.gz
│   ├── aaa94d58ef441f09bf64a392dc25f64fac8c4134.nq.gz
│   ├── ab78160072ef1b88e827fd36445241e4bf04d654.nq.gz
│   ├── b03f0a14513258259bbfba0d60d3e0954a5f7769.nq.gz
│   ├── c6d1cd6a549625307a539405579fb0ec15f2bc33.nq.gz
│   └── fb65fe1326e268505a91efd56cc4eb158169d1b6.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── dep
│   └── e7f26ad7dbcb4a02a4995aade4743aad47656b27.nq.gz
├── filetree
│   └── e7f26ad7dbcb4a02a4995aade4743aad47656b27.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

15 directories, 21 files
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

## Source repository

[alex/pretend](https://github.com/alex/pretend)

---
*Parsed on 2026-04-13 by [repolex](https://repolex.ai)*
