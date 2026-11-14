# grpc-learning-lab

Hands-on, phase-by-phase exploration of gRPC, built from first principles by someone coming from a REST/microservices background. Each folder is a standalone, runnable piece covering one concept, progressing from basic unary calls to a small multi-service capstone.

## Why this repo exists

I've built and called plenty of microservices over REST. This repo is me doing the same thing over gRPC, on purpose, concept by concept, so I actually understand the tradeoffs instead of just repeating buzzwords, streaming types, deadlines/cancellation, interceptors, schema evolution, and how gRPC compares to REST in practice (with real benchmark numbers, not guesses).

## Stack

- Python (`grpcio`, `grpcio-tools`)
- Protocol Buffers (`protoc` / `buf`)
- `grpcurl` for client-less debugging via server reflection
- `grpc-gateway` (or a hand-rolled proxy) for the REST bridge phase
- `ghz` for load testing

## Phases

| Phase | Folder | Concept |
|---|---|---|
| 0 | `00-setup` | Toolchain: protoc/buf, grpcio, grpcurl |
| 1 | `01-unary-basics` | First `.proto`, generated stubs, servicer/channel vocabulary |
| 2 | `02-real-unary-service` | A real unary server + client, compared mentally to Flask/FastAPI equivalent |
| 3 | `03-streaming` | Server streaming, client streaming, bidirectional streaming |
| 4 | `04-errors-status-codes` | gRPC status codes vs HTTP status codes |
| 5 | `05-deadlines-cancellation` | Multi-hop deadline propagation and cancellation |
| 6 | `06-interceptors` | Logging + auth interceptors (unary and streaming) |
| 7 | `07-security-tls-auth` | TLS, mTLS, token auth via metadata |
| 8 | `08-reflection-grpcurl` | Server reflection, calling a service with no generated client |
| 9 | `09-rest-gateway-bridge` | Exposing a gRPC service over REST/JSON via a gateway |
| 10 | `10-schema-evolution` | Breaking and correctly evolving proto messages |
| 11 | `11-rest-vs-grpc-benchmark` | Same service built twice, load-tested with `ghz` |
| 12 | `capstone` | Multiple services + one REST gateway + auth, tied together |

*(Infra-heavy topics — k8s health probes, service-mesh load balancing, full observability stacks — are covered as notes/write-ups rather than full deployments; noted inline where relevant.)*

## Status

🚧 Work in progress — building this phase by phase. See each folder's own README for what's done and how to run it.

## Running any phase

\`\`\`bash
cd <phase-folder>
# proto generation and run instructions are in each phase's own README
\`\`\`

## Notes

This is a learning repo, not a production template, some phases intentionally leave rough edges to make a point.
