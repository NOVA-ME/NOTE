# The Rust programming language

### Hello Rust

```rust
fn main(){
  println!("Hello Rust!");
}
```



### 可变性

```rust
// Rust变量默认是不可变的🙅
fn main(){
    let x = 5;
    println!("Value is {}", x);
    // Error
    x = 6;
    println!("Value is {}", x);
}

fn main(){
    // mut关键字赋予变量或引用可变性
    let mut x = 5;
    x = 6;
    println!("Value is {}", x);
}
```

### 常量

```rust
fn main(){
    // 常量大写的蛇形写法，必须指定类型
    const MAX_POINTS: i32 = 100_000;
}
```

### 遮罩（Shadowing）

```rust
fn main(){
    let x = 1;
    // 用let x 遮罩（Shadowing）了原来的x
    let x = x + 1;
    let x = x * 2;
    println!("The value of x is: {}", x);
}
```



### 数据类型

- 整型

    | Length  | Signed | UnSigned |
    | ------- | ------ | -------- |
    | 8-bit   | i8     | u8       |
    | 16-bit  | i16    | u16      |
    | 32-bit  | i32    | u32      |
    | 64-bit  | i64    | u64      |
    | 128-bit | i128   | u128     |
    | arch    | isize  | usize    |

- 整数字面量

    | Number literals | Example     |
    | --------------- | ----------- |
    | Decimal         | 98_222      |
    | Hex             | 0xff        |
    | Octal           | 0o77        |
    | Binary          | 0b1111_0000 |
    | Byte(u8 only)   | b'A'        |

- 浮点型

    | Length | Signed |
    | ------ | ------ |
    | 32-bit | f32    |
    | 64-bit | f64    |

    

