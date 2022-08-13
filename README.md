# Ker

Ker is an interactive theorem prover for certified programming and formal math.
Inspired by Lean and Coq, Ker should bear the following attributes.
1. Dependent types
2. Unicode identifiers and operators
3. Proof tactics
4. Hygienic macros that are strongly typed and reflects the language syntax
5. Literate programming (VSCode notebook)
6. A very lean kernel and a very lean prelude (prelude can be turned off)
7. Transpile to Rust and Rust FFI
8. Bootstrap with Rust, and eventually self-bootstrap

A well-written program should contain no accidental complexity and be structured
so clearly that lends itself to instant formal verification by just providing a
few extra annotations manually. Formal verification thus removes the need for
unit tests. Formal specification avoids contradictory features and communicates
the actual behavior of programs.

If low-level imperative code can be formally verified easily, we can more
frequently attempt very obscure but efficient optimizations that are often
dreaded due to our inability to follow through complex low-level logic.

People that want to ship fast and never look back can do it even faster, as
whatever spaghetti code one is raced to produce will guarantee to work without
testing and review.

Writing mathematical proofs could be assisted by a smart program that takes a
lot hints.

## Unique Features

- First class DSL support. Custom DSL parsers leverage the Ker parser for code
  reuse. DSLs can be prototyped in interpreted mode then compiled to native code
  with the Ker compiler later.
- Ker can always introduce breaking changes to the language, but users need not
  require backward-compatibility, as migration to newer versions of Ker syntax
  and standard libraries can be done automatically with Ker's linter. The code
  transformation rules provided by Ker's linter is formally verified with Ker.
  All in all, the Ker language can introduce a breaking change as long as there
  is a corresponding automated formal code migration rule.
- Ker should allow very context-dependent name resolutions, to the extent of
  customizing juxtaposition as operator alias.
- Don't separate notations from named definitions contrary to Lean's separation
  of `And` and `∧`. Definitions should be annotated with mixfix, precedence, and
  associativity instead of using type classes.
- Type classes should be registered with operators instead of the
  type-of-discourse to avoid duplications of multiplicative groups and additive
  groups as found in Mathlib of Lean.
- Support LaTeX display.
- Very rich hint in the editor.
- The `def` keyword is unnecessary by treating any top-levels as defintitions,
  definitions are organized as a DAG like in
  [Observable](https://observablehq.com/). This enables non-linear presentation
  of code which makes literate programming possible.
- Support Rust-like imperative programming that are accompanied by correctness
  proofs.
- Code should carry proof and complexity information so that the $O(n \log n)$
  time complexity of merge sort could be proved easily in practice. Hence, time
  and space complexities could be formally specified and verified.
- Customizable debugging experience that utilizes Web technology for visualizing
  algorithms etc.
- Higher inductive types and cubical/HoTT?
- LLVM/GCC backend?