### 데이터 모델 (Data Model)

데이터·정보를 어떤 식으로 모델링할 것인가에 대한 수학적 도구를 말합니다.



일반적인 데이터 모델의 구성 요소 (모델에 따라 세 개를 다 지원할 수도 있고 안할수도 있음)

1. 데이터 구조 (Structure of the data)

2. 데이터 조작 (Operations on the data)

3. 데이터 제약 조건 (Constraints on the data)



데이터 모델의 종류

· <u>Relational Model</u>

데이터를 수학적 관계로 표현한 모델로, DBMS에서 가장 널리 사용되는 모델입니다. 따라서 앞으로 저희가 다룰 데이터 모델은 Relational Model입니다.

· The Semistructured-data Model

웹 언어로 사용되는 HTML은 이 Semistructured-data Model이라고 볼 수 있는 XML의 파생형 언어입니다. XML 자체는 문자 시퀀스로써 자체가 구조를 가지고 있지는 않지만, <head> <body> 같은 tag 자체는 구조를 나타낸다고 볼 수 있습니다.

따라서 이러한 것들은 구조화되긴 됐는데 반 정도만 구조화된 모델이라고 해서 Semistructured data Model이라고 합니다.

· Object - Oriented Data Model

· Object - Relational Model

Relational model을 사용하는 DBMS에서 대게는 Object - Relational Model 역시 지원합니다. 그런데 DBMS마다 구현이 달라서 생각보다 널리 활용되지는 않습니다.

· Hierarchical Model

· Network Model



### Relational Model의 구성 요소

|       title        | year | length | genre  |
| :----------------: | :--: | :----: | :----: |
| Gone With the Wind | 1939 |  231   | drama  |
|     Star Wars      | 1977 |  124   | sciFi  |
|   Wayne's World    | 1992 |   95   | comedy |

**· Relations (Tables) : 위의 테이블과 같은 것을 Relations이라고 합니다.**

**· Attributes (Columns) : 위 테이블에서 Columns을 Attributes라고 합니다.**

title, year, length, genre

**· Schemas : 테이블 구조를 얘기합니다.**

Movies(title, year, length, genre)

**· Tuples : 위 테이블에서 Rows를 Tuples라고 합니다.**

(Gone With the Wind, 1939, 231, drama)

**· Domains : Column의 title이 가질 수 있는 값들의 집합을 말합니다.**

Movies(title: sttring, year: integer, length: integer, genre: string)



### Mathematical Relation

수학적으로 관계를 어떻게 표현할까? 

만약 A라는 남학생 집합과 B라는 여학생 집합이 있을 때 CC관계를 표현하고자 한다고 생각해보자. 둘 사이의 CC관계, 즉 **관계**는 **곱집합**으로 표현할 수 있다. (A, B 집합 각각의 원소의 모든 가능한 pair가 만들어지므로)

