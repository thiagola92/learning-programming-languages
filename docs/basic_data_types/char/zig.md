# Zig

## Char

```zig
const print = @import("std").debug.print;

pub fn main() !void {
    const a: u8 = 'z';

    print("a = {c}\n", .{a});
}
```

```
a = z
```
