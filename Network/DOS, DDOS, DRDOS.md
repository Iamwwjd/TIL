## DOS,DDOS,DRDOS

### DOS(Denial of Service)공격

**타겟 시스템의 자원을 고갈 시키거나 네트워크 대역폭을 초과시켜 원래 의도된 용도로 사용하지 못하게 하는 공격이다.(가용성 침해)**

**DDOS와의 차이점은 Attacker가 직접 공격을 수행한다는 점이다.**

---

**DOS공격 유형**

- Ping of Death
    
    개념
    
    - ICMP Echo Request 패킷의 크기를 정상 크기보다 아주 크게 만들어 공격 네트워크에 도달하는 동안 아주 작은 조각으로 쪼개져 Victim이 쪼개진 조각을 모두 처리하게 하여 부하가 걸리도록 하는 공격이다
    
    대응법
    
    - 반복적으로 들어오는 일정한 수 이상의 ICMP 패킷을 무시하도록 설정한다.(대부분의 시스템에서 이미 설정이 되어있다.)
    - System 보안 패치를 한다.
- Smurf Attack
    
    개념
    
    - Attacker가 출발지 IP를 Victim의 IP로 Spoofing하여 ICMP Request패킷을 시스템이 아주 많은 네트워크를 Broadcast하면 해당 패킷을 받은 네트워크가 Victim에게 ICMP Reply패킷을 대량으로 보내는 공격이다
    
    대응법
    
    - 라우터에서 Direct Broadcast를 차단한다(대부분의 라우터에서 이미 Default로 차단되어 있다.)
- SYN Flooding
    
    개념
    
    - 3way handshake 취약점을 이용하여 Backlog Queue가 초과하도록 만드는 공격이다
    1. Attacker가 SYN 패킷을 보낸 후 SYN+ACK 패킷이 돌아와도 ACK 패킷을 보내지 않아 Victm이 SYN Received 상태로 ACK 패킷을 계속 기다리는 상태로 만든다. (Backlog에 빠지도록 만든다)
    2. 이런식으로 계속 SYN 패킷ㅇㄹ 보내어 Victim의 Backlog Queue를 초과하도록 만든다
    
    대응법
    
    - Backlog Queue크기를 늘려준다
    - System 보안 패치를 한다.
    - SYN Cookie를 이용한다.
    - IDS,IPS에서 정형화된 SYN Flooding 패킷을 탐지한다
- Land Attack
    
    개념
    
    - 대량의 패킷이 출발지 IP주소와 목적지IP소를 같게 만들어서 Victim에 보내는 공격이다
    
    대응법
    
    - 출발지 IP주소와 목적지 IP주소를 확인하여 동일한 패킷은 버린다.(현재 대부분의 시스템은 이미 적용하고 있다.)
    - 라우터나 방화벽에서 출발지 IP주소와 내부 IP주소가 동일한 패킷은 차단한다.
- DHCP Starvation
    
    개념
    
    - 공격자가 MAC Address를 계속 변경하여 DHCP Server로부터 IP를 할당받아서 DHCP Server가 보유하고있는 모든 IP주소를 할당받아 정작 정상적인 호스트가 IP를 할당받지 못하게 하는 방식이다.
    
    대응법
    
    port security기능을 사용한다. port security 기능을 사용하면 해당 MAC Address에게만 IP를 할당하거나 해당Port에 최대로 줄 수 있는 IP개수를 제한할 수 있다.
    

---

### DDOS(Distributed DoS)

- Attacker가 여러 대의 컴퓨터를 감염시켜 동시에 한 타겟 시스템을 집중적으로 공격하는 방법이다.
- 짧은 시간 안에 서버를 마비시킬 수 있으며 DoS보다 치명적이다.
- DOS와의 차이점은 실질적인 Attacker가 아닌 Attacker가 감염시킨 좀비 PC가 공격을 수행한다는 점이다.

**구성요소**

| Attacker | 공격자 |
| --- | --- |
| Master(C&C) | Attacker에게 명령을 받는 시스템 |
| Agent | Master의 명령을 받아 직접 공격하는 시스템 |
| Victim | 희생자 |

---

### DRDOS(Distributed Reflection DoS)

- DDOS보다 발전된 공격이다.
- Attacker는 출발지 IP를 Victim의 IP로 Spoofing한 SYN 패킷을 반사 서버로 대량으로 전송하여 이를 받은 반사서버가 Victim에 SYN/ACK을 보내 홍수를 일으켜 Victim을 다운시킨다.(ICMP 프로토콜의 Request/Reply를 이용하기도 한다.