## Intro

Iron Leap middleware for Go works with applications based on `net/http`.

## Installation

```shell
go get github.com/IronLeap/iron-leap-go
```

Iron Leap uses [Go Modules](https://github.com/golang/go/wiki/Modules) to manage dependencies.


## Basic configuration

Configure Iron Leap at the start of your `main()` function:

```go
import "github.com/IronLeap/iron-leap-go"

func main() {
	iron_leap.Configure(iron_leap.Configuration{
		APIKey:     "YOUR API KEY HERE",
		ProjectID:  "YOUR PROJECT ID HERE",
		KeysToMask: []string{"password", "card_number"}, // optional, mask fields you don't want sent to Iron Leap
		ServerURL:  "https://rocknrolla.ironleap.com",    // optional, don't use default server URL
	}

    // rest of your program.
}

```


After that, just use the middleware with any of your handlers:
 ```go
mux := http.NewServeMux()
mux.Handle("/", iron_leap.Middleware(yourHandler))
```