## DNS Service

DNS(도메인 네임 시스템)는 사람이 읽을 수 있는 도메인 이름(ex www.amazon.com)을 머신이 읽을 수 있는 IP주소(ex 192.0.2.44)로 변환

---

**DNS 서비스 유형**

- 신뢰할 수 있는 DNS
    - 개발자가 퍼블릭 DNS 이름을 관리하는데 사용하는 업데이트 메커니즘을 제공
    - 메커니즘을 통해 DNS 시스템은 DNS 쿼리에 응답하고 도메인 이름을 IP 주소로 변환 → 컴퓨터가 서로 통신 가능
    - 도메인에게 최종 권한이 있으며 재귀적 DNS 서버에 IP 주소 정보가 담긴 답을 제공해야 함
- 재귀적 DNS
    
    대부분의 클라이언트는 신뢰할 수 있는 DNS 에 직접 쿼리를 수행하지 않음
    
    - 호텔 컨시어지와 같은 역할을 함
    - DNS 레코드를 소유하고 있지 않지만 사용자를 대신해서 DNS 정보를 가져올 수 있는 중간자의 역할
    - 재귀적 DNS가 일정 기간 캐시된 또는 저장된 DNS 참조를 가지고 있는 경우, 소스 또는 IP 정보를 제공하여 DNS 쿼리에 응답 하거나 해당 정보를 찾기위해 쿼리를 신뢰할 수 있는 DNS서버에 전달 함

## DHCP Service

**DHCP : 호스트의 IP주소와 각종 TCP/IP 프로토콜의 기본 설정을 클라이언트에게 자동적으로 제공해주는 프로토콜**

- DHCP지원 클라이언트는 네트워크 부팅과정에서 DHCP서버에 IP주소를 요청하고 이를 얻을 수 있다.
- 네트워크 안 컴퓨터에 자동으로 네임 서버 주소, IP주소, 게이트웨이 주소를 할당해주는것을 의미하고, 해당 클라이언트에게 일정기간 임대를 하는 동적 주소 할당 프로토콜

---

장점 : PC의 수가 많거나 PC 자체 변동사항이 많은 경우 IP설정이 자동으로 되기 때문에 효율적으로 사용 가능하고 IP를 자동으로 할당해주기 때문에 IP충돌을 막을 수 있다.

단점 : DHCP 서버에 의존되기 때문에 서버가 다운되면 IP할당이 제대로 이루어지지 않는다.

---

DHCP 구성

- DHCP 서버
    - DHCP서버는 네트워크 인터페이스를 위해서 IP주소를 가지고 있는 서버에서 실행되는 프로그램으로 일정한 범위의 IP주소를 다른 클라이언트에게 할당하여 자동으로 설정하게 해주는 역할을 한다다.
    - DHCP서버는 클라이언트에게 할당된 IP주소를 변경없이 유지해 줄 수 있다
    - 클라이언트에게 IP 할당 요청이 들어오면 IP를 부여해주고 할당 가능한 IP들을 관리해주게 된다.
- DHCP 클라이언트
    - 클라이언트들은 시스템이 시작하면 DHCP서버에 자신의 시스템을 위한 IP주소를 요청하고, DHCP 서버로부터 IP주소를 부여받으면 TCP/IP 설정은 초기화되고 다른 호스트와 TCP/IP를 사용해서 통신을 할 수 있게 된다.
    - 서버에게 IP를 할당받으면 TCP/IP 통신을 할 수 있다.

---

DHCP 프로토콜의 원리

DHCP를 통한 IP 주소 할당은 “임대”라는 개념을 가지고 있는데 이는 DHCP 서버가 IP 주소를 영구적으로 단말에 할당하는 것이 아니고 임대기간(IP Lease Time)을 명시하여 그 기간 동안만 단말이 IP 주소를 사용하도록 하는 것이다. 

단말은 임대기간 이후에도 계속 해당 IP 주소를 사용하고자 한다면 IP 주소 임대기간 연장(IP Address Renewal)을 DHCP 서버에 요청해야 하고 또한 단말은 임대 받 IP 주소가 더 이상 필요치 않게 되면 IP 주소 반납 절차(IP Address Release)를 수행하게 된다

---

**단말이 DHCP 서버로 부터 IP주소를 할당 받는 절차**

1. DHCP Discover

메시지 방향 : 단말 → DHCP 서버

 주요 피라미터

- Client MAC

1. DHCP Offer

메시지 방향 :  DHCP 서버 → 단말

주요피라미터

- Client MAC
- Your IP
- Subnet Mask
- Router
- DNS
- IP
- DHCP Server Identifier

1. DHCP Request

 단말 → DHCP 서버

주요 피라미터

- Client MAC
- Requested IP Address
- DHCP Server Identifier

1. DHCP Ack

DHCP 서버 → 단말

주요 피라미터

- Client MAC
- Your IP
- Subnet Mask
- Router
- DNS
- IP Lease Time
- DHCP Servr Identifier