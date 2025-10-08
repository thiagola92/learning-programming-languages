# Rust

## Create directory

```rust
use std::fs::create_dir;

fn main() {
    create_dir("example");
}
```

## List files

=== "Stream Content"

    ```rust
    use std::fs::read_dir;

    fn main() {
        let files = read_dir("example").unwrap();

        for file in files {
            println!("{:?}", file.unwrap().file_name());
        }
    }
    ```

## Remove directory

```rust
use std::fs::remove_dir;

fn main() {
    remove_dir("example");
}
```