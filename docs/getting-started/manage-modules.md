---
sidebar_position: 2
---

# Manage Modules

## Adding A Module

To add a module boilerplate to the project, you need to run the following command:

```bash
stk add -m
```

eg: `stk add -m admin`

This command will generate the required files for the module.

## Removing A Module

To remove a module boilerplate from the project, you need to run the following command:

```bash
stk rm -m
```

eg: `stk rm -m admin`

This command will remove the module related files from the project.

## File Structure

example of files related to module `admin`:

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

