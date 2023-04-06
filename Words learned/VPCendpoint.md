### VPC endpoint
*AWS의 여러 서비스들과 VPC를 연결시켜주는 중간 매개체로서, AWS에서 트래픽이 VPC 밖으로 나가지 않고 AWS의 여러 서비스를 사용할 수 있게 만들어주는 서비스*

### 종류

*Access 방식으로 나뉜다!*

 **Interface Endpoint**

- ENI(Elastic Network Interface)를 이용하여, Private IP를 만들어 서비스를 연결한다.
- 할당된 IP로 Access 한다.
- Private IP 내부에 위치한다.
- SNS, Kinesis, Sagemaker 등 많은 서비스를 지원한다.

 **Gateway Endpoint**

- Route Table을 이용하여 Ecdpoint에 Access한다.
- 라우팅 테이블에서 경로의 대상으로 지정하여 사용한다.(S3, DynamoDB 일부만 지원)

### 통신과정

1. Private Subnet에 위치한 EC2에서 s3와 통신하기 위한 api를 부른다
2. 라우팅 테이블을 보고 라우터로 가서 Gateway 엔드포인트쪽으로 보낸다
3. Gateway 엔드포인트는 트래픽을 받고 s3로 보내준다.