---
sidebar_position: 3
---

# Middlewares

Middleware executes code before the request is handled by the route handler. Middleware functions are defined separately and then added to the server using the `Use` function.

```go
// Define your middleware
var MyMiddleware gsk.Middleware = func(next gsk.HandlerFunc) gsk.HandlerFunc {
    return func(c *gsk.Context) {
        // Execute code Before handler 

        next(c)

		// Execute code after handler
    }
}

// Add middleware to the server
server.Use(MyMiddleware)
```

Note that middleware is applied when the route is registered. Therefore, make sure to register routes after adding the middleware.

### Middleware Ordering

Middlewares apply only to the routes registered after the middleware is added. You can add some routes which do not require a specific middleware.

```go
server.Use(MyMiddleware)
// applies my middleware to all routes registered after this
server.Get("/path", func(c *gsk.Context) {
    // handle the request
})

server.Use(AnotherMiddleware)
// applies another middleware to all routes registered after this
// but not to the route registered before this
// *my middleware will still be applied to this route*
server.Get("/path2", func(c *gsk.Context) {
    // handle the request
})
```

### With Route Groups

Group routes and apply middleware to the group:

```go
server.Use(MyMiddleware)
// applies MyMiddleware to all routes registered after this
authGroup := server.RouteGroup("/auth")
authGroup.Use(AuthMiddleware)

// applies auth middleware to all routes registered after this
authGroup.Get("/login", func(c *gsk.Context) {
	// handle the /auth/login request
})

publicGroup := server.RouteGroup("/public")
// applies only MyMiddleware to all routes registered after this
publicGroup.Get("/home", func(c *gsk.Context) {
	// handle the /public/home request
})
```