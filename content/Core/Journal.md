The [[Journal]] structure is responsible for logging changes to database pages, enabling [[commit]], which applies the changes to the database and [[rollback]], that enables rolling back changes if something goes wrong. 

The journal `File` stores the snapshots of the database pages *before* they're modified. This workflow is heavily inspired by [SQLite 2.8.1](https://sqlite.org/src/dir?name=src&ci=590f963b6599e4e2) way of doing thing, but simplified.

```rust
struct Journal<File> {  
    buffer: Vec<u8>,  /// The in-memory page buffer.
    page_size: usize, /// The size of each page.
    max_pages: usize, /// The maximum of pages to be loaded in memory.
    buffered_pages: u32, /// The current number of pages held in the `buffer`. 
    journal_number: u64,  /// The random journal's identifier.
    path: PathBuf,  /// The path of the journal file.
    file: Option<File>, /// The actual File handler. 
}
```