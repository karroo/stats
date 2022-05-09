
# Overview


### 통계 시스템의 데이터 흐름도

![](<.gitbook/assets/PPTX File viewer | Microsoft Teams 2022-05-08 17-39-27.png>)

1. Connector
    * Datasource에서 데이터를 가져올때 사용하는 리소스타입별 Connection모듈
1. Datasource
    * Stat시스템을 사용하여 통계를 처리하려는 원본 데이터.
    * 원본 데이터는 그 자체로 통계에 이용하기 어려우므로, Dataset으로 가공되어야 함.
1. Dataset
    * 통계처리에 직접적으로 사용되는 가공 저장된 데이터 
    * Datasource 로부터 필요한 필드만을 추출/가공하여 저장한 2차 데이터이다.
1. JobServer
    * Datasource를 Dataset으로 가공처리하는 프로세스이다.
    * One-time 배치 또는 finite-loop 배치 처리를 실행한다.
1. Statics Engine
    * 저장된 Dataset으로 집계 query를 수행하여 통계데이터를 생성한다 
    * 실시간처리와 cached 집계 데이터를 위한 query를 처리한다.
1. UI
    * Datasource, Dataset, Panel, Dashboard를 관리한다
    * Job의 실행/중지를 관리한다.


### Datasource
가공처리하여 집계에 사용하게 될 원본 데이터.
데이터 소스는 다음 3가지의 유형으로 나눌 수 있다.

1. DMBS
    - RDMBS, NoSql 등의 DMBS 를 의미하며, Database의 종류에 따라 그에 대응하는 Datasource Connector 가 존재해야 한다.
    - 현재는 Mongo DB 만을 지원함.

3. File
    - CSV 파일 형식의 데에터를 업로드 함으로서 다량의 데이터를 적재 할 수 있다.
    - 현재 미지원

### Statistic Engine
집계처리를 담당하는 Stats 서버의 핵심부분

1. Repository
    - Dataset을 저장하는 저장소
    - Online 집계처리에 성능을 보장할 수 있도록 하는 column-based 저장소로 이루어져 있다.
2. Query Engine
    - Panel에서 요청한 query를 수행하는 엔진.
3. Cache
    - 성능을 보장하기 위한 cache처리된 집계 데이터
    - 현재 지원되지 않는다.

### UI
1. Dataset
    - Datasource로 부터 Dataset을 생성해내는데 필요한 스펙을 관리한다.
1. Panel
    - Dataset으로 부터 처리할 집계 query를 정의하며, 이를 Chart로 어떻게 보여줄지를 정의한다.
1. Dashboard
    - Panel을 여러개 모아서 한눈에 집계현황을 파악할 수 있는 Dashboard를 관리한다.

