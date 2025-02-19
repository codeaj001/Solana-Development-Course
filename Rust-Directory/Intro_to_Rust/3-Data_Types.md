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
A string is a piece of text enclosed in double quotes (`" "`) or single quotes (`' '`). We should knwo that Strings is immutable by default, which means after it has been created, it cannot be modified (pushing_str to it or something like that)

#### Example:
```rust
let name = "Code AJ";
// To see the output
println!("{}", name);

// Output:
// Code AJ
```
But let's discuss about Strings more:
- String
- String slice &str

In simple terms, String is when you own it, and string slice is when you borrow it, how..?
```
let mut my_book = String::from("The Adventures of Rustacean"); 
my_book.push_str(": The Sequel"); 
println!("{}", my_book);  
```
###### Explain
Create a mutable varible with name 'my_book',and assign it the text ("The Adventures of Rustacean"), push the text, The Sequel to the the my_book varibale, and then print the my_book varibale -this give the output:
`"The Adventures of Rustacean: The Sequel"`

And then, String slice or &str is when the variable is not your own, so you borrow it, you can use it, but you can modify it, and cannot add anything to it. For example:

```
let library_book = String::from("The Adventures of Rustacean"); 
let chapter: &str = &library_book[4..14];  
println!("{}", chapter);
```

###### Explain
After the variable library_book has been created, create another variable with name chaoter, and give a tye of &str, which means borrowed string, and fetch the 4th to 14th character of the library_book string, then print it.

#### But we must try it out to see the error..... (normally)
```
let mut library_book = String::from("The Adventures of Rustacean");
let chapter: &str = &library_book[4..14]; 
library_book.push_str(": The Sequel");   
println!("{}", chapter); 
```
This will print the following error:
##### error[E0502]: cannot borrow `library_book` as mutable because it is also borrowed as immutable

That is so awesome..!!!!
Let's go
L...F...G!!!
I l
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
| isize   | arch  | Depends on your arch                    |
| usize   | arch  | Depends on your arch                    |

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

#### The "architecture" refers to whether your machine is 32-bit or 64-bit:

32-bit machine: Each memory address is represented using 32 bits (4 bytes).
64-bit machine: Each memory address is represented using 64 bits (8 bytes).
The size of isize and usize is designed to be the same as the pointer size because they are often used for memory-related tasks like indexing arrays, working with slices, or offsets. Matching the pointer size ensures that these types can hold any possible memory address on your machine.


When you create a variable of type isize or usize:

Rust doesn't "check available memory" or "shrink the variable."
Instead, it already knows the size (4 bytes or 8 bytes) based on your machine's architecture. For example:
On a 32-bit system, an isize or usize will always take 4 bytes.
On a 64-bit system, it will always take 8 bytes.
This size is determined at compile time (when the program is built), not at runtime.

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
Arrays are collections of elements of the same type with a fixed size which means:
- You cannot add or remove.
- Arrays only contains the same type of values i.e you cannot mix integers with strings, or floats or bools e.t.c

#### Example:
```rust
let numbers = [1, 2, 3, 4, 5];
println!("First element: {}", numbers[0]);
```

My key takeaway about Arrays is memory efficiency, because it is stored as a contiguous block of memory which makes it efficient for accessign and iterating.

---

### 7. Slices
Slices are views into arrays or other sequences, allowing you to work with a subset of the data. A slice is like a window into an array or a vector. It allows you to access part of the data without owning it. Think of a slice as saying, “Hey, I just want to look at this part of the array for a bit, but I won’t move or change the whole array.”

##### 🌟 Key Features of Slices
- Variable Size: Unlike arrays (which have fixed size), slices are variable in size.
- Same Type: Just like arrays, all elements in a slice must have the same type.
- Reference-Based: A slice is always a reference to an existing array, vector, or other sequence.

##### 🚀 Why Use Slices?
1️⃣ Efficient: No copying—just a reference to the data.
2️⃣ Flexible: Work with variable-sized chunks of data.
3️⃣ Safe: Borrow-checker ensures no data races!

#### Example:
```rust
let numbers = [1, 2, 3, 4, 5];
let slice = &numbers[1..3];
println!("Slice: {:?}", slice);
```

---

### 8. Tuples
Tuples can hold multiple values of different data types, let's say for example, I need one palce to store a name, age, and something true or false about someone, below:

#### Example:
```rust
let person = ("Alice", 30, true);
println!("Name: {}, Age: {}, Active: {}", person.0, person.1, person.2);
```

As this is an example that shows storing string = Alice, Integer = 30 and Boolean = true, different data types stored in a single data type; amazing right?

Let's dig more into tuples, accessingl tuples value by index number, which startes from 0, in programming, we start counting from 0.
```
let tuple_words = ("Solana", "SuperTeam", "Moon");
println!("Community {}", tuple_words.1);
println!("Ecosystem {}", tuple_words.0);
println!("Location {}", tuple_words.2);
```

There is another called "Box unto box" - I call it that actually ....
It is called `Nested tuples`
This is actually having another tuple inside another tuple:
```
let nested_tuple = (("Code AJ", "SuperTeam"), "Solana", 217.91);
println!("Nested tuple: {}", nested_tuple.0.0);
println!("Second Nested tuple: {}", nested_tuple.0.1);
println!("Tuple: {}", nested_tuple.1);
```

`DESTRUCTURING TUPLES ` coming soooon.............

Destructuring tuples is a way fo assigning variable name to each of the value in the tuples, so, instead of using index numbers, we use variable names to call or print the values in the tuple.
---

### What’s Next? 🚀
Rust’s strong type system ensures safety and performance. Experiment with these data types to get a solid foundation. Follow my journey on [Twitter](https://x.com/code_a_j) for more tips, code examples, and insights as we explore Rust together!
