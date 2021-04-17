이전 포스팅에서 relational algebra에 대해 다뤘는데, 예시로 다뤘던 것처럼 operator를 하나만 사용해도 원하는 결과를 얻어낼 수 있지만, 일반적으로 의미있는 query를 하기위해서 여러operator가 결합된 형태로 사용됩니다.



### Combining Operations to Form Queries

다음과 같은 Movie 테이블이 존재한다고 할 때

**Movie**

|     title     | year | length | inColor | studioName | producerCNo |
| :-----------: | :--: | :----: | :-----: | :--------: | :---------: |
|   Star Wars   | 1977 |  124   |  true   |    Fox     |    12345    |
| Mighty Ducks  | 1991 |  104   |  true   |   Disney   |    67890    |
| Wayne's World | 1992 |   95   |  true   | Paramount  |    99999    |

여기서 상영시간(length)이 최소 100분이고, Fox사에 의해서 만들어진 영화의 title과 year를 찾고 싶은 경우 어떻게 expression을 줘야할까요?



차근차근 하나씩 찾아보면,

1. 먼저 Movie의 tuple 중 length가 100 이상인 tuple을 찾습니다.
2. Movie의 tuple 중 studioName이 Fox인 tuple을 찾습니다.
3. (1)과(2)의 교집합을 찾습니다.
4. 교집합에서 title, year attribute를 projection 합니다.



이를 하나의 expression으로 표현하면 다음과 같습니다.

**π title,year(σ length ≥ 100(Movie) ∩ σ studioName='Fox'(Movie))**



### Equivalent Expressions and Query Optimization

이것만 있을까요?

**π title,year(σ length ^ studioName='Fox'(Movie))** 

이것도 위의 식과 동일한 결과를 내게됩니다.

이렇듯  query는 같은 결과를 이끌어내는 다양한 식이 존재합니다. 

우리가 다루는 보통의 프로그래밍 언어(C, Java 등등)는 우리가 코딩한데로 실행되지만, SQL은 우리가 식을 어떻게 주던 알아서 최적화(Query Optimization)한 다음에 실행하기 때문에 query <u>결과가 정확하게 나오도록 작성하는게 중요합니다.</u>



두 개의 테이블에서 query 하는 것을 살펴보도록 하겠습니다.

다음과 같이 두 개의 테이블이 있다고 할 때,

**Movie1(title, year, length, filmType. studioName)**

**Movie2(title, year, starName)**



여기서 **상영길이가 최소 100분(100분 이상)인 영화에 출연한 스타의 이름을 찾아라** 라고 한다면 어떻게 query를 줘야할까요?

상영길이(length)는 Movie1에 있고, 스타의 이름(starName)은 Movie2에 있는데, 어떻게 찾아야 할까요?



먼저 Movie1, Movie2는 title, year attribute를 공통으로 갖고 있기 때문에 natural join 해줍니다. (Movie1 ⨝ Movie2)

이렇게 natural join할 경우 attribute가 title, year, length, filmType, studioName, starName을 갖는 table이 하나 생성되는데 Movie1과 Movie2의 title, year가 같은 tuple만 살아남습니다.

**Movie1 ⨝ Movie2 **

| title | year | length | filmType | studioName | starName |
| :---: | :--: | :----: | :------: | :--------: | :------: |
|       |      |        |          |            |          |

그럼 이제 그 중 lenth가 100분 이상인 걸 selection하고,

**σ length ≥ 100 (Movie1 ⨝ Movie2)**

거기서 starName만 projection하면 저희가 원하는 결과를 얻어낼 수 있습니다.

**π starName (σ length ≥ 100 (Movie1 ⨝ Movie2))**



**<u>원하는 정보가 이렇게 흩어져 있을 때는 natural join하거나 theta join한 다음에 selection하고 projection하면 저희가 원하는 정보를 query 할 수 있습니다.</u>**



### Renaming

  **ρ s(A1, A2, ···, An)(R)**

테이블 이름을 s로 바꾸고 첫번째 column은 A1, 두번째 column은 A2 ··· n번째 column은 An으로 바꾸는 operator입니다.



**ρ s(R)**

이렇게 줄 경우 그냥 테이블 이름만 s로 변경합니다.



#### Example

**R**

|  A   |  B   |
| :--: | :--: |
|  1   |  2   |
|  3   |  4   |

**S**

|  B   |  C   |  D   |
| :--: | :--: | :--: |
|  2   |  5   |  6   |
|  4   |  7   |  8   |
|  9   |  10  |  11  |

**R X ρ s(X,C,D)(S)** 

|  A   |  B   |  X   |  C   |  D   |
| :--: | :--: | :--: | :--: | :--: |
|  1   |  2   |  2   |  5   |  6   |
|  1   |  2   |  4   |  7   |  8   |
|  1   |  2   |  9   |  10  |  11  |
|  3   |  4   |  2   |  5   |  6   |
|  3   |  4   |  4   |  7   |  8   |
|  3   |  4   |  9   |  10  |  11  |

R과 S를 cartesian product하면 충돌이 생기니까 renaming해서 cartesian product함.



### Relationships Among Operations

계산기에서 빼기는 10의 보수로, 곱하기는 더하기를 반복해서 함으로써 동일한 계산결과를 낼 수 있기 때문에 더하기, 나누기만 구현해서 계산기를 완성할 수 있음(간단한 사칙 연산 계산기) 

