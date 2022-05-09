# Dataset

비정헝의 원본데이터는 통계를 처리하기에 다소 까다롭거나, 불가능한 경우가 있기 때문에 2차원의 테이블 형식의 데이터로 가공해야만 도구를 사용하여 퉁계를 처리할 수 있게 된다. 데이터 셋은 이러한 1차 가공을 처리하기 위해서 사용하며, 원본데이터가 무엇인지를 선택하고, 원본 데이터의 칼럼을 선택및 가공하여 새로운 필드를 만들며, 필터를 사용하여 원본으로부터 가져올 데이터의 범위를 제한할 수 있다. 

데이터셋을 정의한 후 실시간및 배치 업데이트 처리 기능을 통해서 원본데이터로부터  테이블 형식의 2차원 데이터가 생성된다. 이렇게 생성된 데이터가 Panel을 생성할때 집계 대상 데이터로서 사용된다. 

### Dataset 목록

![](<.gitbook/assets/CogInsight | STATS 2022-05-08 14-50-16.png>)

Dataset의 목록을 조회한다.

목록에서 이름을 선택하여 상세로 이동하고나, 생성 버튼을 선택하여 신규 데이터 셋을 생성할 수 있다.

### Dataset 상세

![](<.gitbook/assets/CogInsight | STATS 2022-05-08 14-53-05.png>)

1. 데이터셋의 기본 정보를 표시한다.
2. 생성된 데이터를 조회한다.
3. 실시간으로 Dataset의 데이터를 생성한다
4. 배치처리로 Dataset의 데이터를 생성한다.
5. 수정 버튼을 선택하여 데이터셋의 편집 상태로 이동할 수 있다.

### Dataset 편집
![](<.gitbook/assets/CogInsight | STATS 2022-05-08 14-57-52.png>)

1. Dataset의 이름을 입력한다.
2. Datasource를 선택한다. Datasource는 원본데이터이며 관리자메뉴에서 등록된 여러 목록중에서 하나를 선택한다.
3. Required Filter. Datasource를 사용할 때 필수로 사용하는 필터이며 관리자 메뉴에서 Datasource를 등록할 때 지정된다.
4. 설명을 입력한다.
5. Dataset의 Column 정보를 등록한다. Datasource 필드로부터 Dataset의 필드를 만들어 내는 스펙을 지시한다.
6. Dataset의 Filter 정보를 등록한다. Datasource로 부터 데이터를 가져올때 범위를 제한하기 위해서 사용된다.
7. Dataset의 설정을 저장하기 전에 가공처리되어 생성될 데이터를 미리보여준다. 
8. Dataset의 설정을 수정하고 저장할때, Column과 Filter 를 수정한 경우는 데이터의 일관성을 위해서 이전에 생성되어 저장되어 있던 모든 데이터를 삭제한다.


### Column 편집
![](<.gitbook/assets/CogInsight | STATS 2022-05-06 16-32-25.png>)

1. date 컬럼은 필수 이며 Read-Only 이다.
2. Required Filter 에 사용되는 Column 또한 Read-Only 이다.
3. 새로운 필드를 등록한다 
4. Dataset의 컬럼 이름을 입력한다.
5. 검색버튼을 선택하여, Datasource 로 부터 사용가능한 필드 목록을 얻어 낼 수 있다.
6. 컬럼의 타입을 선택할 수 있다. 검색버튼을 선택하여 Datasource의 필드를 선택한 경우 자동으로 세팅되며 수정가능하다.
7. Datasource 의 필드 이름을 입력한다. $ prefix를 사용하여 지정해야 하며, 검색버튼을 선택하여 Datasource의 필드를 선택한 경우 자동으로 세팅되며 수정가능하다.
8. Column 값 편집기를 팝업한다. column의 타입이 array, keyword, category 일 경우 표시된다.


#### script 편집기&#x20;

![](<.gitbook/assets/Coginsight Stats 2022-01-13 18-12-03.png>)

* 기본이 되는 편집기이며, 컬럼타입이 string,bookean,number,date 일때 적용된다.
* datasource 의 컬럼을 지정할 때는 \$field\_path 식으로 $ prefix 를 사용한다
* field\_path는 . 표현식으로 하위필드를 사용할 수 있으며, \[n] 표현식으로 배열형식의 필드의 특정 row 데이터를 선택할 수 있다.
  * (예: $system.device\_type, $intents\[0].intent )
*   javascript 문법에 따르지만, 다음의 규칙으로 제한돤다.

    * . 표현 식으로 변수에 이어서 기술하는 . 표현식의 함수를 이용하는 방식은 필드이름의 연속인지 구분할 수 없으므로 허용되지 않는다. 즉, $web.substr(0,3) 등을 사용할 때는, ($web).substr(0,3) 과 같이 사용한다.



