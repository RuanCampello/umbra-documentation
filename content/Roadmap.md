---
title: Umbra Roadmap
---
# Umbra Project Roadmap

This roadmap outlines the components of each module, highlighting what has been completed and what is planned.

## Core Module

Responsible for all low-level storage, paging, and caching mechanisms.

- [-] Pager – Interface for reading and writing fixed-size pages to disk.
- [/] Cache – In-memory page buffer clock eviction policy.
- [x] Journal – Write-ahead log for atomicity and recovery.
- [x] Paging System – Disk layout abstraction with page tracking and pinning.
- [x] B*-Tree – Persistent tree structure for ordered data storage.

- [ ] Free-list Management – Track and reuse deallocated pages.
- [ ] Blob Storage – Support for multi-page variable-length values.
- [ ] Concurrency Control – Read/write isolation, possible MVCC or lock manager.
- [ ] Snapshots and Checkpoints – Safe view of the database for backups and recovery.

## SQL Module

Handles parsing, planning, and execution of SQL statements.

- [x] Tokenizer – Converts SQL input into token stream.

- [ ] Parser – Generates abstract syntax trees from tokens.
- [ ] Planner – Constructs logical query plans from ASTs.
- [ ] Execution Engine – Executes logical plans over the core storage layer.
- [ ] Expression Evaluation – Runtime for computing values, conditions, filters.
- [ ] Query Optimiser – Basic rules for reordering or transforming logical plans.
- [ ] Type System – Literal typing, column type declarations, and coercion.
- [ ] DDL Support – `CREATE`, `DROP`, and `ALTER TABLE` statements.
- [ ] Error Reporting – Structured diagnostic messages and SQL source spans.

## Testing & Tooling

Testing infrastructure and development utilities.

- [ ] Integration Tests – End-to-end system verification for correctness.
- [ ] Fuzzing – Automated mutation testing on tokenizer and parser.
- [ ] Benchmarks – Performance evaluation tools for inserts, reads, joins.
- [ ] CLI Tool – Interactive shell for entering SQL and viewing results.

## Exploratory Features

Ideas not on the main roadmap, but under consideration for future versions.

- [ ] Vector Search – Embedding-based k-NN indexing and querying.
- [ ] User-defined Functions – Custom scalar and aggregate extension points.
- [ ] Foreign Data Sources – Query across APIs, files, or external DBs.

## Influences

- SQLite 2.8 – Umbra’s foundational structure mirrors this version's pager and B-tree layering.
- Limbo (Turso) – Reference for modular SQL and modern design separation.
