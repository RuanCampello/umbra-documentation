---
title: Roadmap
---
This roadmap outlines the components of each module, highlighting what has been completed and what is planned.

## Core Module

Responsible for all low-level storage, paging, and caching mechanisms.


- [x] [[Pager]] – Interface for reading and writing fixed-size pages to disk

- [x] [[Cache]] – In-memory page buffer clock eviction policy.
- [x] [[Journal]] – Write-ahead log for atomicity and recovery.
- [x] [B*-tree](Btree) – Persistent tree structure for ordered data storage.
- [ ] Snapshots and Checkpoints – Safe view of the database for backups and recovery.

## SQL Module

Handles parsing, planning, and execution of SQL statements.

- [x] [[Tokenizer]] – Converts SQL input into token stream.

- [ ] [[Parser]] – Generates abstract syntax trees from tokens.
- [ ] Planner – Constructs logical query plans from ASTs.
- [ ] Query Optimiser – Basic rules for reordering or transforming logical plans.
- [ ] Error Reporting – Structured diagnostic messages and SQL source spans.

## Testing & Tooling

Testing infrastructure and development utilities.

- [ ] Integration Tests – End-to-end system verification for correctness.
- [ ] Fuzzing – Automated mutation testing on tokenizer and parser.
- [ ] Benchmarks – Performance evaluation tools for inserts, reads, joins.

## Exploratory Features

Ideas not on the main roadmap, but under consideration for future versions.

- [ ] Vector Search – Embedding-based indexing and querying.
- [ ] User-defined Functions – Custom scalar and aggregate extension points.

## Influences

- SQLite 2.8 – Umbra’s foundational structure mirrors this version's pager and B-tree layering.
- [Limbo](https://github.com/tursodatabase/limbo) (Turso) – Reference for modular SQL and modern design separation.
