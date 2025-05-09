<p align="center">
  <img src= "https://github.com/thrushlang/thrushc/blob/master/assets/thrushlang-v1.5.png" alt= "logo" style= "width: 2hv; height: 2hv;"> </img>
</p>

<h1 align="center">Thrush Programming Language</h1>

The **Thrush Programming Language**. A programming language dedicated to creating maintainable and modular software.

## Philosophy

The Thrush Programming Language aims to simplify the inherently tedious process of programming in a systems language, streamlining the experience while maintaining the essence of a proper systems language.

Introducing concepts such as:

- Memory safety.
- Simple error handling.
- Strong Foreign Function Interface (FFI).
- Simplified low-level memory control.
- Compile-time execution with Just-In-Time compiler.
- Automatic deallocation when reaching EFC.
- Automatic construction of destructors.
- Reference and hidden dereference systems.

## Features 

- High level abstraction.
- Statically typed.
- Strongly in OOP paradigm.
- Automatic memory management through ARC.
- Partial memory safety.
- Faster compilation times.
- Faster as C.
- Compiled to machine code.

## Example - Fibonacci sequence 

### Compiler

```console
thrushc fibonacci.th -o fibonacci && ./fibonacci
```

### Package Manager

```console
thorium run
```

### Code

```
fn print(fmt :: ptr) s32 @public @ignore @extern("printf");

fn fibonacci(n :: u64) u64 @alwaysinline @strongstack @hot {

    if n <= 1 {
        return n;
    }

    return fibonacci(n - 2) + fibonacci(n - 1);

}

fn main() { 

    for local i: u64 = 0; i < 10; i++; {

        local format: str = "fibonacci of '%ld': %ld\n";

        // Explicit pointer arithmetic.
        print(carry[ptr] address format[0][0], i, fibonacci(i));

    }

}
```

## Contribute

- If you're interested in contributing to the project and you're a **Spanish speaker**, let us know by visiting our official social media channels below.
- If you already know Rust but not LLVM, we're willing to teach.

## Social Media

[![Thrush Programming Language](https://invite.casperiv.dev?inviteCode=DJaVs4kM9U)](https://discord.gg/DJaVs4kM9U)
