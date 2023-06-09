*컨테이너화 된애플리케이션을 신속하게 구축, 테스트 및 배포할 수 있는 오픈소스 가상화 플랫폼*

GO 언어로 개발되고 있다.

Docker를 사용한 서버관리

OS 환경설정, 언어, 라이브러리, 시스템 도구 등이 설치된 환경을 그대로 **이미지**로 빌드할 수 있는데 이때 이미지는 Dockerfile을 이용하여 만든다. 개발 환경에서 만들어진 이미지를 프로덕션 서버에 전달하고 이미지를 기반으로 컨테이너를 생성, 실행하면 끝 !

위 컨테이너의 특징은 도커의 중요한 특징인 표준성와 상통하는데, 다양한 언어와 프레임워크를 사용한 서비스들은 각기 다른 배포 방법을 가지고 있는데 이를 도커를 통해 패키징하여 컨테이너를 만든다면 언어,프레임워크,런타임과 관계없이 모두 동일한 배포 프로세스를 갖게 된다.

이런 표준성 덕분에 도커는 높은 **확장성**과 **이식성**을 갖는다. 도커가 설치된 환경이라면 어디서든 컨테이너를 실행할 수 있으며, 이를 통해 프로덕션 서버는 물론, 개발 및 테스트 서버 구축과 운영도 아주 쉬워진다. 컨테이너를 환경에 따라 환경변수를 다르게 설정하여 관리할 수 있다.

왜 도커를 쓸까

- 산업 발전 → 서비스 인프라 구조도 상승
- 서버가 점점 많아질수록 인프라 관리가 힘듦 → 물리적 서버관리가 매우 힘듦(온습도 등등)
- 빠르게 대처가ㅏ 가능함.

MSA

→ 쪼개진 서비스만 관리하는 서버 (인력이 많이 필요)

→ 아직은 모놀리식 선호

친구랑 작업을 할 때 같은 설정이라도 미묘하게 다른 환경

- VM은 hostOS 위에 guestOS를 설치해 무겁고, 느리다.

docker

→ 사람들이 쓰기 쉽게 컨테이너를 만든것. but 최초는 아님

- 대기업들은 예전부터 썼지만, 사람들이 이용하기 쉽게 만든 것

컨테이너 기반 가상화 플랫폼

컨테이너 + 이미지

컨테이너는 cgroup과 namespace로 만들어져 있음

**컨테이너**

애플리케이션의 코드, 라이브러리 및 종속성을 포함하는 패키지

## 주의사항

1. Docker 컨테이너는 호스트 시스템과 분리되어 있지만, 보안이 약하다 
    
    → 이미지를 신뢰할 수 있는곳에서 받고, 가능한 적은 권한으로 실행해준다
    
2. Docker 컨테이너는 삭제와 동시에 모든 데이터가 초기화 된다.
    
    → 외부 저장장치에 링크, 별도의 클라우드 스토리지(S3) 사용
    

### 컨테이너와 가상머신(VM)의 차이점

시스템 구조적으로 컨테이너는 한 OS를 공유하는 구조이고 VM은 각각의 OS를 띄워야 하는 구조이기 때문에 컨테이너가 VM보다 더 빠르다. 하지만 컨테이너는 리눅스 OS에서 윈도우용 컨테이너를 사용할 수 없고, VM은 보안적으로 문제가 생겨도 VM이 각각 분리되어 있기에 서로 피해가 가지 않지만 컨테이너는 보안적으로 문제가 생길 수 있다. 

→ 이에 따라 컨테이너는 시스템을 모듈별로 쪼개서 개발을 했을 때 큰 효과를 낼 수 있다 !