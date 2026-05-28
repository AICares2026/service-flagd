## Stack
Go (see go.mod for version), flagd feature flag daemon, OpenFeature SDK, gRPC/protobuf, Docker

## Constraints
- `go.sum` — lock file, never edit manually
- `*.pb.go` — protobuf generated code, do not modify
- `vendor/` — if present, do not edit contents directly
- `config/` — credential or environment config files
- Any file matching `*_generated.go`
- Migration files if present under `migrations/`

## Conventions
- Tests live alongside source files as `*_test.go` in the same package directory
- Test files use standard `testing` package; table-driven tests preferred
- Binary entrypoints under `cmd/`
- Core logic under `pkg/` or `internal/`
- Dockerfile(s) at repo root or under `build/`; use specific base image digests when hardening
- Go module path defined in `go.mod` — match it exactly in new files

## Dependency manifests
- `go.mod` — primary Go dependency manifest, edit this to update dependencies
- `go.sum` — checksum file, regenerated automatically via `go mod tidy`, never edit directly

## Workflow notes
- After changing `go.mod`, run `go mod tidy` to sync `go.sum`
- Run `go build ./...` and `go test ./...` to verify changes compile and pass
- CVE and dependency update PRs must only touch `go.mod` (and resulting `go.sum` after tidy)
- Dockerfile changes must not remove existing `USER` directives or downgrade to `latest` tags
