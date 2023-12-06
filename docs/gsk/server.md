---
sidebar_position: 1
---

# Server

### Initialization:

Initialize a new server instance by invoking the `New` function.

```go
server := gsk.New()
```

Optionally, you can pass a `ServerConfig` object to `New` to set the server's configurations, such as the port, logger, and body size limit.

```go
config := &gsk.ServerConfig{
	Port:          ":8081",
	Logger:        slog.New(),
	BodySizeLimit: 1<<20, // 1 MB
}
server := gsk.New(config)
```

### Starting and Stopping:
 
Use `Start` to start the server and `Shutdown` to stop it.

```go
server.Start()

// and later...
err := server.Shutdown()
if err != nil {
    // handle error
}
```

Here is an example function to start and gracefully shutdown the server:

```go
package main

import (
	"log/slog"
	"net/http"
	"os"
	"os/signal"
	"syscall"

	"github.com/adharshmk96/stk/gsk"
	"github.com/adharshmk96/stk/pkg/middleware"
)

var logger = slog.New(slog.NewJSONHandler(os.Stdout, nil))

func setupRoutes(server *gsk.Server) {
	server.Get("/", func(c *gsk.Context) {
		c.Status(http.StatusOK).JSONResponse(gsk.Map{"message": "Hello World"})
	})
}

func StartHttpServer(port string) (*gsk.Server, chan bool) {

	serverConfig := &gsk.ServerConfig{
		Port:   port,
		Logger: logger,
	}

	server := gsk.New(serverConfig)

	rateLimiter := middleware.NewRateLimiter()
	server.Use(rateLimiter.Middleware)

	server.Use(middleware.RequestLogger)
	server.Use(middleware.CORS(middleware.CORSConfig{
		AllowAll: true,
	}))

	setupRoutes(server)

	server.Start()

	// graceful shutdown
	done := make(chan bool)

	// A go routine that listens for os signals
	// it will block until it receives a signal
	// once it receives a signal, it will shutdown close the done channel
	go func() {
		sigint := make(chan os.Signal, 1)
		signal.Notify(sigint, os.Interrupt, syscall.SIGTERM)
		<-sigint

		if err := server.Shutdown(); err != nil {
			logger.Error("Server Shutdown Failed", err)
		}

		close(done)
	}()

	return server, done
}

func main() {

	startAddr := "0.0.0.0:"
	startingPort := "8080"

	_, done := StartHttpServer(startAddr + startingPort)
	// blocks the routine until done is closed
	<-done

}
```