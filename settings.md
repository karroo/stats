# Settings (시스템 사용자 메뉴)

데이터셋을 정의할 때 사용하는 원본데이터에 대한 정의를 하는 공간.
- Datasource: Dataset을 정의 할 때 사용하는 원본 저장소에 대하 정의. 원본저장소에 대한 연결정보, 대상리소스의 이름, Date 필드, Key 필드및 필터에 정보를 지정하여, 원본데이터를 가져올때 필요한 기본적인 정보를 지시한다.
- Connector: Datasource에 지정하는 원본데이터에 대한 연결 정보를 설정한다.
- filters: Datasource에 정의하고 Dataset 에서 사용하는 필터를 사전에 정의 하고자 할때 사용한다.


## Datasource

Connector, TargetObject, Filter을 사용하여 원본데이터에 대한 정보를 기술한다.

### Datasource 목록

Dataset의 목록을 조회한다.

![](<.gitbook/assets/CogInsight | STATS 2022-05-06 17-59-13.png>)

목록에서 이름을 선택하면 해당 Datasource의 상세를 조회하며, 생성 버튼을 눌러 신규 Datasource 를 생성할 수 있다.


### Datasource 상세

![](<.gitbook/assets/CogInsight | STATS 2022-05-06 18-26-01.png>)

Dataset의 상세를 조회한다.


수정 버튼을 선택하면 편집상태로 전환하여, 데이터셋을 수정할 수 있다.



### Datasource 편집

![](<.gitbook/assets/CogInsight | STATS 2022-05-06 18-17-03.png>)


1. 이름을 입력한다.  Dataset에서 선택할때 사용하는 이름.
2. 설명을 입력한다.
3. 저장소에 대한 연결 정보. 미리 정의되어 있는 Connector 정보에서 선택한다.
4. 실제 대상 리소스를 입력한다. (예, 테이블의 이름, 컬렉션의 이름)
5. Date 필드를 입력한다. Date 필드는 Dataset의 정의에 필수 항목으로 반드시 지정되야 하며, Dataset에서는 "date" 라는 이름으로 필드를 사용할 수 있다.
6. 대상리소드의 컬럼별로 사용하고자 하는 필터를 지정한다. 
    * 반드시 사용되어야 할 필터는 "is required" 항목을 Required로 선택한다.
    * 필터를 지정한 필드는 Dataset 에서 사용할때 Selection 필드로 처리되어 사용자가 값을 직접 입력하는 것이 아니라, 선택하여 지정할 수 있는 편의를 제공한다. 
    * "Required"로 지정한 필드는 반드시 선택해야할 필드와 그 값을 사전에 제공함으로서 사용자이게 노출시키지 말아 야할 데이터를 제한하거나, 전체 데이터를 불필요하게 한꺼번에 가져오는 동작으로 시스템의 성능이 저하되는 일을 방지할 수 있다.



## Connector

Datasource에 대한 물리적인 연결을 설정한다.

### Connector 목록

![](<.gitbook/assets/CogInsight | STATS 2022-05-06 18-05-44.png>)

Connector의 목록을 조회한다.

목록에서 이름을 선택하면 상세화면으로 이동하며, 생성 버튼을 눌러서 신규 Connector 를 생성할 수 있다.

### Connector 상세
![](<.gitbook/assets/CogInsight | STATS 2022-05-06 18-07-55.png>)

Connector의 상세화면이며, 수정 버튼을 눌러서 편집상태로 전환할수 있다.

### Connector 편집
![](<.gitbook/assets/CogInsight | STATS 2022-05-06 18-11-43.png>)

Connector의 편집화면

1. 이름을 입력한다. Datasource에서 Connector를 선택할 때 사용하는 이름.
2. 설명을 입력한다.
3. Connector의 종류를 입력한다. 현재는 mongodb 만을 제공한다.
4. Connector의 종류에 따른 연결 설정 정보 입력


## Filter

### Filter 목록

![](<.gitbook/assets/CogInsight | STATS 2022-05-06 18-18-18.png>)

Filter의 목록을 조회한다. 

목록에서 이름을 선택하여 상세화면으로 이동하거나, 생성 버튼을 선택하여 신규 Filter를 생성할 수 있다.

### Filter 상세
![](<.gitbook/assets/CogInsight | STATS 2022-05-06 18-19-30.png>)

Filter의 상세 조회화면

수정 버튼을 선택하여 편집상태로 전환할 수 있다.


### Filter 편집
![](<.gitbook/assets/CogInsight | STATS 2022-05-06 18-21-18.png>)

Filter의 상세 편집화면

1. 이름을 입력한다. Datasource를 설정할때 사용하는 이름. 
2. 설명을 입력한다.
3. Filter의 아이템목록을 입력한다. value는 실제값이며 label은 Dataset에서 선택할 때 보여지는 표시 값이다.