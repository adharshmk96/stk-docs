---
id: project-initial
sidebar_position: 1
title: Creating a project
sidebar_label: Creating a project
---

To start a project, you need to run the following command:

```bash
stk init 
```

> Hint: You can pass the package name in an empty directory eg: `stk init github.com/adharshmk96/stk`

You can run this command in 
- Empty directory : Given argument will be used as  package name ( or it generates random name ).
- Go module directory : The go module name will be used as the package name.
- Git repository : The repo name will be used as the package name.


This will create the project structure and add the required files. The project structure will look like this:

```
.
├── cmd
│   ├── root.go
│   └── serve.go
├── go.mod
├── go.sum
├── internals
│   ├── core
│   │   ├── entity
│   │   │   └── ping.go
│   │   └── serr
│   │       └── ping.go
│   ├── http
│   │   ├── handler
│   │   │   └── ping.go
│   │   ├── handler_test
│   │   │   └── ping_test.go
│   │   ├── helpers
│   │   │   └── ping.go
│   │   └── transport
│   │       └── ping.go
│   ├── service
│   │   └── ping.go
│   ├── service_test
│   │   └── ping_test.go
│   └── storage
│       └── pingStorage
│           ├── ping.go
│           └── pingQueries.go
├── main.go
├── makefile
├── public
│   ├── assets
│   │   ├── script.js
│   │   └── styles.css
│   └── templates
│       └── index.html
├── README.md
└── server
    ├── infra
    │   ├── config.go
    │   ├── constants.go
    │   ├── db
    │   │   └── sqlite.go
    │   └── logger.go
    ├── middleware
    │   └── middleware.go
    ├── routing
    │   ├── ping.go
    │   └── initRoutes.go
    └── setup.go
```