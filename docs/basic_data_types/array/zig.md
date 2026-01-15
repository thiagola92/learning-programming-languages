# Zig

## Array

=== "Empty"

    ```zig
    const print = @import("std").debug.print;

    pub fn main() !void {
        const example: [3]i32 = undefined;

        print("example[0] = {}\n", .{example[0]});
        print("example[1] = {}\n", .{example[1]});
        print("example[2] = {}\n", .{example[2]});
    }
    ```

    ```
    example[0] = -1431655766
    example[1] = -1431655766
    example[2] = -1431655766
    ```

=== "Set"

    ```zig
    const print = @import("std").debug.print;

    pub fn main() !void {
        const example = [_]i32{ 1, 2, 3 };

        print("example[0] = {}\n", .{example[0]});
        print("example[1] = {}\n", .{example[1]});
        print("example[2] = {}\n", .{example[2]});
    }
    ```

    ```
    example[0] = 1
    example[1] = 2
    example[2] = 3
    ```

    !!! note

        Essa é a notação mais utilizada pois deixa para o compilador descobrir o **tamanho do array** e o **tipo da variável**.  
        Dito isto, é possível ser explícito sobre ambos.
        
        Explícito sobre o tamanho do array:  

        ```zig
        const example = [3]i32{ 1, 2, 3 };
        ```

        Explícito sobre o tamanho do array e o tipo da variável:  

        ```zig
        const example: [3]i32 = .{ 1, 2, 3 };
        ```

        Diferente de [C](./c.md), esta não é uma maneira de preencher o array parcialmente, ou seja, o tamanho deve ser o esperado.  
