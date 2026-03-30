# Zig

## Union
Apenas o campo inicializado pode ser utilizado. Para trocar o campo é preciso inicializar novamente.  

```zig
const print = @import("std").debug.print;

const Example = union {
    field1: i32,
    field2: f32,
};

pub fn main() !void {
    var example = Example{ .field1 = 1 };
    print("example.field1 = {}\n", .{example.field1});

    example = Example{ .field2 = 5.5 };
    print("example.field2 = {}\n", .{example.field2});
}
```

```
example.field1 = 1
example.field2 = 5.5
```

!!! warning

    Só é possível identificar o campo utilizado quando usando tagged unions.  

## Tagged Union
Passando um enum durante a criação de uma union, fará com que os campos do enum sejam utilizados como tag para a union.  

```zig
const print = @import("std").debug.print;

const Tag = enum {
    field1,
    field2,
};

const Example = union(Tag) {
    field1: i32,
    field2: f32,
};

pub fn main() !void {
    var example = Example{ .field1 = 1 };
    example = Example{ .field2 = 5.5 };

    switch (example) {
        Example.field1 => {
            print("Field1", .{});
        },
        Example.field2 => {
            print("Field2", .{});
        },
    }
}
```

```
Field2
```