# http-server

This example is built using the [WASI Preview 2 API](https://github.com/WebAssembly/wasi-http)
with the [waki](https://github.com/wacker-dev/waki) library.

## Build

Requires Rust 1.82+.

```
$ rustup target add wasm32-wasip2
```

Use the following command to compile it into a WASM program:

```
$ cargo build
```

Or use `--release` option to build it in release mode:

```
$ cargo build --release
```

## Run

After compilation, you can use [wasmtime](https://github.com/bytecodealliance/wasmtime) to run it:

```
$ wasmtime serve -S cli target/wasm32-wasip2/debug/http_server.wasm
Serving HTTP on http://0.0.0.0:8080/
```

```
$ curl http://localhost:8080/
Hello, WASI!

$ curl http://localhost:8080/?name=ia
Hello, ia!
```
