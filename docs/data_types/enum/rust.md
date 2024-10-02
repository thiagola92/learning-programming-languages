# Rust

## Enum

=== "Auto"

    ```rust
    #[derive(Debug)]
    enum Example {
        A,
        B,
        C,
    }

    fn main() {
        print!("A = {:?}\n", Example::A);
        print!("B = {:?}\n", Example::B);
        print!("C = {:?}\n", Example::C);
    }
    ```

    ```
    A = A
    B = B
    C = C
    ```