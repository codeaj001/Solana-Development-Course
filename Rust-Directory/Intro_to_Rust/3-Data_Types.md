# Rust Data Types

## What Are Data Types? 🤔
Data types define what kind of data a variable can hold. Think of a variable as a container, and the type tells us what kind of product (data/value) is inside the container.

---

## Rust Data Types Overview
Rust’s type system ensures safety and performance by specifying what kind of data can be stored in variables. Below are the common data types in Rust:

- **String**
- **Integer**
- **Float**
- **Boolean**
- **Character**
- **Array**
- **Slices**
- **Tuples**

---

### 1. String
A string is a piece of text enclosed in double quotes (`" "`) or single quotes (`' '`).

#### Example:
```rust
let name = "Code AJ";
// To see the output
println!("{}", name);

// Output:
// Code AJ
```

---

### 2. Integer
An integer is a whole number without quotes.

#### Example:
```rust
let number = 4;
let a = 14;
```

#### Integer Types:
Rust integers have different sizes to manage memory efficiently. These types are:

| Type  | Size     | Range                          |
|-------|----------|--------------------------------|
| i8    | 8 bits   | −128 to 127                 |
| u8    | 8 bits   | 0 to 255                      |
| i16   | 16 bits  | −32768 to 32767            |
| u16   | 16 bits  | 0 to 65535                    |
| i32   | 32 bits  | −2,147,483,648 to 2,147,483,647 |
| u32   | 32 bits  | 0 to 4,294,967,295            |
| i64   | 64 bits  | −922... to 922...          |
| u64   | 64 bits  | 0 to 18...                    |

#### Signed vs Unsigned Integers:
- **Signed (`i`)**: Can hold both positive and negative values (e.g., `i32`).
- **Unsigned (`u`)**: Can hold only positive values (e.g., `u32`).

#### Why Choose Unsigned?
Unsigned integers are ideal for cases like account balances, where negative numbers are invalid. They also optimize memory usage by doubling the range of positive numbers.

#### Checking Integer Limits:
You can check the minimum and maximum values of an integer type using:
```rust
let min_size = i32::MIN;
let max_size = i32::MAX;
println!("Min value = {} and Max value = {}", min_size, max_size);
```

---

### 3. Float
Floats represent numbers with decimals (e.g., 3.14).

#### Example:
```rust
let pi = 3.14;
println!("Pi is {}", pi);
```

Rust supports two floating-point types:
- `f32`: 32-bit precision
- `f64`: 64-bit precision (default)

---

### 4. Boolean
A boolean represents a value of `true` or `false`, they are often used in conditions and statements, when we reach if-else, we will discuss about it.

#### Example:
```
let rust_is_fun = true;
println!("Active: {}", rust_is_fun);
```

---

### 5. Character
Characters in Rust are defined using single quotes and support Unicode, emojis e.t.c, amazing right?.

#### Example:
```rust
let letter = 'A';
let emoji = '😄';
println!("{} {}", letter, emoji);
```

---

### 6. Array
Arrays are collections of elements of the same type with a fixed size.

#### Example:
```rust
let numbers = [1, 2, 3, 4, 5];
println!("First element: {}", numbers[0]);
```

---

### 7. Slices
Slices are views into arrays or other sequences, allowing you to work with a subset of the data.

#### Example:
```rust
let numbers = [1, 2, 3, 4, 5];
let slice = &numbers[1..3];
println!("Slice: {:?}", slice);
```

---

### 8. Tuples
Tuples can hold multiple values of different types.

#### Example:
```rust
let person = ("Alice", 30, true);
println!("Name: {}, Age: {}, Active: {}", person.0, person.1, person.2);
```

---

### What’s Next? 🚀
Rust’s strong type system ensures safety and performance. Experiment with these data types to get a solid foundation. Follow my journey on [Twitter](https://x.com/code_a_j) for more tips, code examples, and insights as we explore Rust together!
