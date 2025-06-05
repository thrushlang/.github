<p align="center">
  <img src= "https://github.com/thrushlang/thrushc/blob/master/assets/thrushlang-v1.5.png" alt= "logo" style= "width: 2hv; height: 2hv;"> </img>
</p>

<h1 align="center">Thrush Programming Language</h1>

The **Thrush Programming Language**. A system programming language that revolutionizes low-level control, intuitive abstraction for beginners, and limitless IR low-level control for experts.

## Philosophy

### The problem

Systems languages like ``C``, ``C++``, and ``Rust`` have yet to fully explore low-level programming potential, particularly in explicit manipulation of intermediate representations (IRs). Direct IR control empowers developers with seamless, high-level orchestration of assembly-like operations from source code, eliminating the need to resort to raw assembly.

### The Thrush solution 

Thrush empowers developers by enabling IR manipulation through language-integrated Low-Level Instructions (LLI), a high-level, streamlined interface for GCC and LLVM intrinsic instructions, while prioritizing beginners with a future memory-safe abstraction layer built atop its powerful, low-level system.

## Why Thrush over C, C++ or Rust?

Thrush holds immense promise for bare-metal and embedded systems development through its innovative low-level instructional concepts, particularly its language-integrated Low-Level Instructions (LLI) for seamless IR manipulation with GCC and LLVM intrinsics. While prioritizing simplicity, Thrush will layer a memory-safe abstraction atop its powerful low-level system, making it beginner-friendly. Depending on your needs, you might still choose C, C++, or Rust, but Thrush offers a unique blend of control and accessibility.

### Low Level Control

- Thrush empowers developers to compile low-level instructions directly to a specified target from source code, enabling precise, architecture-specific optimization with unparalleled ease.

```rust
compile @target("armv7e-m") @output("example.s") @asm {
  instr allocated_u8: ptr[u8] = alloc stack!, { u8, @align(4) };
  write allocated_u8, u8 8;
};
```

- Thrush enables seamless integration of low-level instructions alongside their high-level counterparts, allowing developers to fluidly switch between abstraction levels within the same codebase.

```rust
fn main() {
    local number: u8 = 0;

    // Low-level instruction for direct memory access.
    instr loaded_value: u8 = load u8, number;
}
```

- Thrush enables seamless embedding of linear assembler within the compilation process, offering direct, streamlined control over architecture-specific code generation.

```rust
fn main() {
    asm {
      section .text
      global _start

      _start:
          mov rax, 60
          mov rdi, 0
          syscall
    };
}
```

- Thrush enables seamless compile-time code execution, empowering developers to perform computations and optimizations directly during compilation with a simple, intuitive syntax.

```rust
fn comptime_sum(a: u8, a: u8) u16 @compiletime {
  // Non-explicit cast is allowed.
  return a + b;
}

fn main() {
   comptime_sum(15, 15);
}
```

- And many more unique features when the language base is finished! ~ Kevin Benavides

## Features

- Direct Code Generation Control: Manipulate intermediate representations (IR) and low-level instructions for precise, architecture-specific optimizations.
- Powerful Sublanguage Integration: Seamlessly interoperate with LLVM and assembler, enabling fine-grained control over code generation.
- Robust Static Typing: Enforce type safety with a strongly statically typed system for reliable, high-performance code.
- Flexible Unsafe Environment: Harness a complex, unsafe low-level system for maximum control in bare-metal and embedded development.
- C Interoperability: Integrate effortlessly with C codebases, leveraging existing libraries and systems.
- Unified, Lightweight Compiler: A robust, all-in-one compiler designed for simplicity and ease of use.
- C-Like Simplicity: Lightweight syntax inspired by C, making it approachable yet powerful.
- Minimal Runtime Overhead

## Goals

- The Thrush Compiler (``thrushc``) is very compact, has the LLVM linker (``lld``) embedded, and supports the ``x86_64`` architecture for the moment, but with the ability to generate executables with formats such as ``COFF`` (Windows), ``ELF`` (Linux), ``Mach0`` (MacOS), and ``WASM`` (WebAssembly).

- The production-ready compiler is estimated to weigh 20MB in its entirety, but only with support for ``x86_64``. Research is currently underway to make it lightweight yet portable with all available backend architectures.

## State

- The Thrush Compiler ``thrushc``: The Thrush Compiler is still in active development. We're currently focused on building out its complex layer of low-level instructions and developing a robust linter.
- The Thrush Package Manager ``thorium``: The package manager has already begun development but is not yet complete.

> [!NOTE]  
> If you want to accelerate the speed of language development, please consider **donating** to the creator or joining us and carrying out the language.

## Documentation

The documentation isn't ready yet, as the language is still in deep development. You can see the speculative syntax at https://github.com/thrushlang/syntax.

## Example - Fibonacci sequence 

### Compiler

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

        local fmt: str = "fibonacci of '%ld': %ld\n";

        // Transformation to pointer.
        instr raw_fmt: ptr[str] = rawptr fmt;

        // Explicit pointer arithmetic.
        instr raw_fmt_str: ptr = load ptr, address raw_fmt { 0, 0 };

        // Print the Fibonacci.
        print(raw_fmt_str, i, fibonacci(i));

    }

}
```

## Contribute

We're looking for contributors for our project! If you're a Spanish speaker and would like to contribute, contact us through our official social media channels.
Already know Rust but not LLVM? Don't worry! We're happy to teach you.

## Social Media

[![Thrush Programming Language](https://invite.casperiv.dev?inviteCode=DJaVs4kM9U)](https://discord.gg/DJaVs4kM9U)
