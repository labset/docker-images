# syntax=docker/dockerfile:1

# buf-toolchain: buf CLI + OpenAPI v3 generation (google/gnostic protoc-gen-openapi)
#
# Build:   docker build -t buf-toolchain buf-toolchain
# Usage:   docker run --rm -v "$PWD:/workspace" buf-toolchain generate

# ---- builder: install the toolchain via go ---------------------------------
FROM golang:1.25-alpine AS builder

ARG BUF_VERSION=v1.72.0
ARG GNOSTIC_VERSION=v0.7.0

ENV CGO_ENABLED=0
RUN go install "github.com/bufbuild/buf/cmd/buf@${BUF_VERSION}" \
    && go install "github.com/google/gnostic/cmd/protoc-gen-openapi@${GNOSTIC_VERSION}"

# ---- runtime: minimal image with just the toolchain ------------------------
FROM alpine:3.20

# ca-certificates for BSR access; git for buf module dependency resolution.
RUN apk add --no-cache ca-certificates git \
    && adduser -D -u 1000 buf

COPY --from=builder /go/bin/ /usr/local/bin/

USER buf
WORKDIR /workspace

ENTRYPOINT ["buf"]
CMD ["--help"]
