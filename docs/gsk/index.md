---
sidebar_position: 2
---

# GSK Server Package

The GSK server package is a lightweight and flexible HTTP server for Golang applications. It provides an interface for managing server lifecycle, adding middleware, routing HTTP methods, and handling static files. Moreover, the package includes features for automated testing of server responses.

- A web server framework with go's native http server wrapper and httprouter for routing
- Middleware support
- slog Logger
- DB Connection helper functions
- Utilities


## Basic Usage

Here's a basic "hello world" server example:

```go
package main

import (
	"net/http"

	"github.com/adharshmk96/stk/gsk"
)

func main() {
	// create a new server
	server := gsk.New()

	// add routes
	server.Get("/", func(gc *gsk.Context) {
		gc.Status(http.StatusOK).JSONResponse(gsk.Map{"message": "Hello World"})
	})

	// start the server
	server.Start()
}
```


