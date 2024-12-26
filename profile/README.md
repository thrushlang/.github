<p align="center">
  <img src= "https://github.com/thrushlang/.github/blob/main/assets/Thrush.png" alt= "logo" style= "width: 2hv; height: 2hv;"> </img>
</p>

<h1 align="center">Thrush Programming Language</h1>

**Thrush Programming Language** is **Strongly Statically Typed**, **Compiled**, **High Level** and **Memory Safety** Programming Language to emit optimal binaries for each architecture. Built with **[LLVM](https://llvm.org/)** Compiler Tools.

## Performance 

Thrush use the minimal **C Runtime** the which improve the performance in comparison with anothers languages, we don't use a **C++ Runtime** and the standard library as **Rust Programming Language** the than which improve the performance with the lowest abstraction, but always is the highly level representation of Assembler.

But in comparison with C and anothers modern languages Thrush compile a **Rich message** in each possible memory breach or overflow in an exact primitive type, that message mean more easy to debug runtime problems for the programmers. The all panics in Runtime will contain a rich message to easy to debug the code.

In common arithmetic **Thrush** need the same time than C in resolve problems, but sometimes the **C compiler is too smart** and calculates the result in still compile time. The current Thrush is don't to able to use that powerful skill in compile time.

## Cross Compilation

Thrush as Rust they use the **[LLVM](https://llvm.org/)** Infraestructure for compile to specific target architecture, enabling the **cross-compilation** completly independent to current host. In addition enabling development of the huge capatibilities for the future.

## Common Compilation Steps

*With the Compiler...*

> `thrushc --executable main.th -o main && output/dist/main`

*With the Package Manager...* (**Coming Soon**)

> `thorium build && output/dist/main`

```
fn main() {

    var hello: string = "Hello World!";

    println("%s", hello);

}
```

## Social Networks

[![](https://dcbadge.limes.pink/api/server/https://discord.gg/DJaVs4kM9U)](https://discord.gg/DJaVs4kM9U)
