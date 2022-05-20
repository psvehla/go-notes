# Go Notes

My notes on Go (YMMV)

## Serialisation and Deserialisation

#### Native (all Go)

Worth exploring: [GORM](https://gorm.io/index.html)

#### JSON

`encoding/json`

## Microservices

### Code Led

### Interface Led

#### OpenAPI
[OpenAPI server generators](https://openapi-generator.tech/docs/generators) are available for net/http, Gin and Echo.

##### go-server

##### go-gin-server

##### go-echo-server

#### gRPC

#### GraphQL

### Design Led

[goa](https://goa.design/) takes another approach: what they call 'design led'. The philosophy here is similar to Interface Led microservice builds, yet instead of defining the interface first, the interface design is expressed in a goa specific DSL. The interfaces themselved are then generated from the DSL (e.g. [OpenAPI](https://goa.design/v1/reference/goa/codegen/generator/), gRPC). Microservice code can also be generated from the DSL. Plugins provide control over how the code is generated. The most promising one appears to be go-kit, which generates [Go kit](https://gokit.io/) compliant services.

#### Goa with Go kit

[A hello service.](https://github.com/psvehla/hello-goakit)

- The DSL is easy to understand and expressive. You define all your protocols in one place.
- The generated code is nicely laid out, easy to understand and 'just works'.
- A big labour saver if you're implementing multiple protocols.
- No Dockerfile, but it's easy to make one.
- Won't fly if you have to start with and OpenAPI definition. There's no way to generate from OpenAPI, you must begin with a design file expressed in the DSL.

#### Worth Exploring

##### goa

##### Go kit

## Authorisation

Worth exploring: [Casbin](https://github.com/casbin/casbin)
