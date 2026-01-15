# Rust

## Array

=== "Empty"

    Está linguagem não permite o uso sem antes ter sido inicializado

    ```rust
    fn main() {
        let example: [i32; 3];

        // print!("example[0] = {:?}\n", example[0]);
        // print!("example[1] = {:?}\n", example[1]);
        // print!("example[2] = {:?}\n", example[2]);
    }
    ```

    !!! tip
    
        É possível inicializar todos com um mesmo valor para simular o comportamento de outras linguagens (inicializar com zeros).  

=== "Set 1"

    ```rust
    fn main() {
        let example = [1, 2, 3];

        print!("example[0] = {:?}\n", example[0]);
        print!("example[1] = {:?}\n", example[1]);
        print!("example[2] = {:?}\n", example[2]);
    }
    ```

    ```
    example[0] = 1
    example[1] = 2
    example[2] = 3
    ```

=== "Set 2"

    Inserir o mesmo valor em todas posições.  

    ```rust
    fn main() {
        let example: [i32; 3] = [0; 3];

        print!("example[0] = {:?}\n", example[0]);
        print!("example[1] = {:?}\n", example[1]);
        print!("example[2] = {:?}\n", example[2]);
    }
    ```

    ```
    example[0] = 0
    example[1] = 0
    example[2] = 0
    ```