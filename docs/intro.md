---
id: home
title: STK Documentation
slug: /
sidebar_position: 1
sidebar_label: Introduction
---

# STK Introduction

Server toolkit - minimal and simple framework for developing server in golang. STK provides a suite of tools tailored for building and managing server applications.

## GSK package

Ideal for building server applications. GSK package provides a suite of tools tailored for building and managing server applications.

- Router using httprouter
- Middleware support
- Logger with slog
- Utilities

## STK CLI

CLI tool to create new project, generate code, and manage the project.

- Create new project boilerplate
- Generate new module boilerplate
- Migration tool for defining and managing database schema

 make sure go is installed 

Linux:

 ```shell
rm -rf /usr/local/go && curl -L https://go.dev/dl/go1.21.4.linux-amd64.tar.gz | tar -C /usr/local -xzf -
```

Mac:

```shell
rm -rf /usr/local/go && curl -L https://go.dev/dl/go1.21.4.darwin-arm64.pkg -o go1.21.4.darwin-arm64.pkg && sudo installer -pkg go1.21.4.darwin-arm64.pkg -target /
```

