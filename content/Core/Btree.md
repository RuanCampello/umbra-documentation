
[[Btree]] is a classical data-structure for databases. The version implemented here is more precisely a [B*-Tree](B*Tree).
[B*-Tree](B*Tree) is a refinement of archetypal [[Btree]] structure, with focus on improving the utilisation of space and reducing the frequency which nodes splits. Instead of splitting a full node immediately, a B*-tree first tries to redistribute keys with a [[sibling]]. This approach delays the growth in tree's height, keeping average node occupancy higher ultimately resulting in better space and [cache](Cache) efficiency.

It's a high-performance implementation inspired by [Art of Computer Programming Vol 3](https://seriouscomputerist.atariverse.com/media/pdf/book/Art%20of%20Computer%20Programming%20-%20Volume%203%20(Sorting%20&%20Searching).pdf) as well as the B-tree structure in [[SQLite]]. If you're interested in how this compares with other production-grade implementations, check out [this deep dive into PostgreSQL’s B-tree](https://iniakunhuda.medium.com/b-tree-implementation-in-postgresql-deep-dive-into-database-indexing-b1a34032637d)

```rust
pub(in crate::core) struct BTree<'p, File, Cmp> {
    root: PageNumber,
    min_keys: usize,
    balanced_siblings: usize,
    pager: &'p mut Pager<File>,
    comparator: Cmp, /// The byte comparator used to get 
}
```


This structure leverages a [[Pager]] to abstract disk I/O and ensure persistence, while a [[Cache]] layer is used to optimize page access and reduce latency. Each page in the tree can store multiple keys and child references, and these are structured to fit efficiently within fixed-size blocks on disk, following a slotted page model. [[Overflow]] handling is also supported for large payloads. While the [[Btree]] operates over fixed-size pages, it handles variable-sized keys and values internally, enabling real-world database flexibility without sacrificing performance.