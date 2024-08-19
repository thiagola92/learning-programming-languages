# Rust

## Print

=== "Formatted"

    ```rust
    fn main() {
        print!("{}\n", "example");
    }
    ```

=== "IO"

    ```rust
    use std::io::{self, Write};

    fn main() {
        io::stdout().write("example".as_bytes()).unwrap();
    }
    ```

## Scan

=== "IO"

    ```rust
    use std::io::{self, Read};

    fn main() {
        let mut string: [u8; 30] = [0; 30];
        io::stdin().read(&mut string).unwrap();
    }
    ```