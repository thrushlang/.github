<p align="center">
  <img src= "https://github.com/thrushlang/thrushc/blob/master/assets/thrushlang-v1.5.png" alt= "logo" style= "width: 2hv; height: 2hv;"> </img>
</p>

<h1 align="center">Thrush Programming Language</h1>

The **Thrush Programming Language**. A programming language dedicated to creating maintainable and modular software.

## Philosophy

### The breach

There's a breach right now, and that's the fact that there's no memory-safe language focused on systems development that also offers beginner-friendly capabilities and a language environment. Thrush attempts to bridge this breach.

### The Thrush solution 

The programming language focuses on providing a beginner-friendly yet advanced experience while also allowing for complete adaptability in certain circumstances, allowing for highly adaptable code.

## Key Points 

- Intrinsic manipulation of code generation.
- Strong sublanguage, with the ability to interoperate directly with **[LLVM](https://llvm.org/)** and **Assembler**.
- Strongly statically typed.
- Memory safety environment.
- Complex unsafe environment.
- C interop.
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