*곱집합이 기억나지 않는다면 여기로 (https://ko.wikipedia.org/wiki/%EA%B3%B1%EC%A7%91%ED%95%A9)* 

즉 CC관계를 R이라고 한다면, R은 A와 B의 곱집합의 부분집합으로 표현할 수 있다. **R ⊆ A X B**

따라서 우리는 앞으로 관계를 다음과 같이 표현할 수 있다. 집합 R이 A, B, C 사이의 관계라면 **R ⊆ A X B X C** 이다.

우리가 앞으로 배우고자 하는 Relational Model은 모든 걸 Relation, 관계로 표현한다. 위 Movies 테이블 (정확히는 Relation)도 역시 관계인 것이다.

위 테이블을 수학적 관계로 표현하면 다음과 같다. 

**Movies  ⊆ title X year X legnth X genre**

그리고 title, year, length, genre 각각의 원소는 다음과 같다.

title = {Star Wars, ···}

year = {0, 1, 2 ···}

length = {0, 1, 2 ···}

genre = {drama, sciFi, comedy ···}



### Relation in the Relational Model

Relational Model에서 Relation이란 결국

**Mathematical Relation + Relation Name + Column Names**이다.

 <u>Mathematical Relation</u>은 위에서 말한 수학적 관계이고, <u>Relation Name</u>은 위에서 예시로 다뤘던 Movies 같은 테이블 이름을 말한다.

<u>Column Names</u>는 Relation의 Attributes(속성)를 말하는데 Movies 테이블에선 title, year, length, genre를 말한다.



#### Movies

|       title        | year | length | genre  |
| :----------------: | :--: | :----: | :----: |
| Gone With the Wind | 1939 |  231   | drama  |
|     Star Wars      | 1977 |  124   | sciFi  |
|   Wayne's World    | 1992 |   95   | comedy |



#### Schema

Schema = Relation Name + Attributes 라고 할 수 있는데 그냥 쉽게 생각해서 Structure를 지칭하는 용어라고 생각하면 된다.

Movies(title, year, length, genre)와 같이 표현된다. (Attributes의 순서는 바뀌어도 상관없지만 막 바뀌면 헷갈리니까 **<u>Schema에 명시한 표준순서로 기술</u>**)



#### Tuples 

Relation의 Rows이다. Tuple은 Relation의 Attribute(Column) 각각의 구성 요소다.

Movies의 첫 번째 tuple은 (Gone With the Wind, 1939, 231, drama)이다.

C++라고 생각한다면 Relation은 Class, Tuple은 Object로도 생각할 수 있다.



#### Domains

각각의 Attributes들이 가질 수 있는 값들의 집합을 말하는데, 각 집합의 구성요소는 atomic해야합니다.

무슨 말이냐면 <u>integer, string 같은 elementary type은 가능</u>한데, record structure, set, list, array 같은 것들은 될 수 없다는 의미입니다.

*+String은 Character의 Array 아닌가?*

*String의 경우 워낙 자주·빈번하게 사용하기 때문에 String 전체를 하나의 값으로 처리.*

*하나의 덩어리로 처리할 수 있으면 atomic type이라고 한다.*



### Relation Instances

현재 이 순간에 Movie 테이블에 저장된 tuple의 집합을 Instance라고 함.

tuple이나 schema가 변경될 때마다 테이블이 변경되는데 현재의 테이블을 가리키는 말로 Instance라는 용어를 사용.



### Keys of Relation

Key로 선언된 Attribute 값에 대해 어떤 tuple도 같은 값을 가질 수 없다.

Formal Definition으로는 이렇게 표현된다. 

어떤 Relation R의 Key를 1개나 2개 이상으로 구성된 Attribute 집합 K라고 할 때, R(Relation이므로 집합임)에서 2개의 구별된 어떤 r1, r2 tuple을 선택해도 r1과 r2의 K값 (Attribute의 집합이므로)이 다르면 K를 key라고 한다.



Movies 테이블에서는 다음과 같은 게 Key가 될 수 있다. (Attribute의 집합이니까)

{title} → 다른 영환데 title이 같을 수 있으니까 key 값으로 사용 X

{title, year} → 다른 영환데 같은 제목, 같은 년도에 나올 수 있으므로 key값으로 사용 X

{title, year, length} → 다른 영환데 제목, 년도, 상영시간 까지 같을 수 있으므로(실제로 그럴 확률은 적지만) key 값으로 사용 X 

{title, year, length, genre} → key 값이 될 수 있긴한데 이거 자체가 relation이니까 제목, 년도, 상영시간, 장르가 같은 값을 넣을 수 없음. key 값으로 별로 의미 없음.



이럴 경우 id라는 attribute를 새로 추가해서 key로 만드는게 좋음. (속도도 빠르고 간단하니까)

#### Movies

|  id  |       title        | year | length | genre  |
| :--: | :----------------: | :--: | :----: | :----: |
|  1   | Gone With the Wind | 1939 |  231   | drama  |
|  2   |     Star Wars      | 1977 |  124   | sciFi  |
|  3   |   Wayne's World    | 1992 |   95   | comedy |



책의 저자는 이해를 쉽게하기 위해 {title, year}를 key 값으로 설정.

Schema에서는 밑줄을 긋는 것으로 key 값을 표현 

Movies(<u>title</u>, <u>year</u>, length, genre)



이 세계에서는 다른 영환데 제목, 연도가 같은 영화는 존재할 수 없음 (입력을 못하므로)

