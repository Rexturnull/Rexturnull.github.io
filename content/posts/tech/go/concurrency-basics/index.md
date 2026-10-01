+++
title = "Go Concurrency 基礎"
date = 2026-09-20T09:00:00+08:00
tags = ["go", "concurrency"]
cover = "cover.svg"
summary = "從 goroutine 與 channel 開始，建立對 Go 併發模型的基本直覺。"
+++

Go 的併發模型建立在 goroutine 與 channel 之上。goroutine 是由 runtime 排程的輕量執行緒，
channel 則是 goroutine 之間安全傳遞資料的管道。

## Goroutine

使用 `go` 關鍵字即可啟動一個新的 goroutine：

```go
go doSomething()
```

## Channel

Channel 用來在 goroutine 之間同步與傳遞資料：

```go
ch := make(chan int)
go func() { ch <- 42 }()
fmt.Println(<-ch)
```
