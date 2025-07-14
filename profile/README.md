<p align="center">
  <img src= "https://github.com/thrushlang/thrushc/blob/master/assets/thrushlang-v1.6.png" alt= "logo" style= "width: 2hv; height: 2hv;"> </img>
</p>

<h1 align="center">Thrush Programming Language</h1>

<p align="center">The <b>Thrush Programming Language</b>. A system's programming language that provides complete low-level control.</p>

## Inspiration

- The syntax of the programming language is mainly inspired by the father of the promodial compiler, Rust. However, it does not inherit its functions and innovations up to this point.
- This language is based on its lowest expression in C.
- Inspired by the low-level capabilities of C.

### Inspiration Name

Its name is Thrush, reminiscent of the **[thrush](https://en.wikipedia.org/wiki/Thrush_(bird))** bird, a relative of the **Turdidae** family.<br>Its pronunciation differs from the bird's name; it's actually **T**.. **Rush**, not Thrush.

#### Why this bird?

The **[thrush](https://en.wikipedia.org/wiki/Thrush_(bird))** bird possesses one of the most complex, coordinated, and wonderful songs in the animal world, standing out in a specific area.

As an analogy.

Thrush is a very expressive and specific language for low-level programming, excelling in memory control, arithmetic operations, assembly, and much more at a low level. It offers a complex type layer to reduce possible runtime errors.

## Philosophy

Thrush empowers developers to create software with complete low-level control. This approach enhances robustness, optimizes performance, and simplifies code development for diverse, even exotic, architectures, directly addressing limitations found in many current systems programming languages.

## Why Thrush?

Thrush is a very promising tool for bare-metal and embedded system development thanks to its innovative low-level instruction concepts, particularly its integrated Low-Level Instructions (LLI) for fluent IR manipulation using GCC and LLVM intrinsics. This prioritizes and encourages learning intermediate code, rather than assembler code, unlocking architecture-specific optimizations and low-level type manipulation. Thrush offers low-level control over systems languages ​​like C, Rust, and C++ due to its manipulation of low-level instructions for optimizations beyond the standard ones. Thrush strives to inherit the type systems of highly typed languages, promoting reliable and robust software.

### Low Level Control

- Thrush empowers developers to compile low-level instructions directly to a specified target from source code, enabling precise, architecture-specific optimization with unparalleled ease.

```rust
compile @target("armv7e-m") @asm @entrypoint @output("example.s") {
  instr allocated_u8: ptr[u8] = alloc @stack, { u8 };
  write allocated_u8, u8 8;
};
```

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

## Features

- Code Generation Control.
- Robust Static Type Checking.
- Flexible Unsafe Environment.
- C Simplicity.
- C Interoperability.
- Native Assembler Interoperability.

## Goals

- The Thrush Compiler has the ability to output pre-compiled object files ``.o`` for the architecture as well as assembler and its counterparts without going through the pass manager for optimization.
- The Thrush Compiler is very lightweight ``20``MB, considering that it contains embedded Clang for Linux and Windows, to be used as a wrapper to the closest linker.

## State

- The Thrush Compiler ``thrushc``: The Thrush Compiler is still in active development. We're currently focused on building out its complex layer of low-level instructions and developing a robust linter.
- The Thrush Package Manager ``thorium``: The package manager has already begun development but is not yet complete.

> [!NOTE]  
> If you want to accelerate the speed of language development, please consider **donating** to the creator or joining us and carrying out the language.

## Documentation

The documentation isn't ready yet, as the language is still in deep development. You can see the speculative syntax at https://github.com/thrushlang/syntax.

## Examples

> [!NOTE]  
> This programming language doesn't rely on Clang or GCC to compile without linking; it simply uses them as a gateway to the closest native linker on the system. This is because creating a driver for a specific linker is a very complex task. Many programming languages ​​didn't even have one decades after their development. And this is the reason for the `-clang`, or `-gcc` flag.

### Compiler

#### Linux

```console
mkdir build
thrushc -build-dir="build" -llvm -clang hello.thrush -start -o hello -end
./hello
```

#### Windows

```console
mkdir build
thrushc -build-dir="build" -llvm -clang hello.thrush -start -o hello.exe -end
.\hello.exe
```

### Package Manager - (Not finished yet)

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

[![Thrush Programming Language](https://invite.casperiv.dev?inviteCode=DJaVs4kM9U)](https://discord.gg/DJaVs4kM9U)
