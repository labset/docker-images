# docker-images

A collection of small, purpose-built Docker images.

## buf-toolchain

A toolchain image for OpenAPI v3 codegen, shipping:

- [`buf`](https://github.com/bufbuild/buf) — the buf CLI.
- [`protoc-gen-openapi`](https://github.com/google/gnostic/tree/main/cmd/protoc-gen-openapi) — gnostic's OpenAPI v3 generator plugin.

Build:

```bash
docker build -t buf-toolchain buf-toolchain
```

Run:

```bash
docker run --rm -v "$PWD:/workspace" buf-toolchain generate
```
