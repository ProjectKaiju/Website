# What is Project Kaiju

Project Kaiju is the incubator for a set of Rust-based technologies for creating a forward thinking and modern World Wide Web.

## What Does it Do

First thoughts center around a hosted service that provides the communication mechanims, such as IIS to minimize wheel reinvention.  There will be three pieces initially:

1. [Godzilla Sever](https://projectkaiju.github.io/Godzilla/) - Hosted by IIS or another webserver, establishes new connections via HTTP(S) and generates an initial page.  The page sets up a WebSocket pipeline for persistent commenication between browser and server.  DOM generation is handled by Godzilla and the HTML is sent via TOML documents up the Web Socket.
2. The Javascript listener, named the [Mothra Javascript Client](https://projectkaiju.github.io/Mothra/), manipulates the DOM based on the TOML contents.
3. Event handlers are written in Rust and are compiled to WASM.  New event handlers can be sent via the TOML messages and hydrated by the [Kong WASM Client](https://projectkaiju.github.io/Kong/).  The [Rust-based event handlers]() allow for complex logic to happen in the client, especially validation logic and supporting interactive HTML where large sets of data may need to be [shaped and/or filtered]().  Events that result in new HTML send a message via [WebSocket to Godzilla]() to retrive and prepare the backend resources as HTML.
