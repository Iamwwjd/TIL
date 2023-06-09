### Kinesis

다양한 소스에서 *대량의 데이터를 수집하고, 처리 및 분석하여 이를 통해 데이터를 실시간으로 처리해 s3와 같은 스토리지에 저장한 후, 다양한 일괄 처리를 할 수 있다.*

한 샤드에 초당 1000개의 레코드 또는 1mb까지 수집할 수 있다.

### 스트리밍 데이터 처리 패턴

<aside>
💡 데이터 수집 → 데이터 분할 → 데이터 처리 → 결과 저장 순으로 데이터 처리가 이뤄진다.

</aside>

1. 데이터 수집
    - 데이터 생산자로부터 데이터를 수집한다.
    - 스트림에 데이터를 쓸 수 있다.
    - 스트림으로 데이터를 전송하여 실시간으로 대규모 데이터를 수집하고 처리할 수 있도록 도와준다.
2. 데이터 분할
    - kinesis 스트림은 데이터를 파티션 단위로 분할하여 처리할 수 있다.
    - 파티션을 통해 스트림의 모든 데이터를 정렬하고 순서대로 처리할 수 있다.
3. 데이터 처리
    - 스트림에서 파티션 단위로 분할된 데이터를 처리한다.
    - 데이터를 필터링, 변환, 집계, 분석하여 실시간으로 결과를 생성할 수 있다.
4. 결과 저장 
    - 처리된 데이터의 결과를 S3, Redstift, Elasticsearch Service 등의 서비스에 저장하거나  스트림으로 재전송하여 실시간으로 사용할 수 있는 정보를 제공함.

### 특징

*비디오와 데이터 스트림을 실시간으로 손 쉽게 수집 및 처리, 분석하는 서비스. 총 4가지로 나뉜다.*

1. Kinesis Data Steams : 데이터 스트림을 분석하는 사용자 정의 애플리케이션 개발에 사용된다
    - 데이터를 받으면 일정 기간 동안 내구성 있게 데이터를 저장하기 위한 서비스
2. Kinesis Data Firehose : 데이터 스트림을 AWS 데이터 저장소에 적재한다.
    - 데이터를 입력 받고 s3나 redshift, elasticsearch로 전송한다.
    - 뒷 단의 목적지로 데이터를 전송하기 위한 목적을 가진다.
3. Kinesis Data Analytics : SQL을 사용한 데이터 스트림 분석
    - Kinesis Data Stream 또는 Firehose에 쉽게 연결하고 Sql검색을 할 수 있다.
    - 수행 결과를 다시 데이터 시스템 또는 Fireshose로 보낸다.
    - 지속적으로 sql결과를 전달한다.
    - 데이터를 처리하기 위해 Stream(인- 메모리 테이블), 펌프(연속쿼리)의 컨셉을 사용하고 있다.
4. Kinesis Video Streams : 분석을 위한 비디오 스트림 캡쳐 및 정리, 저장

### 장점

1. 대규모 스트리밍 데이터를 처리하는데 최적화 되어있다
2. 응용 프로그램에서 사용할 수 있는 정보를 실시간으로 빠르게 제공할 수 있다
3. 수신한 데이터 양에 따라 자동으로 크기 조정이 가능하다 → 데이터 처리를 위한 하드웨어 비용을 최적화 할 수 있다.
4. 스트림 데이터의 내구성을 보장하여 단일 가용 영역의 장애가 발생해도 데이터가 안전하다.
5. 다양한 AWS 서비스와 통합이 가능하다.

### 단점

1. 데이터 처리량에 따라 비용이 많이 발생할 수 있다.
2. 초당 처리량과 대역폭에 대한 제한이 있다.
3. 분산된 데이터 처리를 위해 설계된 Kinesis는 일부 응용프로그램에서 데이터 처리 과정이 너무 복잡하거나 불안정 할 수 있다.