# xoctopus

**Composable Go modules for building backend services, from type analysis and
code generation to runtime and application assembly.**

xoctopus is not a single framework. Each module solves one problem and can be
used alone, while together they form a consistent stack: types are the shared
foundation, and generated code replaces repetitive boilerplate.

## Architecture

```text
Application   confx                configuration, lifecycle, infrastructure
Runtime       httpx  sqlx  concx   HTTP, SQL, concurrency
Generation    genx                 AST-aware code generation
Language      typx  pkgx           Go type and package analysis
Foundation    x  logx  sfid        utilities, logging, IDs
```

Layers describe each module's role, not a strict import order.

## Modules

| Module                                     | Purpose                                                    |
|--------------------------------------------|------------------------------------------------------------|
| [confx](https://github.com/xoctopus/confx) | Typed configuration, app lifecycle, and service components |
| [httpx](https://github.com/xoctopus/httpx) | HTTP routing, request binding, validation, and OpenAPI     |
| [sqlx](https://github.com/xoctopus/sqlx)   | Typed SQL builder, model generation, and migration         |
| [concx](https://github.com/xoctopus/concx) | Goroutine lifecycles, schedulers, pipelines, and cron      |
| [genx](https://github.com/xoctopus/genx)   | Directive-driven generation of enums, errors, and more     |
| [typx](https://github.com/xoctopus/typx)   | One type model over `reflect.Type` and `go/types`          |
| [pkgx](https://github.com/xoctopus/pkgx)   | Semantic inspection of Go packages and doc comments        |
| [x](https://github.com/xoctopus/x)         | Generic utilities, typed error codes, and test matchers    |
| [logx](https://github.com/xoctopus/logx)   | Context-aware logging with std and zap backends            |
| [sfid](https://github.com/xoctopus/sfid)   | Snowflake-style distributed ID generation                  |
| [devx](https://github.com/xoctopus/devx)   | Generated Makefiles, Dockerfiles, CI, and lint config      |

## Highlights

- **Type-driven**: configuration, HTTP requests, and SQL models are declared as
  Go types, and behavior follows from them.
- **Generated, not hand-written**: source directives such as `// +genx:model` and
  `// +genx:enum` produce the repetitive code.
- **Fail fast**: components validate configuration and dependencies at startup.
- **Multiple SQL dialects**: sqlx includes MySQL, PostgreSQL, and SQLite adaptors.
- **Observable**: structured logging, OpenTelemetry, and metrics are built in.

## Getting started

Start with [confx](https://github.com/xoctopus/confx) to assemble a service, then
add only the modules you need. Each one is a standalone Go module:

```sh
go get github.com/xoctopus/confx
go get github.com/xoctopus/httpx
go get github.com/xoctopus/sqlx
```

Examples:

- [Application assembly](https://github.com/xoctopus/confx/tree/main/example/appx)
- [HTTP service](https://github.com/xoctopus/httpx/tree/main/example)
- [SQL models](https://github.com/xoctopus/sqlx/tree/main/example)

## Status

The modules require Go 1.27.3 or later and are pre-1.0, so APIs may change between
minor versions. Each repository publishes its own tagged versions and changelog.

## License

The libraries are released under the
[MIT License](https://github.com/xoctopus/.github/blob/main/profile/LICENSE).
