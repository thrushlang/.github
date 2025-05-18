<p align="center">
  <img src= "https://github.com/thrushlang/thrushc/blob/master/assets/thrushlang-v1.5.png" alt= "logo" style= "width: 2hv; height: 2hv;"> </img>
</p>

<h1 align="center">Thrush Programming Language</h1>

The **Thrush Programming Language**. A programming language dedicated to creating software that is highly adaptable to the programmer's experience.

## Philosophy

### The breach

There's currently a breach: there's no memory-safe language focused on systems development that also offers easy-to-use features and a language environment. 
For example:

- ``Rust`` Complexity is inherited by the borrow checker itself, and in addition to having an advanced **[LLVM](https://llvm.org/)** lifetimes system, by default it is not beginner-friendly.
- ``Swift`` It is beginner-friendly, but at the same time it cannot be used as a systems language due to its very closed systems compared to FFI and C. It is not advanced-friendly.

### The Thrush solution 

The programming language focuses on providing an advanced yet beginner-friendly experience while allowing for complete adaptability in certain circumstances, allowing for highly adaptable code based on the programmer's experience.

## Key points for advanced programmers

- Intrinsic manipulation of code generation.
- Strong sublanguage, with the ability to interoperate directly with **[LLVM](https://llvm.org/)** and **Assembler**.
- Strongly statically typed.
- Complex unsafe environment.
- C interop.

## Key points for beginner programmers

- Automatic memory management (thanks, ``Swift``, for the concept).
- By default, a lot of good abstractions.
- Partial memory safety environment.
- Lightweight software (C-like).
- Minimal runtime requirements (only the C runtime).

## Example - Fibonacci sequence 

### Compiler (Not beginner-friendly)

#### Linux

```console
mkdir build
thrushc -build-dir "build/" -llvm fibonacci.th -llvm-linker-flags "-ofibonacci;-melf_x86_64;--dynamic-linker=/lib64/ld-linux-x86-64.so.2;/usr/lib/crt1.o;/usr/lib/crti.o;/usr/lib/gcc/x86_64-pc-linux-gnu/15.
1.1/crtbegin.o;-L/usr/lib;-L/usr/lib/gcc/x86_64-pc-linux-gnu/15.1.1;-lc;/usr/lib/gcc/x86_64-pc-linux-gnu/15.1.1/crtend.o;/usr/lib/crtn.o" && ./fibonacci
```

### Package Manager

```console
thorium run
```

### Code

```
fn print(fmt: ptr) s32 @public @ignore @extern("printf");

fn fibonacci(n: u64) u64 @alwaysinline @strongstack @hot {

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
