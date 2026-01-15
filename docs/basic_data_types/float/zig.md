# Zig

## Float

```zig
const print = @import("std").debug.print;

pub fn main() !void {
    const a: f16 = 10;
    const b: f16 = 10;
    const c: f64 = 10;
    const d: f80 = 10;
    const e: f128 = 10;

    print("a = {}\n", .{a});
    print("b = {}\n", .{b});
    print("c = {}\n", .{c});
    print("d = {}\n", .{d});
    print("e = {}\n", .{e});
}
```

```
a = 10
b = 10
c = 10
d = 10
e = 10
```
