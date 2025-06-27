<p align="center">
  <img src= "https://github.com/thrushlang/thrushc/blob/master/assets/thrushlang-v1.5.png" alt= "logo" style= "width: 2hv; height: 2hv;"> </img>
</p>

<h1 align="center">Thrush Programming Language</h1>

The **Thrush Programming Language**. A system's programming language that revolutionizes low-level control. 

## Inspiration

- The language is largely based on the syntax of its source language, Rust.
- Its name is Thrush, reminiscent of the **[thrush](https://en.wikipedia.org/wiki/Thrush_(bird))** bird, a relative of the **Turdidae** family. Its pronunciation differs from the bird's name; it's actually T.. Rush, not Thrush.

## Philosophy

### The problem

Systems languages like ``C``, ``C++``, and ``Rust`` have yet to fully explore low-level programming potential, particularly in explicit manipulation of intermediate representations (IRs). Direct IR control empowers developers with seamless, high-level orchestration of assembly-like operations from source code, eliminating the need to resort to raw assembly.

### The Thrush solution 

Thrush empowers developers by enabling IR manipulation through language-integrated Low-Level Instructions (LLI), a high-level, streamlined interface for GCC and LLVM intrinsic instructions, while prioritizing beginners with a future memory-safe abstraction layer built atop its powerful, low-level system.

## Why Thrush?

Thrush is a very promising tool for bare-metal and embedded system development thanks to its innovative low-level instruction concepts, particularly its built-in Low-Level Instructions (LLI) for seamless IR manipulation using GCC and LLVM intrinsics. Prioritizing simplicity, Thrush incorporates a memory-safe abstraction over its powerful low-level system, making it ideal for beginners. Depending on your needs, you could opt for C, C++, or Rust, but Thrush offers a unique combination of control and accessibility while the language matures into a final form.

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

asmfn invoke_exit_syscall() void {
    "mov $$60, %rax",
    "mov $$1, %rdi",
    "syscall"
} { 
    "~{rax}~{rdi}"
}

fn main() {
  invoke_exit_syscall();
}
```

- Thrush enables seamless compile-time code execution, empowering developers to perform computations and optimizations directly during compilation with a simple, intuitive syntax.

```rust
fn comptime_sum(a: u8, b: u8) u16 @compiletime {
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
- Robust Static Typing: Enforce type safety with a strongly statically typed system for reliable, high-performance code with powerful recursive bounds type checking.
- Flexible Unsafe Environment: Harness a complex, unsafe low-level system for maximum control in bare-metal and embedded development.
- C Interoperability: Integrate effortlessly with C codebases, leveraging existing libraries and systems.
- Unified, Lightweight Compiler: A robust, all-in-one compiler designed for simplicity and ease of use.
- Minimal Runtime Overhead (C compiler code generation-like)

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
thrushc -build-dir="build" -llvm -clang fibonacci.th -start -o fibonacci -end
./fibonacci
```

#### Windows

```console
mkdir build
thrushc -build-dir="build" -llvm -clang fibonacci.th -start -o fibonacci.exe -end
.\fibonacci.exe
```

### Package Manager - (Not finished yet)

```console
thorium run
```

### Code Example - Hello World

```rust
fn print(fmt: ptr) s32 @public @ignore @extern("printf");

fn main() {

    local fmt: str = "%s";
    local hello_world: str = "Hello World!";

    print(fmt as ptr, hello_world as ptr);

}
```

### Code Example - 3D Matrix

```rust
/*
 * 3D Matrix Representation (2x2x2) simulated using a one-dimensional array.
 *
 * Element access is performed using a linear index calculation:
 * index = z * (dim_y * dim_x) + y * dim_x + x
 *
 * Where:
 * - z: Index in the Z dimension (depth)
 * - y: Index in the Y dimension (rows)
 * - x: Index in the X dimension (columns)
 * - dim_x, dim_y, dim_z: Total dimensions of the matrix along each axis.
 *
 * This code demonstrates:
 * 1. Initialization of the matrix with predefined values.
 * 2. Iteration over the three dimensions to print each element.
 * 3. Modification of a specific element using a dynamic index and a complex expression.
 * 4. Verification of the modification by reprinting the matrix.
*/

fn print(fmt: ptr) s32 @public @ignore @extern("printf");

fn main() {
    // 2x2x2 u32 matrix (simulated with an 8-element array)
    // [z][y][x]
    local mut cube: array[u32; 8] = fixed[
        10, 11, 12, 13,
        14, 15, 16, 17
    ];

    local cube_fmt: str = "Cube[%ld,%ld,%ld] = %ld\n";
    local cube_modified_fmt: str = "Modified Cube[%ld,%ld,%ld] to %ld\n";
    
    local dim_z: u32 = 2;
    local dim_y: u32 = 2;
    local dim_x: u32 = 2;
    
    // 3D index calculation: z * (dim_y * dim_x) + y * dim_x + x
    local yx_plane_size: u32 = dim_y * dim_x; // 2 * 2 = 4
    
    // Phase 1: Print all elements
    for local mut z_idx: u32 = 0; z_idx < dim_z; ++z_idx; {
        for local mut y_idx: u32 = 0; y_idx < dim_y; ++y_idx; {
            for local mut x_idx: u32 = 0; x_idx < dim_x; ++x_idx; {
                local linear_idx: u32 = (z_idx * yx_plane_size) + (y_idx * dim_x) + x_idx;
                local val: u32 = deref cube[linear_idx];
                print(cube_fmt as ptr, z_idx, y_idx, x_idx, val);
            }
        }
    }
    
    // Phase 2: Assignment with complex expression as index
    // cube[1,0,1] = cube[0,0,0] + (offset_val * 2)
    local target_z: u32 = 1;
    local target_y: u32 = 0;
    local target_x: u32 = 1;
    local target_linear_idx: u32 = (target_z * yx_plane_size) + (target_y * dim_x) + target_x;
    
    local source_z: u32 = 0;
    local source_y: u32 = 0;
    local source_x: u32 = 0;
    local source_linear_idx: u32 = (source_z * yx_plane_size) + (source_y * dim_x) + source_x;
    local source_val: u32 = deref cube[source_linear_idx];
    
    local offset_val: u32 = 5;
    local new_val: u32 = source_val + (offset_val * 2); // Complex expression
    
    cube[target_linear_idx] = new_val; // Assignment with dynamic index
    
    print(cube_modified_fmt as ptr, target_z, target_y, target_x, new_val);
    
    // Phase 3: Print again to verify
    for local mut z_idx_final: u32 = 0; z_idx_final < dim_z; ++z_idx_final; {
        for local mut y_idx_final: u32 = 0; y_idx_final < dim_y; ++y_idx_final; {
            for local mut x_idx_final: u32 = 0; x_idx_final < dim_x; ++x_idx_final; {
                local linear_idx_final: u32 = (z_idx_final * yx_plane_size) + (y_idx_final * dim_x) + x_idx_final;
                local val_final: u32 = deref cube[linear_idx_final];
                print(cube_fmt as ptr, z_idx_final, y_idx_final, x_idx_final, val_final);
            }
        }
    }

    /*
      3D Matrix Simulation Output:
      
      - Cube[0,0,0] = 10
      - Cube[0,0,1] = 11
      - Cube[0,1,0] = 12
      - Cube[0,1,1] = 13
      - Cube[1,0,0] = 14
      - Cube[1,0,1] = 15
      - Cube[1,1,0] = 16
      - Cube[1,1,1] = 17
      - Modified Cube[1,0,1] to 20
      - Cube[0,0,0] = 10
      - Cube[0,0,1] = 11
      - Cube[0,1,0] = 12
      - Cube[0,1,1] = 13
      - Cube[1,0,0] = 14
      - Cube[1,0,1] = 20
      - Cube[1,1,0] = 16
      - Cube[1,1,1] = 17
    */
}
```

## Contribute

We're looking for contributors for our project! If you're a Spanish speaker and would like to contribute, contact us through our official social media channels.
Already know Rust but not LLVM? Don't worry! We're happy to teach you.

## Social Media

[![Thrush Programming Language](https://invite.casperiv.dev?inviteCode=DJaVs4kM9U)](https://discord.gg/DJaVs4kM9U)
