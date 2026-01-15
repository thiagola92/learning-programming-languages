# Zig

## Enum

=== "Auto 1"

    ```zig
    const print = @import("std").debug.print;

    const Example = enum {
        A,
        B,
        C,
    };

    pub fn main() !void {
        print("A = {d}\n", .{Example.A});
        print("B = {d}\n", .{Example.B});
        print("C = {d}\n", .{Example.C});
    }
    ```

    ```
    A = 0
    B = 1
    C = 2
    ```

=== "Auto 2"

    É possível especificar o tipo que o enum deve usar.  

    ```zig
    const print = @import("std").debug.print;

    const Example = enum(u2) {
        A,
        B,
        C,
    };

    pub fn main() !void {
        print("A = {d}\n", .{Example.A});
        print("B = {d}\n", .{Example.B});
        print("C = {d}\n", .{Example.C});
    }
    ```

    ```
    A = 0
    B = 1
    C = 2
    ```

=== "Set"

    É obrigatório informar o tipo a ser usado pelo enum.  

    ```zig
    const print = @import("std").debug.print;

    const Example = enum(u2) {
        A = 0,
        B = 1,
        C = 2,
    };

    pub fn main() !void {
        print("A = {d}\n", .{Example.A});
        print("B = {d}\n", .{Example.B});
        print("C = {d}\n", .{Example.C});
    }
    ```

    ```
    A = 0
    B = 1
    C = 2
    ```

=== "Both"

    É obrigatório informar o tipo a ser usado pelo enum.  

    ```zig
    const print = @import("std").debug.print;

    const Example = enum(u5) {
        A,
        B = 25,
        C,
    };

    pub fn main() !void {
        print("A = {d}\n", .{Example.A});
        print("B = {d}\n", .{Example.B});
        print("C = {d}\n", .{Example.C});
    }
    ```

    ```
    A = 0
    B = 25
    C = 26
    ```

## Extra

=== "Methods"

    Enums podem conter métodos.

    ```zig
    const print = @import("std").debug.print;

    const Example = enum {
        A,
        B,
        C,

        pub fn isA(self: Example) bool {
            return self == Example.A;
        }
    };

    pub fn main() !void {
        print("A? {}\n", .{Example.A.isA()});
        print("A? {}\n", .{Example.B.isA()});
    }
    ```

    ```
    A? true
    A? false
    ```