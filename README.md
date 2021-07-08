# Randoml

A cryptographically-secure random number library.
As I can't do system calls in OCaml I am forced to use bindings to a Rust library (to call `getrandom`).

## Installation

You'll need Rust: https://rustup.rs/

Then:

```
$ opam install randoml
```

## Usage

Fill a buffer with random bytes:

```ocaml
let buf = Bytes.create 16 in
rand_fill buf
```

Get a random `int32`:

```ocaml
let x = rand_int32 ()
```

Get a random `int64`:

```ocaml
let x = rand_int64 ()
```

Get a random int32 between 1 and 100000000:

```ocaml
let lower = Int32.of_int_exn 1 in
let upper = Int32.of_int_exn 100000000 in
let x = rand_int32_range lower upper
```

Get a random int64 between 1 and 100000000:

```ocaml
let lower = Int64.of_int_exn 1 in
let upper = Int64.of_int_exn 100000000 in
let x = rand_int64_range lower upper
```

Get a random [Bigint]() upperbounded by some number (warning: it won't work well if your upperbound is not smaller and close to a power of 2):

```ocaml
let upperbound =
Bigint.of_string
    "7067388259113537318333190002971674063309935587502475832486424805170478604"
in
let x = rand_bigint upperbound
```
