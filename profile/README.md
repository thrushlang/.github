<p align="center">
  <img src= "https://github.com/thrushlang/.github/blob/main/assets/logos/thrushlang.png" alt= "logo" style= "width: 1hv; height: 1hv;"> </img>
</p>

<h1 align="center">Thrush Programming Language</h1>

<p align="center">The <b>Thrush Programming Language</b>. A general-purpose systems programming language that provides a new low-level development approach.</p>

## Characteristics

- Syntactically it is based on Rust.
- Inspired by the low-level capabilities of C.

### Inspiration Name

Its name is Thrush, reminiscent of the **[thrush](https://en.wikipedia.org/wiki/Thrush_(bird))** bird, a relative of the **Turdidae** family.<br>Its pronunciation differs from the bird's name; it's actually **T**.. **Rush**, not Thrush.

#### Why this bird?

The **[thrush](https://en.wikipedia.org/wiki/Thrush_(bird))** bird possesses one of the most complex, coordinated, and wonderful songs in the animal world, standing out in a specific area.

This is an analogy.

Thrush is a very expressive and specific language for low-level programming, excelling in memory control, arithmetic operations, assembly, and much more at a low level. It offers a complex type layer to reduce possible runtime errors.

## Philosophy

Thrush allows software developers to create software with complete low-level control. This approach enhances robustness, optimizes performance, and simplifies code development for diverse, even exotic, architectures, directly addressing limitations found in many current systems programming languages.

## Why Thrush?

Thrush is a very promising tool for bare-metal and embedded system development thanks to its innovative low-level instruction concepts, particularly its integrated Low-Level Instructions (LLI) for fluent IR manipulation using GCC and LLVM intrinsics. This prioritizes learning intermediate code, rather than assembler code, unlocking architecture-specific optimizations and low-level type manipulation. Thrush offers low-level control over systems languages ​​like C, Rust, and C++ due to its manipulation of low-level instructions for optimizations.

### Low Level Control

- Thrush enables integration of low-level instructions along their high-level counterparts, allowing developers to fluidly switch between abstraction levels within the same codebase.

```rust
fn main() u32 {

    local number: u8 = 0;

    // Low-level instruction for direct memory access.
    instr loaded_value: u8 = load u8, number;

    return 0;

}
```

- Thrush enables embedding of linear assembler within the compilation process, offering direct control over architecture-specific code generation.

```rust

asmfn invoke_exit_syscall() void {
    "mov $$60, %rax",
    "mov $$1, %rdi",
    "syscall"
} { 
    "~{rax}~{rdi}"
}

fn main() u32 {
    invoke_exit_syscall();
    return 0;
}
```

- Thrush enables compile-time code execution, allowing developers to perform computations and optimizations directly during compilation with a simple, intuitive syntax.

```rust
fn comptime_sum(a: u8, b: u8) u16 @compiletime {
    // Non-explicit cast is allowed.
    return a + b;
}

fn main() u32 {
    comptime_sum(15, 15);
    return 0;
}
```

## Current Features

- Code Generation Control.
- Robust Static Type Checking.
- C Simplicity.
- C Interoperability.
- Native Assembler Interoperability.

## Future Features

- Automatically generated types for C headers (**CBindgen**).
- Quantum code generation, through QIR and CIR.
- Support for quantum behavior emulation with embedded QCOR, or a bytecode runner.

## Goals

- The Thrush Compiler has the ability to output pre-compiled object files ``.o`` for the architecture as well as assembler and its counterparts without going through the pass manager for optimization.
- The Thrush Compiler is very lightweight ``20``MB, considering that it contains embedded Clang for Linux and Windows, to be used as a wrapper to the closest linker.
- The Thrush compiler can now be used as a linker directly; it contains the LLVM Linker embedded in the executable, so you can invoke it directly without relying on external sources. The compiler can be used as a manual linker for ``Elf``, ``Coff``, ``Mach0``, and ``WASM`` formats.

## State

- The Thrush Compiler ``thrushc``: The Thrush compiler is still under development. Currently, we are focusing on developing its complex low-level instruction layer, optimizations in code generation, and a Clang-like C-style generation around LLVM.
- The Thrush Package Manager ``thorium``: The package manager has already begun development but is not yet complete.

## Documentation

The documentation isn't ready yet, as the language is still in deep development. You can see the speculative syntax at https://github.com/thrushlang/syntax.

## Examples

> [!NOTE]  
> This programming language doesn't rely on Clang or GCC to compile without linking; it simply uses them as a gateway to the closest native linker on the system. This is because creating a driver for a specific linker is a very complex task. Many programming languages ​​didn't even have one decades after their development. And this is the reason for the `-clang`, or `-gcc` flag.
 
> [!NOTE]  
> The ``-start`` and ``-end`` flags delimit the parameters to be passed to the currently active link compiler (e.g., Clang or GCC). This is a way to simplify flag processing and, above all, make it independent of the final link compiler.
> 
> It should be noted that in each distribution of the compiler, it will always include a compiled clang for the architecture for which the compiler was compiled so that in the first compilation it installs in `thrushlang/`. If the `-clang` flag is used and no path is specified, the compiler will use the integrated one it has for linking; the same goes for GCC.

### Compiler

#### Linux

```console
mkdir build && ./thrushc -build-dir="build/" -llvm-backend -clang -opt=mcqueen fibonacci.thrush -start -o fibonacci -end && ./fibonacci
```

#### Windows

```console
mkdir build && .\thrushc.exe -build-dir="build/" -llvm-backend -clang -opt=mcqueen fibonacci.thrush -start -o fibonacci.exe -end && .\fibonacci.exe
```

### Linker

The compiler can currently be used directly as a linker. It includes the LLVM Linker, already embedded in the executable, so it requires no external dependencies beyond a C runtime.

In the future, we plan to create wrappers for other linkers to make the compiler completely independent.
In addition, there will be a driver for each.

The example is on Linux with ``.o`` already precompiled:

```console
mkdir build && ./thrushc -build-dir="build/" -llvm-backend -llinker -llinker-flavor=elf --hash-style=gnu --build-id --eh-frame-hdr -m elf_x86_64 -pie -dynamic-linker /lib64/ld-linux-x86-64.so.2 -o a.out /usr/bin/../l
ib64/gcc/x86_64-pc-linux-gnu/15.1.1/../../../../lib64/Scrt1.o /usr/bin/../lib64/gcc/x86_64-pc-linux-gnu/15.1.1/../../../../lib64/crti.o /usr/bin/../lib64/gcc/x86_64-pc-linux-gnu/15.1.1/crtbeginS.o -L
/usr/bin/../lib64/gcc/x86_64-pc-linux-gnu/15.1.1 -L/usr/bin/../lib64/gcc/x86_64-pc-linux-gnu15.1.1/../../../../lib64 -L/lib/../lib64 -L/usr/lib/../lib64 -L/lib -L/usr/lib build/emit/obj/program.o -lg
cc --as-needed -lgcc_s --no-as-needed -lc -lgcc --as-needed -lgcc_s --no-as-needed /usr/bin/../lib64/gcc/x86_64-pc-linux-gnu/15.1.1/crtendS.o /usr/bin/../lib64/gcc/x86_64-pc-linux-gnu/15.1.1/../../..
/../lib64/crtn.o
```

The result is a valid executable, created without external dependencies in relation to the linker, since no external linker and only the Thrush compiler were used.

### Package Manager

In the future, there will be a package manager that works exactly like Rust **Cargo**. Once it is installed in the system path at the root of the project, wherever the **Project.toml** file is located, it will automate the program's build process.

```console
thorium run
```

### Code Example - Hello World

```rust
// ******************************************************************************************
//
//   Hello World!
//
// ******************************************************************************************

// Thrush Programming Language - File extensions
// 
// - '.🐦'
// - '.thrush'
//

// External declaration for the C printf function
fn print(fmt: ptr) s32 @public @ignore @extern("printf");

fn main() u32 {

    print("Hello World!" as ptr);         
    return 0;

}
```

### Code Example - Fibonacci

```rust
// ******************************************************************************************
//
//   Fibonacci - O(2^n)
//
// ******************************************************************************************

// Thrush Programming Language - File extensions
// 
// - '.🐦'
// - '.thrush'
//

// External declaration for the C printf function
fn print(fmt: ptr) s32 @public @ignore @extern("printf");

// Computes the nth Fibonacci number recursively
//
// Parameters:
//   n: The index of the Fibonacci number to compute (unsigned 32-bit integer)
//
// Returns: The nth Fibonacci number (unsigned 32-bit integer)
//
// Attributes:
//   @hot: Marks the function as frequently executed, encouraging aggressive optimizations
//         and placement in a .hot section for better cache locality. Useful for
//         performance-critical code, but may conflict with @minsize.
//   @inline:
//         Maps to LLVM's 'inlinehint', suggesting the compiler inline this function
//         at call sites to reduce call overhead. May increase code size, conflicting
//         with @minsize, and may be limited for deep recursion (e.g., n=25).
//
fn fibonacci(n: u32) u32 @hot @inline {
    if n <= 1 {
        return n;
    }

    return fibonacci(n - 1) + fibonacci(n - 2);
}

// Prints the first n Fibonacci numbers
// Parameters:
//   n: The number of Fibonacci numbers to print (unsigned 32-bit integer)
fn printFibonacci(n: u32) void {
    for local mut i: u32 = 0; i < n; ++i; {
        print("%d\n", fibonacci(i));
    }
}

fn main() u32 {
    print("Fibonacci sequence: " as ptr);         
    printFibonacci(25);            

    return 0;
}
```

General examples of programming language usage can be found: [Examples](https://github.com/thrushlang/thrushc/blob/master/examples)

## Background

In fact, the programming language was originally intended for learning purposes in the compiler field, for the "team" behind the project. However, this doesn't mean it will be __taken as seriously as possible__.

The plan is to offer a full mapping to the entire LLVM-C API and to offer code generation as close to Clang as a C compiler. This also includes future mappings to other backends such as QIR and MLIR, for quantum and more specialized computing, respectively.

The responsible team (practically a *solo developer*) considers it a side, not main, project. We focus on improving both ourselves and our projects in parallel.

## Contribute

We're looking for contributors for our project! If you're a Spanish speaker and would like to contribute, contact us through our official social media channels.
Already know **[Rust](https://www.rust-lang.org/)** but not **[LLVM](https://llvm.org/)**? Don't worry! We're happy to teach you.

### Contributions required

#### Documentation

- If you don't want to get involved with the compiler, you can choose to passively develop the language documentation or syntax repository.

#### Ideas

- If you don't want to get involved with the compiler, you can contribute future ideas to integrate into the language.

Any kind of support is appreciated and will be taken into account.

## Support 

If you'd like to deeply support the development of the language, please consider donating to the team with any contribution or join us in driving the development of this research programming language.

<a href="https://paypal.me/DevCheck" target="_blank" rel="noopener noreferrer">
    <img src="https://img.shields.io/badge/PayPal-00457C?style=for-the-badge&logo=paypal&logoColor=white" alt="Support via PayPal" style="display: inline-block;">
</a>

## Social Networks

[![Thrush Programming Language](https://invite.casperiv.dev?inviteCode=MhVpCSxnhV)](https://discord.gg/MhVpCSxnhV)
































