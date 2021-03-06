# zero
A Lightweight Socket Service with heartbeat, Can be easily used in TCP server development.

[![Build Status](https://api.travis-ci.org/9b9387/zero.svg?branch=master)](https://travis-ci.org/9b9387/zero)

Wiki Page [https://github.com/9b9387/zero/wiki](https://github.com/9b9387/zero/wiki)

## Requirements

Go version: 1.9.x or later

## Usage

```
go get -u github.com/9b9387/zero
```

```
import "github.com/9b9387/zero"

func main() {
 	host := "127.0.0.1:18787"

 	ss, err := zero.NewSocketService(host)
	if err != nil {
		return
	}

	// set Heartbeat
	ss.SetHeartBeat(5*time.Second, 30*time.Second)

	// net event
	ss.RegOnMessageHandler(HandleMessage)
	ss.RegOnConnectHandler(HandleConnect)
	ss.RegOnDisconnectHandler(HandleDisconnect)

	ss.Serv()
}


```
Exmaple Code: [https://github.com/9b9387/zero/blob/master/service_test.go](https://github.com/9b9387/zero/blob/master/service_test.go)
