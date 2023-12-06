---
sidebar_position: 4
---

# Serving Static Files: 

Static files are served from the `public/assets` directory under `/static` route. ( default )

This can be configured in server configs

```go
serverConfig := &gsk.ServerConfig{
	StaticPath: "/static",
	StaticDir: "public/assets",
}
```

### Serving Templates (text/html)

Template responses can be served using the `TemplateResponse` function.

```go
server.Get("/", func(gc *gsk.Context) {
	gc.TemplateResponse(&gsk.Tpl{
		TemplatePath: "public/templates/index.html",
		Variables: gsk.Map{
			"Title":   "STK",
			"Content": "Hello, World!",
		},
	})
})
```

Variables can be accessed in template via `{{ .Var.Name }}`

Constants can be accessed in template via `{{ .Const.Name }}`

Available constants:
- `{{ .Const.Static }}` : static path

