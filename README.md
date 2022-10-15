# Go Notes

My notes on Go (YMMV)

## Tooling

### Vulnerability Scanning

[govulncheck](https://go.dev/blog/vuln)

## Serialisation and Deserialisation

### Native (all Go)

Worth exploring: [GORM](https://gorm.io/index.html)

### JSON

`encoding/json`

## Microservices

### Code Led

#### Go kit

[Go kit](https://gokit.io/) is a proper, grown up service development framework for developing proper, grown up services. It defines a separation of concerns that allows communication details and business logic to be kept apart. It applies a decorator pattern for this layering, simplifying the insertion of layers for logging, tracing, observability and other such grown up things.

I've been quite pleased with the results when using this framework to build services that interfaced with multiple queues (sending and receiving messages) as well as calling other synchronous services. What these services didn't have was a traditional RESTful API. For services that required such an API I used go-echo-server instead, since I was starting with an OpenAPI spec and the generator gave me quite a start. However, I couldn't help feeling that the result was somewhat amateurish compared to the Go kit service.

TODO: I'd like to try grafting go-server to Go kit. go-server's approach to how it displays unimplemented routes is the most professional, however it doesn't give you much more in terms of application framework. But if I rely on Go kit for all that, it could be a winner.

### Interface Led

#### OpenAPI

[OpenAPI server generators](https://openapi-generator.tech/docs/generators) are available for net/http, Gin and Echo.

##### go-server

[A hello service.](https://github.com/psvehla/hello-http)

- No fuss code generation.
- Generated code doesn't always build, but the problems are super easy to fix.
- Generated code is clear, simple and easy to reason about.
- How to proceed after generating the code is well documented *in the code*.
- Dockerfile included, though it needs updating.
- Unimplemented routes behave well, with correct return codes and a helpful message.

##### go-gin-server

[A hello service.](https://github.com/psvehla/hello-gin)

- No fuss code generation.
- Generated code doesn't always build, but the problems are easy to fix.
- Generated code is clear, simple and easy to reason about.
- Dockerfile included, though it needs updating.
- Unimplemented routes return with 200 and an empty JSON.
- Great doco, lots of examples on how to do various things.

##### go-echo-server

[A hello service.](https://github.com/psvehla/hello-echo)

- No fuss code generation.
- Generated code doesn't always build, but the problems are easy to fix.
- Generated code is clear, simple and easy to reason about.
- Dockerfile included, though it needs updating.
- Unimplemented routes return with 200 and a 'Hello World' message.
- Great doco, lots of examples on how to do various things.
- Includes a mechanism for injecting dependencies.

#### gRPC

#### GraphQL

### Design Led

[goa](https://goa.design/) takes another approach: what they call 'design led'. The philosophy here is similar to Interface Led microservice builds, yet instead of defining the interface first, the interface design is expressed in a goa specific DSL. The interfaces themselved are then generated from the DSL (e.g. [OpenAPI](https://goa.design/v1/reference/goa/codegen/generator/), gRPC). Microservice code can also be generated from the DSL. Plugins provide control over how the code is generated. The most promising one appears to be [goakit](https://github.com/goadesign/plugins/tree/v3/goakit), which generates [Go kit](https://gokit.io/) compliant services.

#### Goa with goakit

[A hello service.](https://github.com/psvehla/hello-goakit)

- The DSL is easy to understand and expressive. You define all your protocols in one place.
- The generated code is nicely laid out, easy to understand and 'just works'.
- A big labour saver if you're implementing multiple protocols.
- No Dockerfile, but it's easy to make one.
- Won't fly if you have to start with and OpenAPI definition. There's no way to generate from OpenAPI, you must begin with a design file expressed in the DSL.

#### Other Players

#### fiber

Seems to tout speed as a prime advantage. No generator available, not net/http compatible.

## Authorisation

Worth exploring: [Casbin](https://github.com/casbin/casbin)

Worth exploring: [OPA](https://www.openpolicyagent.org/)
