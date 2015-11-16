racerd
======

JSON/HTTP API for [racer][]. The project's primary goal is supporting Rust in
[YouCompleteMe][].

[Documentation][]

## Status

```rust
fn is_it_ready() -> bool {
    false
}
```

## ycmd protocol notes

_ycmd_ has an example client which logs HTTP requests and responses. The
(slightly annotated with markdown fences) output of the client is in
[YCMPROTO.md][]. The completions and events APIs should be instructive for
designing a racer service.

[YouCompleteMe]: https://github.com/Valloric/YouCompleteMe
[YCMPROTO.md]: YCMPROTO.md
[racer]: https://github.com/phildawes/racer

## Building

Requires nightly rust to satisfy racer

### OSX Issues

If errors are encountered building openssl or openssl-sys on MacOSX, that
may be because you are running version 10.11 which dropped the system
provided OpenSSL. Note that if the pkg-config call below fails, you can install
openssl via homebrew.

First, check that pkg-config knows about openssl. This command will be silent if
openssl is available.

```sh
pkg-config --print-errors openssl
```

If necessary, run `brew install openssl`. The next snippet sets environment
variables for use during racerd compilation.

```sh
export OPENSSL_LIB_DIR=$(pkg-config --variable=prefix openssl)/lib
export OPENSSL_INCLUDE_DIR=$(pkg-config --variable=prefix openssl)/include
```

[Documentation]: http://jwilm.github.io/racerd/libracerd/
