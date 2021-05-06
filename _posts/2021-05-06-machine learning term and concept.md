------

나는 마블 영화들 중 아이언맨을 가장 좋아한다. 뭔가 현실적이여서(실현가능할 것 같아서) 그런지 더 멋있게 느껴진다.

토니 스타크가 슈트를 입고 자비스와 대화하는 장면을 볼 때마다 *나도 저런 인공지능이 있었으면 좋겠다!!* 하고 생각했었다.

![jarvis](https://user-images.githubusercontent.com/76269316/117230593-66cd0780-ae58-11eb-820c-30c4800c2ec8.png)

그래서 인공지능을 한 번 공부해보기로 했다. 다음 학기에 인공지능 수업이 있긴하지만 요새 마음도 싱숭생숭하고, 벌써 3학년 1학기 절반이 지나갔다는 압박감(?)에 갑자기 막 공부가 하고 싶어졌다.

어제 밤에 막 인공지능 공부법, 강의를 찾아보니까 홍콩 과학기술대학교 김성훈 교수님의 [모두를 위한 머신러닝 / 딥러닝](http://hunkim.github.io/ml/) 강의가 괜찮아보여서 강의를 듣고 정리해보려고 한다.

------



[ML lec  01 - 기본적인 Machine Learning의 용어와 개념 설명](https://youtu.be/qPMeuL2LIqY)

### Machine Learning

일종의 소프트웨어.  

우리가 사용하는 일반 프로그램의 경우 우리가 입력을 주면 입력을 기반으로 데이터를 보여준다거나하는 출력을 주는데, 그런 프로그램을 **explicit program**이라고 한다.



### Machine Learning

우리가 사용하는 일반 프로그램의 경우 우리가 입력을 주면 입력을 기반으로 데이터를 보여준다거나하는 출력을 주는데, 그런 프로그램을 **explicit(분명한) program**이라고 한다.

하지만 이렇게 explicit하게 구현하기 어려운 프로그램들이 존재함.  그 중 하나가 이메일 스팸 필터인데 규칙들이 너무 많아서 이런 경우에는 explicit하게 만들 수 없다. 요새 대두되고 있는 자율주행의 경우도 그렇다.

이렇게 일일이 모든 경우에 대해서 프로그래밍을 할 수 없으니까

프로그램 자체에서 어떤 데이터를 보고  스스로 학습해서 알아서 출력값을 결정하는 프로그램의 일종을 머신러닝이라고 한다.



### Supervised / Unsupervised Learning

학습하는 방법에 따라서 supervise와 unsupervised로 나뉩니다.



### supervised learning

<u>labeled 데이터(training set)</u>를 가지고 학습하는 것

supervised learning의 대표적인 예가 Image labeling입니다.

고양이 그림, 강아지 그림, 컵 그림, 모자 그림 이렇게 labeled된 데이터들을 가지고 학습을 하는 것이 supervised learning입니다.

![image](https://user-images.githubusercontent.com/76269316/117240987-01cfdc80-ae6d-11eb-86c3-60d014d36e8e.png)



### unsupervised learning

un-labeled 데이터를 가지고 학습하는 것

unsupervised의 대표적인 예가 google news grouping(유사한 뉴스들을 그룹핑), word clustering(비슷한 단어들끼리 모음) 있습니다.



저희는 supervised learning에 대해 주로 다루는데, 이를 통해 Image labeling, Email spam filter, Predicting exam score등을 할 수 있습니다.



### Training data set

labeled 데이터(training data set)를 가지고 학습시켜 머신러닝 모델을 생성한 다음, 내가 모르는 X test의 값을 주면 모델이 생각한 답(Y=3)을 주는 것이 supervised learning입니다. 알파고가 대표적인 예입니다.

![image](https://user-images.githubusercontent.com/76269316/117242728-c59e7b00-ae70-11eb-8367-625e1272356f.png)



그런데 supervised learning도 결과에 따라 다르게 나뉘는데,

시험 성적을 예측하는 시스템의 경우 0~100점 사이의 점수를 예측해야 하는데, 이런 예측을 하는 것을 **regression**이라고 하고,

점수로 매기지 않고, 이 사람이 pass했느냐 non pass했느냐 두 가지 결과중 하나로 분류하는 것을 **binary classfication**이라고 합니다.

학점(A, B, C, D, F)으로 예측하는 것을 **multi-label classfication**이라고 합니다.



[ML lec 02 - Linear Regression의 Hypothesis 와 cost 설명](https://youtu.be/Hax03rCn3UI)

### Predicting exam score : regression

| x(hours) | y(score) |
| -------- | -------- |
| 10       | 90       |
| 9        | 80       |
| 3        | 50       |
| 2        | 30       |

어떤 학생이 몇 시간 공부했더니, 얼마 정도의 성적이 나왔는지 데이터를 가지고 supervised learning을 해서 생성한 모델에게 7시간 공부한 학생의 성적이 얼마일까? 하고 물어보면, 학습된 데이터를 기반으로 65점 정도 받을거라고 예측하는데, 이것을 **Linear Regression**이라고 합니다.

![image](https://user-images.githubusercontent.com/76269316/117244486-0b107780-ae74-11eb-985b-0cf0c6b4a8e4.png)

### Regression

주어진 데이터가 x가 1일 때 y는 1이고, x가 2일 때 y는 2, x가 3일 때 y는 3이라고 하면 이를 그래프로 나타내면

| x    | y    |
| ---- | ---- |
| 1    | 1    |
| 2    | 2    |
| 3    | 3    |

x : 예측을 하기 위한 기본적인 자료(feature라고 합니다.)

y : 예측해야하는 대상



다음과 같이 직선 형태로 나타나게 됩니다. 이런 Linear Regression 모델을 학습시키기 위해서는 가설(Hypothesis)을 세울 필요가 있는데 이런 직선 형태의 가설을 Linear Hypothesis라고 합니다.

세상의 많은 데이터(현상)들이 Linear 형태로 표현될 수 있습니다. 공부양과 성적의 상관관계(공부를 많이 할수록 성적↑), 집의 크기와 가격의 상관관계(집의 크기가 클수록 가격 ↑)등이  Linear하게 가설을 세울 수 있습니다.

직선이기 때문에 이렇게 표현할 수 있습니다. 

##### **H(x) = Wx + b**

![linear hypothesis1](https://user-images.githubusercontent.com/76269316/117245919-a3a7f700-ae76-11eb-9e17-c98cbc50ff27.png)



아래처럼 여러 가설을 세울 수 있는데, 이 직선 중 어떤 직선이 우리가 갖고 있는 데이터와 잘 맞는 직선인지를 찾아야 하는데, 

![linear hypothesis2](https://user-images.githubusercontent.com/76269316/117245942-ac98c880-ae76-11eb-89c5-be6f960ffb7d.png)



이는 실제 데이터와  가설이 나타내는 점 사이의 거리( **H(x) - y**)를 계산해냄으로써 알 수 있는데,

![linear hypothesis3](https://user-images.githubusercontent.com/76269316/117246376-7e67b880-ae77-11eb-877d-f85cb04eaed8.png)



### Cost function (Loss function)

이를 cost function이라고 합니다.

 **H(x) - y** 하지만 이 값은 양수가 될 수도 있고, 음수가 될 수도 있기 때문에 그냥 사용하지 않고, 다음과 같이 제곱해서 사용합니다.

![image](https://user-images.githubusercontent.com/76269316/117246677-0221a500-ae78-11eb-9429-d831c2c5b85c.png)

이렇게 제곱할 경우 항상 양수로 값이 표현되고, 제곱이기 때문에 차이가 클 경우 더  패널티를 많이 주게됩니다. (거리가 작을수록 좋으니까)



위 그래프의 cost function은 다음과 같습니다. 데이터와 직선 위의 점 사이의 거리를 각각 제곱한 뒤 이를 3(데이터의 개수)으로 나눠서 평균을 낸 것입니다.

![image](https://user-images.githubusercontent.com/76269316/117246793-34cb9d80-ae78-11eb-9328-bb7ecb52a636.png)

cost function을 formal하게 정리하면 다음과 같습니다. (m = 학습데이터의 개수)

![image](https://user-images.githubusercontent.com/76269316/117246916-5fb5f180-ae78-11eb-94e1-b8771c024541.png)

위에서 얘기한 것처럼 Hypothesis는 직선이기 때문에 **H(x) = Wx + b** 다음과 같이 표현할 수 있고, 이를 cost function에 대입하면 cost function은 w와 b의 function이 되게 됩니다.

![image](https://user-images.githubusercontent.com/76269316/117247052-9429ad80-ae78-11eb-8d47-b95b95677d7a.png)

**결국, Linear Regression의 학습은 이 cost를 가장 작게하는 W와 b값을 찾는 것입니다.**