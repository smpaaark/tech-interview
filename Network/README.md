# Network
* [HTTP란 무엇입니까?](#http란-무엇입니까)
* [HTTP 요청 메시지란 무엇입니까?]()
* [HTTP 요청 메서드란 무엇입니까?]()
* [Status Code란 무엇입니까?]()
* [Persistent Connections란 무엇입니까?]()
* [HTTP의 Session State란 무엇입니까?]()
* [HTTP Message란 무엇입니까?]()
* [HTTP cURL이란 무엇입니까?]()
* [HTTP 응답이란 무엇입니까?]()
* [HTTP Security란 무엇입니까?]()
* [HTTP에서 200 OK 응답 코드는 무엇입니까?]()
* [참고](#참고)

[목차로](https://github.com/smpark1020/tech-interview#%EB%AA%A9%EC%B0%A8)

## HTTP란 무엇입니까?
HTTP는 Hypertext Transfer Protocol을 의미합니다.   
WWW(World Wide Web)에서 오디오, 비디오, 그래픽 이미지, 텍스트, 기타 멀티미디어 파일 등을 전송하는데 사용되는 규칙 집합입니다.   
HTTP는 하이퍼텍스트를 클라이언트에서 서버로 전송하는 데 사용되는 프로토콜이지만 HTTP에는 보안이 없습니다.   
사용자가 웹 브라우저를 열 때마다 사용자가 HTTP를 간적접으로 사용한다는 것을 의미합니다.   

[맨위로](#network)

## HTTP 요청 메시지란 무엇입니까?
HTTP 요청은 클라이언트 또는 사용자가 서버에서 작업을 시작하기 위해 보내는 메시지입니다.   
다음과 같은 다양한 요소들로 구성됩니다.
* Request Line
  * 메서드 토큰으로 시작하고 그 뒤에 프로토콜 버전인 Request-URI가 이어지며 CRLF로 끝납니다.
    * CRLF: 줄마꿈을 입력하는 문자를 칭하는 표현입니다.
  * SP 문자를 사용하면 요소가 구분됩니다.
    * SP: 공백 문자
  * Syntax
    ```
    Request-Line = Method SP Request-URI SP HTTP-Version CRLF  
    ```

* 요청에 의해 식별된 리소스
* 요청 헤더 필드
  * 클라이언트가 추가적인 요청 정보를 서버에 전달할 수 있도록 하는데 사용됩니다.   
  * 프로그래밍 언어 메서드 호출의 매개변수와 동등한 의미와 함께 요청 제어자 역할을 합니다.

[맨위로](#network)

## HTTP 요청 메서드란 무엇입니까?
GET
* 지정된 URI를 사용하여 지정된 서버에서 정보를 검색합니다.   
* 데이터를 검색할 수 있습니다.
* 데이터에 다른 효과를 적용시킬 수는 없습니다.

HEAD
* GET 메서드와 동일합니다.
* status line과 헤더 부분만 전송하는데 사용됩니다.

POST
* 데이터를 서버로 전송합니다.
* 예를 들어 HTML을 사용한 파일 업로드, 고객 정보 등록 등이 있습니다.

PUT
* 현재 대상 리소스를 업로드된 내용으로 변경하는데 사용됩니다.

DELETE
* URI에서 제공하는 대상 리소스를 모두 제거하는 데 사용됩니다.

CONNECT
* 지정된 URI로 식별되는 서버에 대한 터널을 설정하는데 사용됩니다.

[맨위로](#network)

## Status Code란 무엇입니까?
서버는 서버에 대한 클라이언트의 요청에 따라 HTTP Status Code를 발급합니다.   
Status Code는 3자리 정수입니다.   
Status Code의 첫 번째 자리수는 5개의 표준 응답 클래스 중 하나를 지정하는 데 사용됩니다.   
마지막 두 자리로 응답의 상세한 의미를 표현합니다.    

[맨위로](#network)

## Persistent Connections란 무엇입니까?
HTTP/1.0에서는 단일 요청 또는 응답 쌍이 지나면 연결이 닫힙니다.   
HTTP/1.1에서 keep-alive-mechanism이라고 알려진 메커니즘이 도입되었습니다.   
* 이 메커니즘에서는 둘 이상의 요청에 대해 연결을 재사용할 수 있습니다.

[맨위로](#network)

## HTTP의 Session State란 무엇입니까?
Session State는 Stateless state라고도 합니다.   
HTTP는 stateless 프로토콜입니다.   
session state에서는 클라이언트와 서버가 현재 요청 중에만 서로에 대해 알게 됩니다.   
연결이 닫혔는데 시스템 두 대가 다시 연결하려면 새 connection으로 서로 정보를 제공해야 하며 첫번째로 처리됩니다.   

[맨위로](#network)

## HTTP Message란 무엇입니까?
클라이언트와 서버 간에 데이터가 교환되는 방식을 보여주는 데 사용됩니다.   
이것은 클라이언트-서버 아키텍처를 기반으로 합니다.   
HTTP 클라이언트는 하나 이상의 HTTP 요청 메시지를 보내기 위해 서버에 대한 연결을 설정하는 프로그램입니다.    
HTTP 서버는 HTTP 응답 메시지를 전송하여 HTTP 요청을 처리하기 위한 연결을 허용하는 프로그램입니다.   

[맨위로](#network)

## HTTP cURL이란 무엇입니까?
command-line Toll 입니다.   
이것은 모든 주요 운영 체제에서 사용할 수 있습니다.   

[맨위로](#network)

## HTTP 응답이란 무엇입니까?
서버가 클라이언트로 보내는 것입니다.   
응답은 요청 받은 리소스를 클라이언트에게 제공하는 데 사용됩니다.   
또한 요청된 작업이 수행되었음을 고객에게 알리는 데도 사용됩니다.   
또한 요청을 처리하는 동안 오류가 발생했음을 클라이언트에 알릴 수도 있습니다.   
HTTP 응답에는 다음 사항이 포함됩니다.
* Status Line
* 응답 헤더 필드
* 메시지 본문

[맨위로](#network)

## HTTP Security란 무엇입니까?
HTTP는 인터넷을 통해 통신하는데 사용되므로 사용자, 정보 제공자, 애플리케이션 개발자는 HTTP/1.1의 보안 제한 사항을 알고 있어야 합니다.   
보안된 HTTP Connection을 설정하는 방법에는 두 가지가 있습니다.
* HTTPS URI
* HTTP/1.1 Upgrade Header

[맨위로](#network)

## HTTP에서 200 OK 응답 코드는 무엇입니까?
요청이 성공했음을 표시하는 데 사용됩니다.

[맨위로](#network)

## 참고
* [Top 20+ HTTP Interview Questions (2021) - javatpoint](https://www.javatpoint.com/http-interview-questions)

[맨위로](#network)
