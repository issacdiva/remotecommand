# remotecommand
enable client-go remotecommand stream to close

修改了client-go tools remotecommand 增加了主动关闭stream的功能

通过closeChan chan bool，实现关闭stream

```go
remotecommand.StreamOptions{
		Stdin:             stdin,
		Stdout:            stdout,
		Stderr:            stderr,
		Tty:               true,
		CloseChan:         closeChan,
		TerminalSizeQueue: terminalSizeQueue,
	}
```

如果需要强制关闭只需要关闭channel：close(closeChan)即可
