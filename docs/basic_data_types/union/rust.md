# Rust

## Union

```rust
union Example {
    field1: i32,
    field2: f32,
}

fn main() {
    let mut example = Example { field1: 1 };
    print!("example.field1 = {}\n", unsafe { example.field1 });
    print!("example.field2 = {}\n", unsafe { example.field2 });

    example.field2 = 5.5;
    print!("example.field1 = {}\n", unsafe { example.field1 });
    print!("example.field2 = {}\n", unsafe { example.field2 });
}
```

```
example.field1 = 1
example.field2 = 0.000000000000000000000000000000000000000000001
example.field1 = 1085276160
example.field2 = 5.5
```