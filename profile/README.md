<p align="center">
  <img src= "https://github.com/thrushlang/.github/blob/main/assets/thrushlang-v1.0.png" alt= "logo" style= "width: 2hv; height: 2hv;"> </img>
</p>

<h1 align="center">Thrush Programming Language</h1>

The **Thrush Programming Language**. A programming language dedicated to creating maintainable and modular software.

## Features 

- High level abstraction.
- Non-explicit cast for primitive types.
- Strongly statically typed.
- Strongly in OOP paradigm.
- Automatic memory management.
- Partial memory safety.
- Ahead of time compilation.
- Faster compilation times.
- Faster as C.
- Compiled to machine code.

## Shiny Features

- Support for quantum programming for quantum machines using Q# as a backend compiler.

## Compilation steps

*With the compiler (thrushc)...*

```console
thrushc --executable hello.th -o hello && ./output/hello
```

*With the package manager...* (**Coming soon**)

```console
thorium run
```

```
fn print(fmt :: str) s32 @public @ignore @extern("printf");

fn fibonacci(n :: u64) u64 {

    if n <= 1 {
        return n;
    }

    local fib_left: u64 = fibonacci(n - 1);
    local fib_right: u64 = fibonacci(n - 2);

    return fib_left + fib_right;

}

fn main() { 

    local fib: u64 = fibonacci(10);

    print("'10' fibonacci: %ld", fib);

}
```

## Contribute

- If you're interested in contributing to the project and you're a **Spanish speaker**, let us know by visiting our official social media channels below.

## Social Media

[![](https://dcbadge.limes.pink/api/server/https://discord.gg/DJaVs4kM9U)](https://discord.gg/DJaVs4kM9U)
