# Panel

### Penel 목록

![](<.gitbook/assets/Coginsight Stats 2022-01-14 10-43-14.png>)

1. Panel의 리스트를 조회한다.&#x20;
2. Panel의 이름을 선택하면 Panel의 상세화면으로 이동한다.&#x20;
3. 생성 버튼을 눌러서 새로운 패널을 생성할 수 있다.

### Panel 편집

1. 패널의 생성과 수정의 화면은 동일하다.
2. 저장 버튼을 누르면 목록에서 생성 버튼을 클릭하여 이동한 경우는 새 Panel이 생성되며, 상세 버틀을 클릭하여 이동했을 때는 해당 패널을 업데이트 한다.

![](<.gitbook/assets/Coginsight Stats 2022-01-14 10-55-21.png>)

1. Title
   * 목록에 표시및 대시보드에서의 패널의 선택시 사용된다.
2. Description
   * Panel에 대한 간략한 설명
3. Query 추가 버튼
   * Query 를 추가한다.
   * 하나의 Panel의 여러개의 Query 로부터 데이터를 가져올 수 있다.
4. Query Editor
   * Query 추가하는 순서대로 Query#1, Query#2 식으로 추가된다.&#x20;
   * Query Editor 에는 아래 설명하는 4가지 콤포넌트로 구성된다.&#x20;
5. Dataset 선택
   * query에 사용될 Dataset을 선택한다.
   * 선택시 나머지 Component 들은 모두 초기화된다.
6. Metrics
   * 집계대상 항목을 추가한다.
   * avg,sum들의 집계 함수및 대상 필드를 선택하여 사용한다.
7. Expressions
   * Metrics 의 필드를 사용하여 추가 필드를 생성할 때 사용한다.
8. Groups
   * query의 group by 에 해당한다.
9. Filters
   * query의 where 절에 해당한다.

### Metrics 편집

\+ 버튼을 눌러서 아이템을 추가한다.

<img src=".gitbook/assets/Coginsight Stats 2022-01-14 11-29-55.png" width="400">

#### Count
<img src=".gitbook/assets/Coginsight Stats 2022-01-14 11-56-35.png" width="400">


* 건수를 집계 할 때 사용한다.
* 기본으로는 조회된 모든 건수를 집계한다.
* Accumulated 를 선택하면 누적 건수를 집계한다.
* Unique는 특정 필드의 중복 제거 건수를 집계한다. Unique Field에서 대상 필드를 선택해야 한다.
* Condition을 선택하면 특정필드의 특정값인 경우만 건수를 집계한다. Condition Field와 Condition Value 를 입력해야 한다. equals 조건 만을 지원한다.
* alias에 이 아이템의 이름을 지정한다.&#x20;

#### Average

<img src=".gitbook/assets/Coginsight Stats 2022-01-14 12-02-34.png" width="400">


* 평균을 구할 때 사용한다.
* Field에 number 타입의 필드를 선택해야 한다.
* alias에 이 아이템의 이름을 지정한다.

#### Sum

<img src=".gitbook/assets/Coginsight Stats 2022-01-14 12-00-42.png" width="400">


* 합계를 구할 때 사용한다.
* Field에 number 타입의 필드를 선택해야한다.
* Accumlated를 선택하여 누적 합을 구할 수 있다.
* alias에 이 아이템의 이름을 지정한다.

### Expression

<img src=".gitbook/assets/Coginsight Stats 2022-01-14 12-06-08.png" width="400">

* Metrics의 아이템을 변수로 이용해서 추가로 필드를 생성할때 사용한다.
* 변수는 $web 과 같이 $ prefix 를 사용한다.
* javascript를 사용한다. 하지만, . 표현 식으로 변수자체의 함수를 이용하는 방식은 허용되지 않는다. 따라서, $web.substr(0,3) 등은 사용할 수 없고, String($web).substr(0,3) 과 같이 사용한다.

### Groups

query의 group by 절에 해당하는 아이템을 편집한다. 보통은 차트상의 X 축에 표시되는 항목이다.

#### Date Histogram

<img src=".gitbook/assets/Coginsight Stats 2022-01-14 12-15-09.png" width="400">


![](<.gitbook/assets/Coginsight Stats 2022-01-18 16-31-16.png>)

* 집계간격을 주어 시간의 흐름에 따라 집계를 할 때 사용한다.
* Field 에 날짜 필드를 선택해야 한다.
* Interval에서 집계 간격을 선택한다.
* alias에 아이템의 이름을 입력한다.

#### Term

<img src=".gitbook/assets/Coginsight Stats 2022-01-14 12-18-14.png" width="400">

![](<.gitbook/assets/Coginsight Stats 2022-01-18 16-36-32.png>)

* 항목의 구분 값을 기준으로 집계를 할 때 사용한다.
* Field에 string 필드를 선택해야 한다.
* Top Limit에 집계구분 값이 너무 많아 차트에 표시하지 못할 수 있으므로 상위 몇개까지 표시할 것인지를 입력한다.
* alias에 아이템의 이름을 입력한다.

#### Daily Term & Montly Term

<img src=".gitbook/assets/Coginsight Stats 2022-01-14 12-20-26.png" width="400">

* Daily Term은 1,2,3,... 31일 구분값 만을 가지고 집계를 할때 사용한다.
* Montly Term은 1,2.3,... 12월 구분 값만 가지고 집계를 할때 사용한다.
* Datily Term과 Montly Term을 함께 사용했을 때, 월별/일자별 비교를 할 때 유용하다.

<img src=".gitbook/assets/Coginsight Stats 2022-01-14 12-43-03.png" width="400">

![](<.gitbook/assets/Coginsight Stats 2022-01-18 16-43-39.png>)

### Filter


<img src=".gitbook/assets/Coginsight Stats 2022-01-14 12-53-56.png" width="400">


* 제한조건을 주어 Dataset 으로 부터 가져오는 데이터의 범위를 제한한다.
* 대상필드이름과 값, 그리고 operator를 선택하여 지정한다.
* operater에는 =,!,<=,>=, in, nin, exists, retention(monthly) 를 지원한다.&#x20;
* retention(monthly) 는 특정필드의 값이 이전달에도 존재했을때 조회하는 조건이다. 재방문율을 집계할 때 사용한다.
  * Field 는 date type이어야 한다.
  * Value 는 재방문율을 계산할 때 사용하는 string 타입의 필드이다.


<img src=".gitbook/assets/Coginsight Stats 2022-01-18 16-50-04.png" width="400">

### Display 세팅

![](<.gitbook/assets/Coginsight Stats 2022-01-18 17-16-43.png>)

* 집계된 데이터를 그래프상에 어떻게 보여줄 지를 세팅한다.
* Metrics의 아이템과 Expressions의 아이템이 모두 디스플레이 세팅의 대상이 된다.

![](<.gitbook/assets/Coginsight Stats 2022-01-18 17-36-09.png>)

* Chart Type: Bar, Line, Pie 를 선택할 수 있으며, None을 선택하면 그래프에 표시하지 않는다.
* Y-Axis 는 left와 right 중에서 선택할 수 있다.
* Chart Type이 Bar 이며 같은 Y-Axis 를 가지고 있는 아이템이 여러개가 있을 경우에는 이를 모두 묶어서 하나의 stack 또는 group bar 그래프로 표시한다.
* Barmode 는 stack 과 group 중 선택할 수 있는데, 첫 번째 item에서 선택한 bardmode가 적용된다.
* Legend 표시 유무를 선택할 수 있다.
