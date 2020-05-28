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

- 字符型

    | Length | Signed |
    | ------ | ------ |
    | 32-bit | char   |

- 复合类型（元组，数组）

    - 元组类型

      ```rust
      fn main() {
          let tup: (f32, u8, i32) = (3.14, 2, -32);
          // 通过模式匹配去解构元组（Pattern match, destructure）
          let (x, y, z) = tup;
          println!("0: {}\n1: {}\n2:{}", tup.0, tup.1, tup.2);
          assert_eq!(y, 2);
      }
      ```

      

    - 数组类型

        ```rust
        fn main() {
            let ary: [i32; 2] = [1, 2];
            let a = [1, 3];
            assert_eq!(a, [1, 1, 1]);
            println!("{:?}", ary);
        }
        ```

        

### 方法

```rust
fn main() {
    let y = plus_one(5);
    // 结果为6
    println!("The value of y is: {}", y);
}

fn plus_one(x: i32) -> i32 {
	// 方法的最后一行不加分号可以表示直接返回值
    x + 1
}
```



### 控制流

- `if`

  ```rust
  fn main() {
      let x = 3;
      if x > 10 {
          println!("x is bigger than 10");
      } else if x > 5 {
          println!("x is bigger than 5, but smaller than 10");
      } else {
          println!("x is smaller than 5");
      }
  }
  ```

- `loop`

  ```rust
  fn main() {
      let mut counter = 0;
      let a = loop {
          counter += 1;
          if counter == 1000 {
              // 终止循环，并且返回值
              break counter * 2;
          }
      };
      println!("The value of a: {}", a);
  }
  ```

- `while`

  ```rust
  fn main() {
      let ary = [1, 2, 3, 4, 5];
      let mut i = 0;
      while i < ary.len() {
          println!("The {} number is: {}", i, ary[i]);
          i += 1;
      }
  }
  ```

- `for`

  ```rust
  fn main() {
      let ary = [9, 8, 7, 6, 5, 4, 3, 2, 1, 0];
      for (i, v) in ary.iter().enumerate() {
          println!("{} --> {}", i, v);
      }
      
      for num in (1..=10).rev() {
          println!("{}", num);
      }
  }
  ```

  

  ### 理解所有权 `Ownership`

  > 所有权系统是`Rust`内存安全的保证，理解它是如何运作的非常重要

  1. 每个值都有一个变量，称之为所有者（`Owner`）
  2. 每个变量只能有一个所有者
  3. 当所有者超出范围，值将被Drop

  ```rust
      {                      // s is not valid here, it’s not yet declared
          let s = "hello";   // s is valid from this point forward
  
          // do stuff with s
      }                      // this scope is now over, and s is no longer valid
  ```

  

