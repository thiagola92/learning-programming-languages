# Rust

## Read File

=== "All Content"

    ```rust
    use std::{fs::File, io::Read};

    fn main() {
        let mut content = String::new();
        let mut file = File::open("example.txt").unwrap();
        file.read_to_string(&mut content).unwrap();
    }
    ```

=== "Stream Content"

    ```rust
    use std::{fs::File, io::Read};

    fn main() {
        let mut partial_content: [u8; 30] = [0; 30];
        let mut file = File::open("example.txt").unwrap();
        file.read(&mut partial_content).unwrap();
    }
    ```

## Write to File

=== "All Content"

    ```rust
    use std::{fs::File, io::Write};

    fn main() {
        let mut file = File::open("example.txt").unwrap();
        file.write_all("Example".as_bytes()).unwrap();
    }
    ```

=== "Stream Content"

    ```rust
    use std::{fs::File, io::Write};

    fn main() {
        let mut file = File::open("example.txt").unwrap();
        file.write("Example".as_bytes()).unwrap();
    }
    ```