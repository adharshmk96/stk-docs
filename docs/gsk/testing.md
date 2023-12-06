---
sidebar_position: 5
---

# Testing 

The server package provides a `Test` function to simulate HTTP requests and test server responses. This function takes the HTTP method, path, body, and optional parameters (cookies and headers), and returns a `httptest.ResponseRecorder` and an error.

```go
w, err := server.Test("GET", "/path", nil)

// w is a *httptest.ResponseRecorder, and can be used to check the response
// err should be checked to ensure the request was processed successfully
```

If you need to send headers or cookies with your test request, use the `TestParams` struct.

```go
params := gsk.TestParams{
	Cookies: []*http.Cookie{{Name: "name", Value: "value"}},
	Headers: map[string]string{"Content-Type": "application/json"},
}

w, err := server.Test("GET", "/path", nil, params)
```

Please note that this documentation is a simplified guide to using the GSK package. To use it fully, ensure to handle error cases properly and use the `Context` object correctly in your route handlers and middleware.
