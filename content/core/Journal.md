
```rust
struct Journal<File> {  
    buffer: Vec<u8>,  
    page_size: usize, /// The maximum of pages to be loaded in memory.  
    max_pages: usize, /// The current number of pages held in the `buffer`.  
    buffered_pages: u32, /// The random journal's identifier.  
    journal_number: u64,  
    path: PathBuf,  
    file: Option<File>,  
}
```

The [[Journal]] file implements the [commit] and [rollback] features.