# Repolex Knowledge Graph of holoviz/pyviz_comms

RDF knowledge graph data for [holoviz/pyviz_comms](https://github.com/holoviz/pyviz_comms), parsed by [repolex](https://repolex.ai).

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
rlex download holoviz/pyviz_comms
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 666f04709f8935f26b1beba6a79189dd17f929ea
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 666f04709f8935f26b1beba6a79189dd17f929ea
│           └── chunk-001.nq.gz
├── blob
│   ├── 056e50aef0e45019fb135bbeafee52f4f5d4a161.nq.gz
│   ├── 07e26e1ff64364ad94d0d9cd47f24e97f412bb3c.nq.gz
│   ├── 0b84196d99af1999e202b57da4a71d09752444fa.nq.gz
│   ├── 0e2c80b6ad3ca058a725ba3888e2f156f1861463.nq.gz
│   ├── 123f1ca433f5dcaf7ff61022bc2dce9dc41572d8.nq.gz
│   ├── 2bf8096d4810842cd0bdf8cd1d1bee0275669bf2.nq.gz
│   ├── 3ea8dcd0c8dcc80285894790e6cd96769285a3b8.nq.gz
│   ├── 47b99b5d8dc4bf43bfd1f40f338df891b794af38.nq.gz
│   ├── 480d8f81edf4c68d6b1de9798c6d418bb5fee3d9.nq.gz
│   ├── 4f2539d12101f31a1c8599f267c82cd2d350bf6f.nq.gz
│   ├── 523d0884e2641d75018fcfd7440600d8f85bf9e6.nq.gz
│   ├── 5ce204dc3271544eea9fe057083f86aacc593259.nq.gz
│   ├── 5edd091c088b6bbd0d40258e66235d4185dd5189.nq.gz
│   ├── 656d70258509560229e00a01de00457267245177.nq.gz
│   ├── 6b410cf85dad42c4bf2e9b5a6428b5140ca7250e.nq.gz
│   ├── 750e48638022e5430f75b6e0fe07e627548a180c.nq.gz
│   ├── 756d2bf9b60241ef62824f292c00bee2df85999e.nq.gz
│   ├── 7e8a99237bea70eff264ed7f5412f92bef5a0c79.nq.gz
│   ├── 7f2312f2a5bcc050686f3c299cbfb490ba580992.nq.gz
│   ├── 8a7ea29e69487a93c256fee6e15adfd533a53280.nq.gz
│   ├── 9348424371fbfb6442044950595b405e9434b4af.nq.gz
│   ├── a028a76408bf46181259249b2e15e14a9bbdf7f1.nq.gz
│   ├── a4d7a35771b9bd62ec18fe44346f2585819b1a64.nq.gz
│   ├── a80ec92e910d327494e883dc9bf2051efd846f23.nq.gz
│   ├── a98b3e217976f07bad68bb8223a2da78466cbe6c.nq.gz
│   ├── aa14c0c21620c74b6f893319767c56dcfb371a9b.nq.gz
│   ├── b0a179d48cb8c6e34f32db884031dfcd89122782.nq.gz
│   ├── bbee47dc3569250bfcb2c53391d9544e466705e4.nq.gz
│   ├── c7ed366d781205a8cce62913ed17218a8be55862.nq.gz
│   ├── ca3e04ba35e65efb83b0be7e87412d43ad4c3884.nq.gz
│   ├── df069e0179b418374d15bc90c99fddea7945eff5.nq.gz
│   ├── e07858d6464dda2b40c99c815d918b6b15916e9f.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── f57e6edb833f6870ef3b249bece1bbd14db9f389.nq.gz
│   ├── f624857377640ca13898473232ec0fcfe56a3ab1.nq.gz
│   └── fe1125f54b574ada4e48f2400826953264cab511.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 666f04709f8935f26b1beba6a79189dd17f929ea.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 44 files
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

[holoviz/pyviz_comms](https://github.com/holoviz/pyviz_comms)

---
*Parsed on 2026-10-16 by [repolex](https://repolex.ai)*
