## Stack
Go (version from go.mod), flagd service implementation, OpenFeature SDK, gRPC/protobuf, Docker

## Constraints
- `go.sum` — never modify directly
- `vendor/` — do not edit vendored code
- Any `*.pb.go` files — generated protobuf code
- `*.gen.go` files — any other generated code
- Credential or secret files (`.env`, `*secret*`, `*key*`)
- Migration files if present under `db/` or `migrations/`

## Conventions
- Go standard project layout: `cmd/`, `pkg/`, `internal/`
- Tests live alongside source files as `*_test.go`
- Test naming: `TestXxx` functions in the same package or `_test` package variant
- Dockerfiles are linted; follow existing style and use pinned base image digests where present
- SPDX license headers required on all source files: `// SPDX-License-Identifier: Apache-2.0`
- One package per directory; exported symbols documented with godoc comments

## Dependency manifests
- `go.mod` — module definition and direct dependency versions
- `go.sum` — checksum database (never edit manually)
- `Dockerfile` / `Dockerfile.*` — base image versions; pin by digest when updating
