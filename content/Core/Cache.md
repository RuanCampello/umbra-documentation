The [[Cache]] handles in-memory page caching with a clock-based eviction policy, inspired by operating system memory.
It's used directly by [[Pager]] to store and retrieve pages without hitting the disk on every access.
