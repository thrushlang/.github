<p align="center">
  <img src= "https://github.com/thrushlang/.github/blob/main/assets/Thrush.png" alt= "logo" style= "width: 2hv; height: 2hv;"> </img>
</p>

<h1 align="center">Thrush Programming Language</h1>

**Thrush Programming Language** is strongly statically typed, AOT native compiled, highly optimized, general-purpose programming language to build maintainable software.

## Features 

- High level abstraction as Java and C#.
- Non implicit cast for primitive types.
- Strongly statically typed.
- Strongly in POO paradigm as Java.
- Minimal Runtime is equal so tiny executables.
- Faster as C.
- Native compiled.

## Cross Compilation

Thrush as Rust they use the **[LLVM](https://llvm.org/)** Infraestructure for compile to specific target architecture, enabling the **cross-compilation** completly independent to current host. In addition enabling development of the huge capatibilities for the future.

## Common Compilation Steps

*With the internal compiler (thrushc)...*

> `thrushc --executable hello.th -o hello && ./output/hello`

*With the package manager...* (**Coming soon**)

> `thorium run`

```
public @extern("printf") fn print(fmt :: String, ...): i32;

fn main() {

    print("Hello World!")

}
```

## Social Networks

[![](https://dcbadge.limes.pink/api/server/https://discord.gg/DJaVs4kM9U)](https://discord.gg/DJaVs4kM9U)
