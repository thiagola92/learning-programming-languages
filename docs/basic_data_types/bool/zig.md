# Zig

## Bool

```zig
const print = @import("std").debug.print;

pub fn main() !void {
    const a = true;
    const b = false;
    
    print("a = {}\n", .{a});
    print("b = {}\n", .{b});
}
```

```
a = true
b = false
```
