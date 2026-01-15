# Rust

## Struct

```rust
struct Example {
    field1: i32,
    field2: f32,
}

fn main() {
    let example = Example {
        field1: 1,
        field2: 5.5,
    };

    print!("example.field1 = {}\n", example.field1);
    print!("example.field2 = {}\n", example.field2);
}
```

```
example.field1 = 1
example.field2 = 5.5
```