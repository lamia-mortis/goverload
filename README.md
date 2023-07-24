**QUICK START**

```go
    params  := map[string]string{"key": "val"}
	headers := map[string]string{"Content-Type": "application/json"}
	body    := `{ "key1": [ [ 0, 0, 0, 0, 0, 0, 0, 0, 0 ] ], "key2": 3 }`

	overloader      := goverload.NewOverloader[string]()
	request         := goverload.NewRequest[string](helpers.HTTP, "sudoku-solve")
	httpRequest, ok := request.(*requests.HttpRequest[string])

	if ok {
		httpRequest.
			SetMethod("POST").
			SetHost("host").
			SetPort("8888").
			SetPath("/api/some/path").
			SetParams(params).
			SetHeaders(headers).
			SetBody(body)

		overloader.
			AddRequest(httpRequest).
			SetConfig(10, 10)

		overloader.Run()
	}
```