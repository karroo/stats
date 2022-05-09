# Overview

### Stats 데이터 흐름도

![](<.gitbook/assets/STATS - Google Slides 2022-01-18 18-03-27.png>)

1. Datasource
   * 원본 데이티를 지칭한다.
   * 원본 데이터는 그 자체로 통계에 이용하기 어려우므로, Dataset으로 가공되어야 한다.
2. Dataset
   * 집계처리에 실제로 사용되는 데이터
   * Datasource 로부터 필요한 필드 만을 추출하여 모아둔 2차 데이터이다.
   * 원본 필드 자체로 통계에 사용하기 어려운 경우, 2차 가공을 한 후에 추가 필드로 지정하여 사용할 수도 있다.
3. JobServer
   * Datasource를 Dataset으로 가공처리하는 프로세스이다.
   * 배치처리 또는 건별 실시간 처리를 지원한다.
4. Statics Engine
   * Dataset을 저장/관리하며 이로부터 query를 수행하여 통계데이터를 생성한다.&#x20;
   * 실시간 통계 처리와 cached 통계 데이터를 지원한다.&#x20;
5. UI
   * Dataset, Panel, Dashboard를 관리한다.&#x20;
   * Job의 실행/중지를 관리한다.

### Data Source

데이터 소스는 데이터의 원본을 의미한다. 데이터 소스는 다음 3가지의 유형으로 나눌 수 있다.

1. Database & Link
   * RDB, NoSql 등의 DMBS 를 의미하며, Database의 종류에 따라 그에 대응하는 Datasource Connector 가 존재해야 한다.
   * 가장 기본이 되는 Datasource이며, 이미 쌓여 있는 데이터를 다량으로 적재할 때 사용된다.
   * 현재는 CogInsight 내장 저장소 만을 지원한다.
2. Application & Message Que
   * Application은 실시간으로 Message Que 를 통해서 데이터를 적재 할수 있다.
   * 현재는 CogInsight의 내부 솔루션 이외의 외부 Application의 연결은 지원하지 않는다.
3. File & Uploader (예정)&#x20;
   * CSV 파일 형식의 데에터를 업로드 함으로서 다량의 데이터를 적재 할 수 있다.
   * 현재 지원하지 않는다.

### Statistic Engine

데이터 집계 처리를 담당하는 Stats 서버 엔진&#x20;

1. Repository
   * Dataset을 저장하는 저장소
   * Online 통계처리에 성능을 보장할 수 있도록 하는 column-based 저장소로 이루어져 있다.
2. Query Engine
   * Panel로 부터 요청된 query를 수행하는 엔진.
3. Cache
   * 성능을 보장하기 위한 cache처리된 통계 데이터

### Stats UI

1. Dataset
   * Datasource로 부터 Dataset을 생성해내는데 필요한 지시내용을 관리한다.
2. Panel
   * Dataset으로 부터 처리할 통계 query를 정의하며, 통계처리 결과 데이터를 Chart로 어떻게 보여줄지를 정의한다.
3. Dashboard
   * Panel을 여러개 모아서 한눈에 통계현황을 파악할 수 있는 Dashboard를 관리한다.
