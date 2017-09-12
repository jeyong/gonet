# HTTP(Hypertext Transfer Protocol)
다른 porotocol이 이진수 형태의 데이터라면 http는 사람이 읽기 쉬운 형태인 text 기반.
RFC : HTTP protocol 정의

## URL (Uniform Resource Locator)
 * URI(Uniform Resource Identifier)의 한 형태
 * http://google.com
   * IP 주소로 resolve
   * 이 IP 주소로 TCP 연결하며 HTTT 포트는 80
   * 해당 사이트의 root document를 요청
 * url 처리 관련 library 
```go
import "net/url"

```