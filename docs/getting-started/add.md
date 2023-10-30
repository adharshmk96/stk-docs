---
id: add-modules
sidebar_position: 2
title: Adding modules
sidebar_label: Adding modules
---

To add a module boilerplate to the project, you need to run the following command:

```bash
stk add -m
```

eg: `stk add -m admin`

This command will generate the boilerplate for the module and add the required files. The project structure will look like this:

example of generated module `admin`:

```
internals
├── core
│   ├── entity
│   │   └── admin.go
│   └── serr
│       └── admin.go
├── http
│   ├── handler
│   │   └── admin.go
│   ├── handler_test
│   │   └── admin_test.go
│   ├── helpers
│   │   └── admin.go
│   └── transport
│       └── admin.go
├── service
│   └── admin.go
├── service_test
│   └── admin_test.go
├── storage
│   └── adminStorage
│       ├── admin.go
│       └── adminQueries.go
server
└── routing
    └── admin.go        
```

You can start using the module by exposing the routes in `server/routing/initRoutes.go` file.

example:

```go
package routing

import (
	"github.com/adharshmk96/stk/gsk"
)

func SetupApiRoutes(server *gsk.Server) {
	apiRoutes := server.RouteGroup("/api")

	setupPingRoutes(apiRoutes)
	setupAdminRoutes(apiRoutes) // Admin 
}
```