relational algebra도 natural join, theta join을 다른 연산으로부터 유도해서 사용할 수 있다는 것을 보여주는 거니까 그 정도만 알고 넘어가도 될 것 같습니다.



**· R ∩  S = R - (R - S)**

**· R ⨝  c S = σ c(R X S)**

이론적으로 가능하지만 데이터가 폭발적으로 증가해서 엄청 느려지기 때문에 안씀

**·R ⨝ S = πL (σc (R X S))** 

πL - 중복되는 걸 한 번만 나타나게 함.



### Linear Notation

programming language에서 variable(변수)로 사용하는 개념이 여기서는 **Linear Notation**이라고 합니다.

임시적인 변수에 중간 과정을 저장하는 걸 얘기하는데 다음과 같이 표현합니다.

**R(t, y, l, i, s, p) := σ length ≥ 100 (Movie)**

R이라는 테이블에 t, y, l, i, s, p라는 attribute에 Movie 테이블에서 length가 100 이상인 tuple을 저장하라.

**T(t, y, l, i , s, p) := R ∩ S**

**Answer(title, year) := π t,y(T)**

T 테이블에 R ∩ S의 결과를 담고, Answer 테이블에 t, y를 projection한 결과를 담아라.



데이터베이스 설계에 있어서 **schema를  설계하는 것**과 **데이터가 지켜야할 제약 조건**을 표현하는 건 굉장히 중요합니다. 

relational algebra로 제약조건을 표현하는 것을 알아보도록 하겠습니다.

### Relational Algebra as a Constraint Language

| Expression |                           Meaning                            | Other Expression |
| :--------: | :----------------------------------------------------------: | :--------------: |
|   R = ∅    |    R은 공집합이어야 한다. (The value of R must be empty)     |      R ⊆ ∅       |
|   R ⊆ S    | R의 모든 tuple들은 S의 tuple에도 있어야한다. (Every tuple in the result of R must also be in the result of S.) |    R − S = ∅     |

두 표현은 사실 같은겁니다. Other Expression에 적힌 것처럼 서로의 방식으로 표현할 수 있기 때문이죠.



### Constraints

- Referential Integrity

**Movie(<u>title</u>, <u>year</u>, length, genre, studioName, producerCNo)**

**MovieExec(certNo, name, address, netWorth)**

책의 저자는 설명을 위해 영화와 영화감독이 다대일 관계(영화 감독은 한 명 밖에 없다 - 한 명의 영화 감독이 여러 편의 영화는 만들 수 있지만, 영화 하나 당 여러 명의 감독은 존재할 수 없다는 의미)로 설정했는데

*+다대일 관계를 어떻게 알 수 있냐면 foreign key(외래키 - 일인쪽 테이블의 key를 다인쪽 테이블로 보내는 것을 말한다.)를 보고 알 수 있는데, 나중에 다룰 내용이라 그냥 넘어가도 좋다.*

<u>**만약 Movie 테이블의 producerNo에 101번이 존재한다면 MovieExec에도 101번 certNo가 존재해야한다는게 Referential Integrity다.**</u>



이를 Constraints로 표현하면 **π producerCNO(Movie) ⊆ π certNo(MovieExec)**가 된다.



- Key constraints

MovieStar(<u>name</u>, address, gender, birthdate)

<u>**MovieStar에 대해 name을 key값으로 설정시 name이 같은 tuple은 존재할 수 없다는게 Key Constraints이다.**</u>



이를 Constraints로 표현하면 조금 어려운데, MovieStar 테이블을 copy해서 MS1, MS2라는 테이블을 만든 다음 (ρ MS1(name,address,gender,birthdate) (MovieStar), ρ MS2(name,address,gender,birthdate) (MovieStar))

cartesian product하고 (즉, 자기자신을 cartesian product하는 것)

name이 같고 address만 다른 것을 selection한게 NULL이 아니면 Key Constraints를 위반한 것.

**σ MS1.name=MS2.name∧MS1.address≠MS2.address(MS1 × MS2) = ∅** 



- Domain Constraint

attribute의 값을 제한합니다. 

MovieStar attribute인 gender는 M, F 값만 가질 수 있도록합니다.

**σ gender≠′F ′∧gender≠′M′(MovieStar) = ∅**



- General Constraint

real world에서 존재하는 일반적인 제약조건

MovieStudio의 president가 되려면 연봉이 적어도 10,000,000$ 이상이어야 한다. 는 조건이 있다면

**Studio(<u>title</u>, <u>year</u>, length, genre, studioName, presCNo)**

**MovieExec(certNo, name, address, netWorth)**

두 개의 테이블이 있을 때, 다음과 같이 표현할 수 있습니다. (둘 다 동일한 표현)

**σ networth<10000000(Studio ⨝ presCNo=certNo MovieExec) = ∅**

**π presCNo(Studio) ⊆ π certNo(σ netWorth≥10000000(MovieExec))**

Studio의 presCNo를 projection한 결과가 MovieExec에서 netWorth가 10000000 이상인 것들을 selection한 다음 certNo에 대해 projection한 결과의 부분집합이어야 한다.



데이터베이스 설계에 있어서 <u>**schema를  설계하는 것**</u>과 **<u>데이터가 지켜야할 제약 조건</u>**을 표현하는 건 굉장히 중요하기 때문에 잘 정리해야겠습니다.

