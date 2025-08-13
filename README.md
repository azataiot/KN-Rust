# KN-Rust

## Primitives

### Scalar Types

| Group                 |                                                              | Example                                     |
|-----------------------|--------------------------------------------------------------|---------------------------------------------|
| Signed integers       | `i8`, `i16`, `i32`,`i64`,`i128` and `isize` (pointer size)   | 1, 100, 1_000_000                           |
| Unsigned integers     | `u8`, `u16`, `u32`, `u64`, `u128` and `usize` (pointer size) | -1, -200                                    |
| Floating point        | `f32`, `f64`                                                 | 3.14159                                     |
| Unicode scalar values | `char` , like `'a'`, `'α'` and `'∞'` (4 bytes each)          | `'a'`, `'α'` and `'∞'`                      |
| Boolean               | `bool` either `true` or `false`                              | `true` or `false`                           |
| The unit type         | `()`                                                         | only possible value is an empty tuple: `()` |



Note: Integers default to `i32` and floats default to `f64`



### Compound Types

| Group  | Example     |
|--------|-------------|
| Arrays | `[1,2,3]`   |
| Tuples | `(1, true)` |



## Variabels

```rust
// let <variable_name>: <type> = <expression>;
let x: u32 = 42;
let mut mutable_binding = 1;
```



## Flow of Control

### if/else

```rust
if n < 0 {
        print!("{} is negative", n);
    } else if n > 0 {
        print!("{} is positive", n);
    } else {
        print!("{} is zero", n);
    }
```

### while

```rust
while <condition> {
    // code to execute
}
```

```rust
// The factorial function using a `while` loop.
pub fn factorial(n: u32) -> u32 {
    let mut result = 1;
    let mut i = 1;
    while i <= n {
        result *= i;
        i += 1;
    }
    result
}
```

### for

```rust
for <element> in <iterator> {
    // code to execute
}
```

```rust
let mut sum = 0;
for i in 1..=5 {
    sum += i;
}
```

here are five kinds of ranges in Rust:

- `1..5`: A (half-open) range. It includes all numbers from 1 to 4. It doesn't include the last value, 5.
- `1..=5`: An inclusive range. It includes all numbers from 1 to 5. It includes the last value, 5.
- `1..`: An open-ended range. It includes all numbers from 1 to infinity (well, until the maximum value of the integer type).
- `..5`: A range that starts at the minimum value for the integer type and ends at 4. It doesn't include the last value, 5.
- `..=5`: A range that starts at the minimum value for the integer type and ends at 5. It includes the last value, 5.

```rust
// The factorial function using a `for` loop.
pub fn factorial(n: u32) -> u32 {
    let mut result = 1;
    for i in 1..=n {
        result *= i;
    }
    result
}
```

## Structs

```rust
// Define a struct
struct Ticket {
    title: String,
    description: String,
    status: String
}

// Instantiation
// Syntax: <StructName> { <field_name>: <value>, ... }
let ticket = Ticket {
    title: "Build a ticket system".into(),
    description: "A Kanban board".into(),
    status: "Open".into()
};

// Field access
let x = ticket.description;

// Methods
impl Ticket {
    fn is_open(&self) -> bool {
        self.status == "Open"
    }
}

// Function call syntax:
let is_open = ticket.is_open();

//   <StructName>::<method_name>(<instance>, <parameters>)
let is_open = Ticket::is_open(ticket);
```

```rust
// All produce a String
title: String::from("Build a ticket system"),
title: "Build a ticket system".to_string(),
title: "Build a ticket system".into(),
```

### Static Method

```rust
struct Configuration {
    version: u32,
    active: bool
}

impl Configuration {
    // `default` is a static method on `Configuration`
    fn default() -> Configuration {
        Configuration { version: 0, active: false }
    }
}



```



## Modules

```rust
mod dog;
```

```rust
// Bring `MyStruct` into scope
use crate::module_1::module_2::MyStruct;

// Now you can refer to `MyStruct` directly
fn a_function(s: MyStruct) {
     // [...]
}
```

```rust
use crate::module_1::module_2::*;
```

Star imports:

```rust
use crate::module_1::module_2::*;
```

*It is generally discouraged because it can pollute the current namespace, nonetheless, it can be useful in some cases, like when writing unit tests.*

