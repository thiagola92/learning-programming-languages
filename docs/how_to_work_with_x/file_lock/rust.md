# Go

## Shared Lock

```rust
use std::fs::File;

fn main() {
    let mut file = File::open("example.txt").unwrap();
    file.lock_shared();
    file.unlock();
}
```

## Exclusive Lock

```rust
use std::fs::File;

fn main() {
    let mut file = File::open("example.txt").unwrap();
    file.lock();
    file.unlock();
}
```