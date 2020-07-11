# Gleam Elli!

A Gleam HTTP service adapter for the Elli web server.

```rust
import gleam/elli
import gleam/http.{Request, Response}
import gleam/bit_builder.{BitBuilder}
import gleam/bit_string

// Define a HTTP service
//
pub fn my_service(req: Request(BitString)) -> Response(BitBuilder) {
  let body = "Hello, world!"
    |> bit_string.from_string
    |> bit_builder.from_bit_string

  http.response(200)
  |> http.prepend_resp_header("made-with", "Gleam")
  |> http.set_resp_body(body)
}

// Start it on port 3000!
//
pub fn start() {
  elli.start(my_service, on_port: 3000)
}
```
