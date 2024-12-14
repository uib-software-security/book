# Programació en Rust

---

## Importància de Rust

- En un món cada vegada més connectat i dependent de la tecnologia, la **seguretat del software** és crítica.
- **Rust** és un llenguatge de programació modern que es destaca per la seva **seguretat**, **rendiment** i **concisió**.
- La seva combinació única de característiques el fa ideal per a aplicacions on la **seguretat** i el **rendiment** són prioritats, com ara sistemes operatius, aplicacions de seguretat, motors de jocs i molts altres

---

## Per què aprendre Rust?

- Llenguatge més ràpid després de C
- Sense _garbage collector_ (temps d'execució més ràpid)
- Sistema de tipus molt extens
- Output útil del compilador
- Llenguatge segur (Seguretat de la memòria)
- Ràpida adopció en diversos sectors

---

## Llenguatge més estimat des del 2016 (Stack Overflow)

![Most loved programming language since 2016](./img/loved-lang.png)

[Llenguatge de programació més estimat des del 2016 (Stack Overflow)](https://survey.stackoverflow.co/2023/#section-admired-and-desired-programming-scripting-and-markup-languages)

---

## Corva d’aprenentatge de Rust

![Rust learning curve](./img/rust-learning-curve.png)

---

## Recursos

- Web oficial:
  - [https://www.rust-lang.org/](https://www.rust-lang.org/)
- Llibre “_The Rust Programming Language_”
  - [https://doc.rust-lang.org/stable/book/](https://doc.rust-lang.org/stable/book/)
- Rust by example:
  - [https://doc.rust-lang.org/rust-by-example/](https://doc.rust-lang.org/rust-by-example/)
- Rustlings:
  - [https://github.com/rust-lang/rustlings](https://github.com/rust-lang/rustlings)
- Rust by practice:
  - [https://practice.course.rs/why-exercise.html](https://practice.course.rs/why-exercise.html)

![The Rust Programming Language](./img/rust-book.png)

---

## Instal·lació

- Linux/MacOS:
  - [https://rustup.rs/](https://rustup.rs/)

```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

- Windows:
  - [https://forge.rust-lang.org/infra/other-installation-methods.html](https://forge.rust-lang.org/infra/other-installation-methods.html)
- Comprovar instal·lació: **rustc --version**
- Comprovar instal·lació: **cargo --version**
- Documentació: **rustup doc**
- Actualitzar: **rustup update**

---

## VS Code

- Extensió rust-analyzer:
  - [https://marketplace.visualstudio.com/items?itemName=rust-lang.rust-analyzer](https://marketplace.visualstudio.com/items?itemName=rust-lang.rust-analyzer)

---

## Programa "Hello World"

- Programa “Hello World”:

```rust
fn main() {
  println!("Hello, world!");
}
```

- Compilar:`rustc <file.rs>`
- Donar format: `rustfmt <file.rs>`

## Cargo: build i package manager

- `cargo new <project_name>`: crea un nou projecte
- `cargo init`: crea un nou projecte al directori actual
- `cargo build`: compila el projecte a ./target/debug
- `cargo build --release`: compila el projecte per publicar (_release_) a ./target/release
- `cargo run`: compila i executa
- `cargo check`: comprova el codi per assegurar-se que es compila (no produeix un executable)
- `cargo fmt`: dona format a tots els fitxers del projecte

---

## Comentaris

```rust
// Line comment

/*
 * Block comment
 */
```

---

## Variables

```rust
let x: i32; // Not initialized
x = 0;
let y: i32 = 0; // Initialized
let mut x: i32; // Mutable Not initialized
x = 0;
let mut x: i32 = 0; // Mutable Initialized
let (name, age) = ("Bob", 33); // assign multiple variables

// compiler is able to infer the type based on the value**
let x = 0;
```

- **Shadowing**: variables can be redeclared inside the same scope

---

## Constants

```rust
// constants
// can be declared global, outside the functions
// type of the value must be annotated

const THREE_HOURS_IN_SECONDS: u32 = 60 * 60 * 3;
```

---

## Print

```rust
println!("a = {} and b = {}", a, b);
println!("a = {0} and b = {1}", a, b);
println!("a = {a} and b = {b}");
println!("a = {a} and b = {b}", a = 1, b = 4);
println!("Binary: {:b} Hex: {:x} Octal: {:o}", 10, 10, 10);
println!("{:?}", (name, age)); // for debug
```

---

## Tipus de dades: sencers

| **Signed**    | **Unsigned**  | **Length**      |
|---------------|---------------|-----------------|
| i8            | u8            | 8-bit           |
| i16           | u16           | 16-bit          |
| i32 (default) | u32           | 32-bit          |
| i64           | u64           | 64-bit          |
| i128          | u128          | 128-bit         |
| isize         | usize         | arch (32 or 64) |

---

## Tipus de dades: sencers**

| **Number literals** | **Example** |
|----------------------|-------------|
| Decimal              | 98_222      |
| Hex                  | 0xff        |
| Octal                | 0o77        |
| Binary               | 0b1111_0000 |
| Byte (u8 only)       | b'A'        |

---

## Tipus de dades: nombres reals, i operacions

- Floating point:

| **Signed** | **Length** | **Description**            |
|------------|------------|----------------------------|
| f32        | 32-bit     | single-precision           |
| f64        | 64-bit     | double-precision (default) |

- Numeric operations:
  - `+`, `-`, `*`, `/`
  - `%` (mòdul)

---

## Tipus de dades: boolean i char

- Boolean:

| **Type** | **Values**  |
|----------|-------------|
| bool     | true, false |

- Char:

| **Signed** | **Length** | **Values** |
|------------|------------|------------|
| char       | 4 bytes    | U+0000 to U+D7FF and U+E000 to U+10FFFF inclusive |
|            |            | 'a', 'b'... |

---

## Tipus de dades: String (1)

- String és un tipus de cadena codificada en UTF-8 que pot créixer, i és mutable
- És el tipus de cadena més comú per modificar o tenir dades de text
- Creació d'una cadena nova
  - String::new() per crear una cadena buida.
    - Exemple: let mut s = String::new();
  - String::from() o el mètode to_string() poden crear una cadena a partir d'un literal de cadena.
    - Exemple: let s = String::from("hola");
    - Exemple: let s = "hola".to_string();

---

## Tipus de dades: String (i 2)

- Afegiu una cadena al final d’una cadena utilitzant push_str()
  - Exemple: s.push_str("món"); // esdevé "hola món"
- Afegeix un sol caràcter amb push().
  - Exemple: s.push('!'); // esdevé "hola món!
- String augmenta automàticament la seva capacitat segons calgui, però també podeu especificar-la amb with_capacity.
  - Exemple: let mut s = String::with_capacity(10);
- Comproveu la capacitat actual mitjançant el mètode de capacity().
  - Exemple: println!("Capacitat: {}", s.capacity());

---

## Tuples

- (type1, type2, … typeN)

```rust
let tup: (i32, f64, u8) == (500, 6.4, 1);
// or let tup = (500, 6.4, 1);

let (x, y, z) = tup;
let five_hundred = tup.0;
let six_point_four = tup.1;
let one = tup.2;
````

---

## Arrays

- array: [type; length]

```rust
let a = [1, 2, 3, 4, 5];
let a: [i32; 5] = [1, 2, 3, 4, 5];
let a = [3; 5]; // let a = [3, 3, 3, 3, 3];
let first = a[0];
let second = a[1];
```

## Funcions

```rust
fn function_name(param1: type1, param2: type2... ) -> returnType {
  // ...
}
```

Example:

```rust
fn five() -> i32 {
  return 5;
}

fn five() -> i32 {
 5
}
```

---

## if expression

```rust
 if x == 4 {
   println!("x is four");
} else if x == 3 {
   println!("x is three");
} else {
   println!("x is something else");
}

let number = if condition { 5 } else { 6 };
```

---

## loop bucle

```rust
loop {
  break;
  continue;
}

// Returning Values from Loops
let result = loop {
  counter += 1;
  if counter == 10 {
    break counter * 2;
  }
};

---

## while bucle

```rust
let mut i = 0;

while i < 10 {
  println!("hello");
  i = i + 1;
}
```

---

## for bucle

```rust
let a = [10, 20, 30, 40, 50];
for element in a {
  println!("the value is: {element}");
}

let mut sum = 0;

for n in 1..11 {
  sum += n;
}
```

---

## Proposta (1)

> Fer un programa que calculi els nombres primers entre 1 i 50.000

![Nombrers primers](./img/prime-numbers.png)

---

## Proposta (2)

> Fer un programa que calculi els primers 100 nombres de la successió de Fibonacci

![Fibonacci](./img/fibonacci.png)

---

## Ownership i borrowing (1)

- **Ownership**: cada valor té només un únic propietari
  - Quan una variable queda fora de l’abast (out of scope), es crida automàticament la funció “**drop**” per alliberar els recursos associats
- **Moving**: quan assignes una variable a una altra, la propietat (ownership) és transferida
- **Cloning**: quan es necessita una còpia de les dades, es pot utilitzar el mètode “**clone**”

## Ownership i borrowing (i 2)

```rust
let name1 = String::from("Bob");
let name2 = name1; // name1 is moved to name2
println!("Hello, {}", name1); // Error: value used here after move
println!("Hello, {}", name2); // OK
```

```rust
let name1 = String::from("Bob");
let name2 = name1.clone(); // Creates a copy of the value
println!("Hello, {}", name1); // OK
println!("Hello, {}", name2); // OK
```

---

## Drop / Copy traits

![Drop / Copy traits](./img/drop-copy.png)

---

## Borrowing

```rust
fn modify_name(name: &mut String) {
   name.push_str(" Doe");
}

fn main() {
   let mut full_name = String::from("John");
   modify_name(&mut full_name); // Passing a mutable reference to 'full _name'.
   println!("Hello, f", full_name); // 'full _name' is still valid and modified.
}
```
