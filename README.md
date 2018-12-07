# logf

[![GoDoc](https://godoc.org/github.com/acronis/logf?status.svg)](https://godoc.org/github.com/acronis/logf)
[![Build Status](https://travis-ci.org/acronis/logf.svg?branch=master)](https://travis-ci.org/acronis/logf)
[![Go Report Status](https://goreportcard.com/badge/github.com/acronis/logf)](https://goreportcard.com/report/github.com/acronis/logf)
[![GoCover](https://gocover.io/_badge/github.com/acronis/logf)](https://gocover.io/github.com/acronis/logf)

Faster-than-light, asynchronous, structured logger in Go with zero allocation count.

## Example

The following example creates the new `logf` logger and logs a message.

```go
package main

import (
    "runtime"

    "github.com/acronis/logf"
)

func main() {
    // The default channel writer writes to stdout using json encoder.
    writer, writerClose := logf.NewChannelWriter.Default()
    defer writerClose()

    logger := logf.NewLogger(logf.LevelInfo, writer)

    logger.Info("got cpu info", logf.Int("count", runtime.NumCPU()))
}
```

The output is the following:

```json
{"level":"info","ts":"2018-11-03T09:49:56+03:00","msg":"got cpu info","count":8}
```
