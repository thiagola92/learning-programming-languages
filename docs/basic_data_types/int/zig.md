# Zig

## Int

```zig
const print = @import("std").debug.print;

pub fn main() !void {
    // Classic bit size.
    const a: i8 = 10;
    const b: i16 = 10;
    const c: i32 = 10;
    const d: i64 = 10;
    const e: i128 = 10;
    const f: u8 = 10;
    const g: u16 = 10;
    const h: u32 = 10;
    const i: u64 = 10;
    const j: u128 = 10;

    // Arbitrary number of bits (maximum is 65535).
    const k: i5 = 10;
    const l: i50 = 10;
    const m: u5 = 10;
    const n: u50 = 10;

    print("a = {}\n", .{a});
    print("b = {}\n", .{b});
    print("c = {}\n", .{c});
    print("d = {}\n", .{d});
    print("e = {}\n", .{e});
    print("f = {}\n", .{f});
    print("g = {}\n", .{g});
    print("h = {}\n", .{h});
    print("i = {}\n", .{i});
    print("j = {}\n", .{j});
    print("k = {}\n", .{k});
    print("l = {}\n", .{l});
    print("m = {}\n", .{m});
    print("n = {}\n", .{n});
}
```

```
a = 10
b = 10
c = 10
d = 10
e = 10
f = 10
g = 10
h = 10
i = 10
j = 10
k = 10
l = 10
m = 10
n = 10
```
