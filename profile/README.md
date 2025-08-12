<p align="center">
  <img src= "https://github.com/thrushlang/thrushc/blob/master/assets/thrushlang-v1.6.png" alt= "logo" style= "width: 2hv; height: 2hv;"> </img>
</p>

<h1 align="center">Thrush Programming Language</h1>

<p align="center">The <b>Thrush Programming Language</b>. A system's programming language that provides complete low-level control.</p>

## Inspiration

### Characteristics

- Syntactically it is based on Rust.
- This language is based on its lowest expression in C.
- Inspired by the low-level capabilities of C.

### Inspiration Name

Its name is Thrush, reminiscent of the **[thrush](https://en.wikipedia.org/wiki/Thrush_(bird))** bird, a relative of the **Turdidae** family.<br>Its pronunciation differs from the bird's name; it's actually **T**.. **Rush**, not Thrush.

#### Why this bird?

The **[thrush](https://en.wikipedia.org/wiki/Thrush_(bird))** bird possesses one of the most complex, coordinated, and wonderful songs in the animal world, standing out in a specific area.

This is an analogy.

Thrush is a very expressive and specific language for low-level programming, excelling in memory control, arithmetic operations, assembly, and much more at a low level. It offers a complex type layer to reduce possible runtime errors.

## Philosophy

Thrush empowers developers to create software with complete low-level control. This approach enhances robustness, optimizes performance, and simplifies code development for diverse, even exotic, architectures, directly addressing limitations found in many current systems programming languages.

## Why Thrush?

Thrush is a very promising tool for bare-metal and embedded system development thanks to its innovative low-level instruction concepts, particularly its integrated Low-Level Instructions (LLI) for fluent IR manipulation using GCC and LLVM intrinsics. This prioritizes and encourages learning intermediate code, rather than assembler code, unlocking architecture-specific optimizations and low-level type manipulation. Thrush offers low-level control over systems languages ​​like C, Rust, and C++ due to its manipulation of low-level instructions for optimizations beyond the standard ones. Thrush strives to inherit the type systems of highly typed languages, promoting reliable and robust software.

### Low Level Control

- Thrush enables seamless integration of low-level instructions alongside their high-level counterparts, allowing developers to fluidly switch between abstraction levels within the same codebase.

```rust
fn main() u32 {

    local number: u8 = 0;

    // Low-level instruction for direct memory access.
    instr loaded_value: u8 = load u8, number;

    return 0;

}
```

- Thrush enables seamless embedding of linear assembler within the compilation process, offering direct, streamlined control over architecture-specific code generation.

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

- Thrush enables seamless compile-time code execution, empowering developers to perform computations and optimizations directly during compilation with a simple, intuitive syntax.

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

- And many more unique features when the language base is finished! ~ Kevin Benavides

## Current Features

- Code Generation Control.
- Robust Static Type Checking.
- Flexible Unsafe Environment.
- C Simplicity.
- C Interoperability.
- Native Assembler Interoperability.

## Future Features

- Automatically generated types for C headers (**CBindgen**).
- Quantum code generation, through QIR and CIR.
- Support for quantum behavior emulation with embedded XQCOR, or a bytecode runner.

## Goals

- The Thrush Compiler has the ability to output pre-compiled object files ``.o`` for the architecture as well as assembler and its counterparts without going through the pass manager for optimization.
- The Thrush Compiler is very lightweight ``20``MB, considering that it contains embedded Clang for Linux and Windows, to be used as a wrapper to the closest linker.

## State

- The Thrush Compiler ``thrushc``: The Thrush compiler is still under development. Currently, we are focusing on developing its complex low-level instruction layer, optimizations in code generation, and a Clang-like C-style generation around LLVM.
- The Thrush Package Manager ``thorium``: The package manager has already begun development but is not yet complete.

> [!NOTE]  
> If you want to accelerate the speed of language development, please consider **donating** to the creator or joining us and carrying out the language.

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
mkdir build && ./thrushc -build-dir="build" -llvm -clang hello.thrush -start -o hello -end && ./hello
```

#### Windows

```console
mkdir build && .\thrushc.exe -build-dir="build" -llvm -clang hello.thrush -start -o hello.exe -end && .\hello.exe
```

### Package Manager - (Not finished yet)

In the future, there will be a package manager that works exactly like Rust **Cargo**. Once it is installed in the system path at the root of the project, wherever the **Project.toml** file is located, it will automate the program's build process.

```console
thorium run
```

### Code Example - Hello World

```rust
fn print(fmt: ptr) s32 @public @ignore @extern("printf");

fn main() u32 {

    print("Hello World!" as ptr);
    return 0;

}
```

General examples of programming language usage can be found: [Examples](https://github.com/thrushlang/thrushc/blob/master/examples)

## Contribute

We're looking for contributors for our project! If you're a Spanish speaker and would like to contribute, contact us through our official social media channels.
Already know Rust but not LLVM? Don't worry! We're happy to teach you.

### Contributions required

#### Documentation

- If you don't want to get involved with the compiler, you can choose to passively develop the language documentation or syntax repository.

#### Ideas

- If you don't want to get involved with the compiler, you can contribute future ideas to integrate into the language.

Any kind of support is appreciated and will be taken into account.

## Social Networks

[![Thrush Programming Language](https://invite.casperiv.dev?inviteCode=MhVpCSxnhV)](https://discord.gg/MhVpCSxnhV)












