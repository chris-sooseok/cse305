# Stack-Language Interpreter (OCaml)

An interpreter for a small stack-based programming language, written in OCaml for CSE 305
(Programming Languages). The interpreter reads a program — one command per line — from an input
file, executes it against an operand stack, and writes anything the program prints to an output
file. Invalid operations push an `:error:` marker rather than crashing.

The full implementation is `project/interpreter.ml`. The language spec is `interpreter.pdf`.

### The language

Built up over three parts:

- **Part 1 — stack and values.** Integers, booleans (`:true:` / `:false:`), quoted strings,
  names, and unit. Commands: `push`, `pop`, `add`, `sub`, `mul`, `div`, `rem`, `neg`, `swap`,
  `toString`, `println`, `quit`.
- **Part 2 — logic and binding.** `cat` (string concat), `and`, `or`, `not`, `equal`,
  `lessThan`, `bind` (bind a name to a value), `if`, and `let` / `end` for nested scopes.
- **Part 3 — functions.** `fun` / `funEnd` / `return` / `call` with first-class closures that
  capture their defining environment.

### Example

Input:

```
push 10
push 17
lessThan
toString
println
quit
```

Output:

```
:true:
```

### Running

```bash
cd project
ocaml interpreter.ml
```

The bottom of `interpreter.ml` contains driver calls that run the bundled test cases
(`part2input/*.txt` → `part2output/my_output*.txt`); edit those lines to point at your own
input/output files. Expected outputs for each fixture are in the matching `*output*` folders.

### Also in this repo

`Ocaml/` and `ocaml-basic/` hold course notes and OCaml practice (grammar, scoping, subprograms,
concurrency).
