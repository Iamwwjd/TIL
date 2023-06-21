URI은 ****Uniform Resource Identifier의 약자로 `통합 자원 식별자` 이다.**

****Uniform : 리소스를 식별하는 통합된 방식****

****Resource :**** URI로 식별이 가능한 모든 종류의 자원(웹 브라우저 및 그 이외의 리소스 등)

****Identifier :**** 다른 항목과 구분하기 위해 필요한 정보

URL은 Uniform Resource Locator의 약자로 **`네트워크상에서 통합 자원(리소스)의 위치를 나타내기 위한 규약` 이다.  ( === 자원 식별자와 위치를 동시에 보여줌 (`웹 사이트 주소 + 컴퓨터 네트워크 상의 자원`))**

특정 웹 사이트에 접속하기 위해서는 웹 사이트의 주소 뿐 아니라 프로토콜(http, https, smp 등)까지 같이 알아야 하는데, URL은 이를 모두 나타낸다.

---

### URI와 URL의 차이점

- URI는 식별자, URL은 식별자 + 위치이다.
    
    `URI : [www.naver.com](https://www.naver.com/)/`  (리소스의 이름만 나타내기 때문)
    
    `URL : https://www.naver.com/` (이름과 프로토콜을 함께 나타내기 때문이다.)
    
- URL은 일종의 URI이며, URI이 더 포괄적인 개념이다.
- URL은 프로토콜과 결합한 형태이다. (프로토콜 + 이름(번호))
- URI은 그 자체로도 이름이 될 수 있다. (이름의 형태, 프로토콜 + 이름의 형태 모두 해당.)
    
    [`www.naver.com](https://www.naver.com/)/` URI
    
    [`https://www.naver.com/`](https://www.naver.com/) URI, URL
    
    **WHY?** *이름 + 위치를 나타내는 URL은 URI의 일종이기 때문이다!*
    

[`https://mail.naver.com/v2/folders/0/all`](https://mail.naver.com/v2/folders/0/all)

Scheme ****`https` : 리소스에 접근하는 데 사용할 프로토콜.웹에서는 보통 http or https 사용

Host [`mail.naver.com/`](https://mail.naver.com/v2/folders/0/all) : 접근할 대상(서버)의 호스트 이름

Path [`v2/folders/0/all`](https://mail.naver.com/v2/folders/0/all) : 접근할 대상(서버)의 경로에 대한 상세 정보

*경로(Path)에 해당하는 부분은 URN이라고 한다.*