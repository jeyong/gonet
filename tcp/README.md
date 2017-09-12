# TCP
데이터를 스트림으로 전송.
연결 기반으로 스트림은 순서대로 중복되지 않게 전송되는 특징.
파일이나 문서를 전송할 때 TCP 사용.
채팅, SSH.

 * stateful stream protocol
   * OS의 네트워크 스택에서 이 protocol을 시작 준비가 완료되어야 가능
   * 통신하는 두쪽 모두 TCP stream 준비가 되어야 함.

 * server
   * passive socket
     * address와 port
     * server가 연결을 받을 준비가 되었다는 것
     * 이 port로 실제 data 주고 받기가 일어나지는 않는다.
     * OS에게 incoming connection 받을 준비가 되었다는 것을 알림
     * 접속 interface용 address와 port 번호를 사용하여 listening
     * HTTP 연결에서 동일한 interface로 접속 가능
   * active socket
     * 연결되는 쪽과 메시지를 주고 받는 용도
     * 읽기/쓰기 데이터가 어떻게 나눠져서 보내지고 받는지 신경쓰지 않아도 된다.
     * 이 socket은 다른 POSIX 프로그램에 전달이 가능하며 파일처럼 읽기/쓰기가 가능하다.
     * local ip/port, remote ip/port를 관리

## Server/Client
```go
package main 

import (
    "fmt"
    "net"
    "bufio"
)

func main() {
    ln, err := net.Listen("tcp", ":8080")
    if err != nil {

    }
    for {
        conn, err := ln.Accept()
        if err != nil {

        }
        go handleConnection(conn)
    }
}
```


```go
package main 

import (
    "fmt"
    "net"
    "bufio"
)

func main() {
    conn, err := net.Dial("tcp", "127.0.0.1:8080")
    if err != nil {

    }
    fmt.Fprintf(conn, "GET / HTTP/1.0\r\n\r\n")
    status, err := bufio.NewReader(conn).ReadString('\n')
}
```
