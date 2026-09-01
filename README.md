# docker-images

A collection of small, purpose-built Docker images.

## buf-toolchain

`buf` CLI + `protoc-gen-openapi` (gnostic) for OpenAPI v3 codegen.

Build:

```bash
docker build -t buf-toolchain buf-toolchain
```

Run:

```bash
docker run --rm -v "$PWD:/workspace" buf-toolchain generate
```
