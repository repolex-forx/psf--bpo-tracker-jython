# Repolex Knowledge Graph of psf/bpo-tracker-jython

RDF knowledge graph data for [psf/bpo-tracker-jython](https://github.com/psf/bpo-tracker-jython), parsed by [repolex](https://repolex.ai).

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
rlex download psf/bpo-tracker-jython
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 731b79d60ee2ae2df4fa24ecd0297e518466accd
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 731b79d60ee2ae2df4fa24ecd0297e518466accd
│           └── chunk-001.nq.gz
├── blob
│   ├── 07818e133c461e293017495edab811eb1389295b.nq.gz
│   ├── 10d36e6d4a2cd1bdd916911148dc91cd117a74a8.nq.gz
│   ├── 16fbff76fce56ef0ad81075c599fcfc40f6a55b6.nq.gz
│   ├── 19d2c2facf1471559b290f1c650925d849f13bc0.nq.gz
│   ├── 25a4f9997399188d7959ee7c82222d001f9b692b.nq.gz
│   ├── 269c5a55749b3648437338dc26b7b75d4b018bd0.nq.gz
│   ├── 270e480f2018be3629396abff84f6f94267bf28e.nq.gz
│   ├── 28ba88467461df6de936b27469162e727320332c.nq.gz
│   ├── 2e346231cf81ccd8a2711d49737c2fb1c3f19993.nq.gz
│   ├── 3d7c00e38d055a8b2ed74c98ac556799197af5be.nq.gz
│   ├── 4162d5ec670fe99e1cc8e163ad6a0fe34e9baa42.nq.gz
│   ├── 448cc2eef46a43f7909ec3622ad9649ba00a5026.nq.gz
│   ├── 4a93007ec44d6d75055fdb45bd0ea3b99b3d65e0.nq.gz
│   ├── 4e81138a2805ac66f95dbb9891e8e54ceff74e6d.nq.gz
│   ├── 576c997160cce366a140a4a5f391641409355768.nq.gz
│   ├── 758ad92f23749a0c54915202b1b231d21f6ca783.nq.gz
│   ├── 775b578673119beca5f712fd42f70918465f7aa6.nq.gz
│   ├── 7b62d79b2305f5abc5706d87873e7264c9c9af65.nq.gz
│   ├── 809d723722e4ad4e6fef64a58d4b91326800f09a.nq.gz
│   ├── 8239cdc6eaa799deb2c25efe202162cdbb80099e.nq.gz
│   ├── 8659c7f66b4fcff076361ac70c42cac138a7acda.nq.gz
│   ├── 8a52ddb3e6799e464fe6e7112243d8bd07a6e0fa.nq.gz
│   ├── 8e4606825e4f4bca251d8fd1bb1f84da3ef30265.nq.gz
│   ├── a0d704d5ff55cace25ed2f08796414502622d021.nq.gz
│   ├── b992f6d9ff6500efdbe807bedcdb8c831f139558.nq.gz
│   ├── c2db086531c96ec9adb3a0a736fe198950096bc9.nq.gz
│   ├── c9c0115da387dbaf87378208dee7f36d5df7c2fc.nq.gz
│   ├── cf355243fb1d57c877dcfcc6014d2447527f955b.nq.gz
│   ├── cfeceaacadb4d3fe8bb9dc5211000c26859c2426.nq.gz
│   ├── d8759303ee0b7759e6f936ab221cf3a03a50f560.nq.gz
│   ├── d908427037dcb0f087e47a74c12c66d60c1c26ac.nq.gz
│   ├── d90d51da74932c3449c60fd186c4cc5ac3311227.nq.gz
│   ├── eb9848e5a72f366ba03f54619912089b3eb4e661.nq.gz
│   ├── f1c3fd7432f2aa4803f5bd3f932e6fa1edd89399.nq.gz
│   ├── fbc9dd1a150ae1133b9dce38f82a80838f5329b0.nq.gz
│   ├── fdc7912bbbf0b54e08f91b97bfe228fed91dd744.nq.gz
│   └── ff4dff3bbf2c83706f4d44c491a83d5eb80acd09.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 731b79d60ee2ae2df4fa24ecd0297e518466accd.nq.gz
└── tag
    └── tag.nq.gz

11 directories, 43 files
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

[psf/bpo-tracker-jython](https://github.com/psf/bpo-tracker-jython)

---
*Parsed on 2026-10-11 by [repolex](https://repolex.ai)*
