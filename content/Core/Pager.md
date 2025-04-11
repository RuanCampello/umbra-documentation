---
tags:
  - pager
  - file
  - io
---
The [[Pager]] abstracts away the complexity of:
- Reading and writing [pages](Page);
- Managing the in-memory [[Cache]];
- Handling [commits](commit) and [rollbacks](rollback) from a given [[Journal]].

```rust
pub(crate) struct Pager<File> {
    file: BlockIo<File>,           // Low-level I/O interface (read/write).
    block_size: usize,         // Filesystem block or I/O buffer size.
    pub page_size: usize,          // Logical page size used by the database.
    cache: Cache,                  // In-memory page cache.
    dirty_pages: HashSet<PageNumber>, // Pages that have been modified in memory.
    journal: Journal<File>,           // Journal used for transactional safety.
    journal_pages: HashSet<PageNumber>, // Tracks what has been backed up.
}
```