#### array 편집기&#x20;

![](<.gitbook/assets/Coginsight Stats 2022-01-13 18-28-33.png>)

* 기본 컬럼 선택시에 타입이 array 인 경우 편집버튼을 누르면, value 로 입력한 datasource의 컬럼의 값을 베이스로 하여 array 편집기가 팝업된다.

![](<.gitbook/assets/Coginsight Stats 2022-01-13 18-25-42.png>)

* array 컬럼 편집기는 기본 컬럼 편집기에서 값으로 선택한 필드데이터의 스키마를 기반으로 하여, 여기서 사용하고자 하는 필드를 선택/가공하여 정의 하는 편집기이다.
* Dataset 은 내부적으로 1:N 관계의 서브테이블로 정의된다.

#### category 편집기&#x20;

![](<.gitbook/assets/Coginsight Stats 2022-01-14 00-51-16.png>)

* 기본 컬럼 선택시에 타입이 category 인 경우 편집버튼을 누르면, value 로 입력한 datasource의 칼럼을 기반으로 하여 category 편집기가 팝업된다.

![](<.gitbook/assets/Coginsight Stats 2022-01-14 00-55-01.png>)

* category 편집는 string 타입의 컬럼값을 기반을 카테고리로 분류하여 이를 컬럼의 값으로 사용하고자 할 때 사용된다
* 행의 좌측에 카테고리의 값을 입력하고 오른쪽에는 datasource의 값의 리스트를 콤마로 구분하여 여러개를 넣을 수 있도록 되어 있다.

#### keyword 편집기&#x20;

![](<.gitbook/assets/Coginsight Stats 2022-01-14 00-51-16.png>)

* 기본 컬럼 선택시에 타입이 keyword 인 경우 편집버튼을 누르면, value 로 입력한 datasource의 칼럼을 베이스로 하여 keyword 편집기가 팝업된다.

![](<.gitbook/assets/Coginsight Stats 2022-01-14 01-02-22.png>)

* keyword 편집기는 입력 방식은 category 키워드와 동일하나, datasource 필드값과 동일한 경우에 제한되는 것이 아니라, 포함하고 있는 경우를 포함한다.
* 주 사용처는 사용자의 입력 값중에서 관심 있는 키워드가 얼마나 자주 언급이 되는지를 파악할 때 사용할 수 있다.

### Filter 편집

![](<.gitbook/assets/Coginsight Stats 2022-01-14 01-37-20.png>)

1. 필터는 datasource에서 가져올 데이터의 범위를 제한하는 용도로 사용된다. datasource 를 선택할 때 자동으로 나오는 기본 필터 이외에 추가로 필터 아이템을 지정할 수 있다.
2. 행의 왼쪽에 datasource 필드를 입력하고, 오른쪽 입력란에는 해당 필드의 값을 지정한다.&#x20;
3. 필터는 equal 조건만 지원된다.&#x20;

### Preview&#x20;

![](<.gitbook/assets/Coginsight Stats 2022-01-14 01-42-17.png>)

1. Preview는 지금까지 입력한 설정 값들을 적용하여, datasource 로 부터 실시간으로 조회/변환 처리된 데이터를 표시한다.&#x20;
2. 설정한 내용을 테스트하는 용도로 사용할 수 있다.


### Dataset 비우기 및 삭제

![](<.gitbook/assets/Coginsight Stats 2022-01-14 02-08-12.png>)

1. Dataset에 쌓여 있는 데이터를 1)비우기를 하거나 , 2)데이터셋 자체를 삭제할 수 있다.&#x20;

### Dataset 조회

![](<.gitbook/assets/Coginsight Stats 2022-01-14 01-46-25.png>)

* Dataset이 배치및 실시간 job 을 실행하여 실제 처리되어 저장된 상태의 데이터를 조회한다.&#x20;

### Dataset Live Update 실행

![](<.gitbook/assets/Coginsight Stats 2022-01-14 01-50-08.png>)

* Live Update 탭에서 실행 버튼을 누르면 실시간 Job 이 실행되며, 이 Job은 최근 5분 데이터를 조회해와 Dataset의 레코드르 번환하여 저장하는 동작을 5분 단위로 스케줄링되어 실행한다.
* stop버튼을 사용하여 Job을 중지시킬 수 도 있다.&#x20;

### Dataset Batch Update실행

![](<.gitbook/assets/Coginsight Stats 2022-01-14 02-01-56.png>)

* datasource로 부터, 한번에 다량의 데이터를 가져와 가공/저장 할때 사용한다.
* 실행시 필터를 지정하여 Datasource로 가져오는 데이터의 범위를 제한할 수 있다.
* 이 Job은 한번만 실행되며, 실행이 끝나면 즉시 종료된다.&#x20;
