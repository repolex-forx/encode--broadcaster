# Repolex Knowledge Graph of encode/broadcaster

RDF knowledge graph data for [encode/broadcaster](https://github.com/encode/broadcaster), parsed by [repolex](https://repolex.ai).

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
rlex download encode/broadcaster
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 6b3ea71d4f8fb038fa7d357a1fb3750d58ac614d
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 6b3ea71d4f8fb038fa7d357a1fb3750d58ac614d
│           └── chunk-001.nq.gz
├── blob
│   ├── 0015d3989d8b0e5ec92b75bf1b4e36d5d56f20ca.nq.gz
│   ├── 013870bfb16f4c1158927af96d937be99c3ba3cc.nq.gz
│   ├── 069d9785b01baf12a457b0811bcb32f6a0d1aa60.nq.gz
│   ├── 188ffaed1ebc431e25e97eb8ce441781401ae42d.nq.gz
│   ├── 2f87d94ca10327497ac0f4c0093930826ff76642.nq.gz
│   ├── 311b2b56c53f678ab95fc0def708c675d521a807.nq.gz
│   ├── 3ea8eef0c22f8ccc90981ede3a92d42430c9bb88.nq.gz
│   ├── 3ee97d21e8659445dac0b4f948bec77fec9ced73.nq.gz
│   ├── 400f43f9ce52d1767eda6431a6a307210ff6ec6b.nq.gz
│   ├── 44835e5554ebe70b118e8c9e7652f43724cb9a2b.nq.gz
│   ├── 4d414601c777f0ff6ff892babe8b08959c9a84d2.nq.gz
│   ├── 5d5e71a13f81d68d679bb33818c38cd9530f7986.nq.gz
│   ├── 60073b42f90705d413a45c36e5354e27b775f015.nq.gz
│   ├── 65885a7208961207ed34c9659c21ac5ef0b90314.nq.gz
│   ├── 7017df3d1b79f154f0bb0bed34476a3542f1ae5a.nq.gz
│   ├── 77699625ef4a71c011720b14ea5f73477995fc2d.nq.gz
│   ├── 81db76157adf64d27ffe357f6390558a5f3e7753.nq.gz
│   ├── 959b34d91539a12ed37eb57ff072e93623fcbbdb.nq.gz
│   ├── a201221e7b7a76d9adcf8d110aeb573e94a85e35.nq.gz
│   ├── a63b22bf4138c79a6a3a3575b5f11e8f277da215.nq.gz
│   ├── ae894019d762ee89af98cf3f33d802999c33f525.nq.gz
│   ├── b88b317559d749e30f4bdb92b079e7a23c7a037a.nq.gz
│   ├── bfd0c44d38f82c8d5ae1da5740001385e5c2f3c2.nq.gz
│   ├── c4e80369893bb85101636bd9b3af80bef85167d1.nq.gz
│   ├── cb718d0d7593cc04250699970ce2b9acc5a354cf.nq.gz
│   ├── d8fb02b06b5c93a1f4f8c8244d11bba97a4023e8.nq.gz
│   ├── dea001f490180a7dea92d1f55e4146d48efc897c.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── ed2926b5340a80503a25b5ab584bbbdce71f529d.nq.gz
│   ├── effb166ea975ae1ba6abc4c4bb3190858b37246e.nq.gz
│   ├── f09dca14a3ce36a9e59c0c48173fd2e3ea6aa249.nq.gz
│   └── f7f32ad12bb044c3c2992089f52c9ccd0a3dfbbe.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 6b3ea71d4f8fb038fa7d357a1fb3750d58ac614d.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 40 files
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

[encode/broadcaster](https://github.com/encode/broadcaster)

---
*Parsed on 2026-10-15 by [repolex](https://repolex.ai)*
