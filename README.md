## Lab 4


# lab-04.js
```
// Require the Fastify framework and instantiate it
const fastify = require("fastify")();
// Handle GET verb for / route using Fastify
// Note use of "chain" dot notation syntax
fastify.get("/", (request, reply) => {
  reply
    .code(200)
    .header("Content-Type", "text/html; charset=utf-8")
    .send("<h1>Hello from Lab 4!</h1>");
});

// Route for /name
fastify.get("/name", (request, reply) => {
  // (A) Getting information from the requester
  const {first, last} = request.query;
  console.log(first, last);

  //const name  // if first and last are defined, then name = "Brianna Wei" else "Guest"
  //<var> = <conditional statement> ? value if cs is true : alt value if cs is false

  // (B) Transforming the request into useful information
  const name = first && last ? `${first} ${last}` : `Guest`;

  // (C) Transforming the request into useful information
  reply
    .code(200)
    .header("Content-Type", "text/html; charset=utf-8")
    .send(`<h1>Hello, ${name}</h1>`);
});

// Start server and listen to requests using Fastify
const listenIP = "localhost";
const listenPort = 8080;
fastify.listen(listenPort, listenIP, (err, address) => {
  if (err) {
    console.log(err);
    process.exit(1);
  }
  console.log(`Server listening on ${address}`);
});

```
