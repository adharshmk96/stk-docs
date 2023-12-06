---
sidebar_position: 2
---

### Routing HTTP methods: 
Define routes for each HTTP method (Get, Post, Put, Delete, Patch) by calling the appropriate function.

```go
server.Get("/path", func(c *gsk.Context) {
    // handle the request
})
```

#### Route Parameters:

Use the `Param` function to get the value of a route parameter.

```go
server.Get("/path/:id", func(c *gsk.Context) {
	id := c.Param("id")
	// handle the request
})
```

#### Query Parameters:

Use the `Query` function to get the value of a query parameter.

```go
server.Get("/path", func(c *gsk.Context) {
	// example: /path?id=123, id = 123
	id := c.Query("id")
	// handle the request
})
```

#### Request Body:

Use the `Body` function to get the request body as a string.

```go
server.Post("/path", func(c *gsk.Context) {
	body := c.Body()
	// handle the request
})
```

### Route Groups:

Use the `RouteGroup` function to group routes under a common prefix.


```go
server := gsk.New()

apiRoutes := server.RouteGroup("/api")

// all routes registered under /api will be prefixed with /api
apiRoutes.Get("/path", func(c *gsk.Context) {
	// handle the request for /api/path
})

otherRoutes := server.RouteGroup("/other")

// all routes registered under /other will be prefixed with /other
otherRoutes.Get("/path", func(c *gsk.Context) {
	// handle the request for /other/path
})

```