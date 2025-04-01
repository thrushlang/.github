<p align="center">
  <img src= "https://github.com/thrushlang/.github/blob/main/assets/thrushlang-v1.1.png" alt= "logo" style= "width: 2hv; height: 2hv;"> </img>
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

## LLVM

The **Thrush Programming Language** compiles using the **[LLVM](https://llvm.org)** project as its primary code generator, which is a backend compiler. It generally compiles bytecode or intermediate languages to assembler or machine code for the 45 different architectures and variants available. 

Thrush compiles AOT to LLVM bitcode, which is then compiled to optimized machine code, functioning similarly to Rust and Swift.

## Compilation steps

*With the compiler (thrushc)...*

```console
thrushc fibonacci.th -o fibonacci && ./fibonacci
```

*With the package manager...* (**Coming soon**)

```console
thorium run
```

```
fn print(fmt :: str) s32 @public @ignore @extern("printf");

fn fibonacci(n :: u64) u64 @alwaysinline @strongstack @hot {

    if n <= 1 {
        return n;
    }

    return fibonacci(n - 2) + fibonacci(n - 1);

}

fn main() { 

    for local i: u64 = 0; i < 10; i++; {

        print("fibonacci of '%ld': %ld\n", i, fibonacci(i));

    }

}
```

## Contribute

- If you're interested in contributing to the project and you're a **Spanish speaker**, let us know by visiting our official social media channels below.

## Social Media

[![](https://dcbadge.limes.pink/api/server/https://discord.gg/DJaVs4kM9U)](https://discord.gg/DJaVs4kM9U)
