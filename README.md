# Go Notes

My notes on Go (YMMV)

## Serialisation and Deserialisation

#### Native (all Go)

Worth exploring: [GORM](https://gorm.io/index.html)

#### JSON

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

#### Worth Exploring

##### goa

##### Go kit

## Authorisation

Worth exploring: [Casbin](https://github.com/casbin/casbin)
