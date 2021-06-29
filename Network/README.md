# Network
* [HTTP란 무엇입니까?](#http란-무엇입니까)
* [HTTP 요청 메시지란 무엇입니까?](#http-요청-메시지란-무엇입니까)
* [HTTP 요청 메서드란 무엇입니까?](#http-요청-메서드란-무엇입니까)
* [Status Code란 무엇입니까?](#status-code란-무엇입니까)
* [Persistent Connections란 무엇입니까?](#persistent-connections란-무엇입니까)
* [HTTP의 Session State란 무엇입니까?](#http의-session-state란-무엇입니까)
* [HTTP Message란 무엇입니까?](#http-message란-무엇입니까)
* [HTTP cURL이란 무엇입니까?](#http-curl이란-무엇입니까)
* [HTTP 응답이란 무엇입니까?](#http-응답이란-무엇입니까)
* [HTTP Security란 무엇입니까?](#http-security란-무엇입니까)
* [HTTP에서 200 OK 응답 코드는 무엇입니까?](#http에서-200-ok-응답-코드는-무엇입니까)
* [HTTP에서 201 Created 응답 코드는 무엇입니까?](#http에서-201-created-응답-코드는-무엇입니까)
* [HTTP에서 300 Multiple Choices 응답 코드는 무엇입니까?](#http에서-300-multiple-choices-응답-코드는-무엇입니까)
* [HTTP에서 400 Bad Request 응답 코드는 무엇입니까?](#http에서-400-bad-request-응답-코드는-무엇입니까)
* [HTTP에서 401 Unauthorized 응답 코드는 무엇입니까?](#http에서-401-unauthorized-응답-코드는-무엇입니까)
* [HTTP에서 405 Method Not Allowed 응답 코드는 무엇입니까?](#http에서-405-method-not-allowed-응답-코드는-무엇입니까)
* [HTTP에서 408 Request Timeout 응답 코드는 무엇입니까?](#http에서-408-request-timeout-응답-코드는-무엇입니까)
* [HTTP에서 500 Internal Server Error 응답 코드는 무엇입니까?](#-http에서-500-internal-server-error-응답-코드는-무엇입니까)
* [IP는 어떤 OSI 계층에 속합니까?](#ip는-어떤-osi-계층에-속합니까)
* [HTTP의 다른 역할은 무엇입니까?](#http의-다른-역할은-무엇입니까)
* [HTTPS란 무엇입니까?](#https란-무엇입니까)
* [HTTP의 컨텐츠 협상(Content Negotiation)이란 무엇입니까?](#http의-컨텐츠-협상content-negotiation이란-무엇입니까)
* [HTTP 컨텐츠 협상(Content Negotiation)의 다른 유형은 무엇이 있습니까?](#http-컨텐츠-협상content-negotiation의-다른-유형은-무엇이-있습니까)
* [HTTP에서 100 Continue 응답 코드는 무엇입니까?](#http에서-100-continue-응답-코드는-무엇입니까)
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

## HTTP에서 201 Created 응답 코드는 무엇입니까?
요청이 수행되어 새 리소스가 생성되었음을 나타냅니다.  

[맨위로](#network)

## HTTP에서 300 Multiple Choices 응답 코드는 무엇입니까?
클라이언트가 선택할 수 있는 리소스에 대한 여러가지 옵션을 나타내는 데 사용됩니다.

[맨위로](#network)

## HTTP에서 400 Bad Request 응답 코드는 무엇입니까?
요청이 잘못되어 서버가 요청을 이해하지 못했음을 나타내는 데 사용됩니다.

[맨위로](#network)

## HTTP에서 401 Unauthorized 응답 코드는 무엇입니까?
리소스에 접근하기 전에 인증을 수행해야 함을 표시하는 데 사용됩니다.

[맨위로](#network)

## HTTP에서 405 Method Not Allowed 응답 코드는 무엇입니까?
요청 메서드가 요청된 리소스에서 지원되지 않음을 나타냅니다.

[맨위로](#network)

## HTTP에서 408 Request Timeout 응답 코드는 무엇입니까?
요청이 서버가 대기하도록 설정된 시간보다 오래 걸렸다는 것을 나타내는 데 사용됩니다.

[맨위로](#network)

## ## HTTP에서 500 Internal Server Error 응답 코드는 무엇입니까?
서버에 에러가 발생했고 서버에서 처리 방법을 알 수 없음을 나타내는 데 사용됩니다.

[맨위로](#network)

## IP는 어떤 OSI 계층에 속합니까?
OSI 계층의 세 번째 계층인 네트워크 계층에 속합니다.

[맨위로](#network)

## HTTP의 다른 역할은 무엇입니까?
HTTP는 주로 html 문서를 가져와서 클라이언트로 전송하도록 설계되었습니다.   
HTTP는 지속적으로 발전하고 기능이 추가되면서 웹에서 데이터를 빠르고 안정적으로 이동시킬 수 있는 가장 편리한 방법이 되었습니다.

[맨위로](#network)

## HTTPS란 무엇입니까?
Hypertext Transfer Protocol Secure를 나타냅니다.   
HTTPS에는 보안 전송 기능이 있습니다.   
HTTPS는 웹 서버에서 반환되는 사용자 HTTP 페이지 또는 HTTP 페이지 요청을 암호화/복호화 하는 데 사용됩니다.   

[맨위로](#network)

## HTTP의 컨텐츠 협상(Content Negotiation)이란 무엇입니까?
대부분의 HTTP 응답에는 사용자가 해석할 수 있는 정보가 포함된 엔티티가 포함됩니다.   
이것은 요청에 따른 최상의 사용 가능한 엔티티를 사용자에게 제공하기 위해 사용됩니다.   
그러나 캐시와 서버의 경우 모든 사용자가 최선에 대해 동일한 선호도를 가지는 것은 아닙니다.   
그렇기 때문에 HTTP에는 여러 가지 표현을 사용할 수 있을 때 주어진 응답에 가장 적합한 표현을 선택하는 프로세스인 컨텐츠 협상(Content Negotiation)을 위한 여러 메커니즘이 마련되어 있습니다.

[맨위로](#network)

## HTTP 컨텐츠 협상(Content Negotiation)의 다른 유형은 무엇이 있습니까?
* 서버 중심 협상(Server-driven Negotiation)
  * 서버에 있는 알고리즘을 통해 응답에 가장 적합한 표현을 선택합니다.
* 에이전트 중심 협상(Agent-driven Negotiation)
  * 사용자 에이전트는 원래 서버로부터 초기 응답을 받은 후 응답에 가장 적합한 표현을 선택합니다.
* 투명한 협상(Transparent Negotiation)
  * 서버 중심 협상과 에이전트 중심 협상의 조합입니다.

[맨위로](#network)

## HTTP에서 100 Continue 응답 코드는 무엇입니까?
클라이언트가 요청을 계속해야 함을 표시하는데 사용됩니다.    
중간 응답은 요청의 초기 부분이 수신되었음을 클라이언트에게 알립니다.   

[맨위로](#network)

## 참고
* [Top 20+ HTTP Interview Questions (2021) - javatpoint](https://www.javatpoint.com/http-interview-questions)

[맨위로](#network)
