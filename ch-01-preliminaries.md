# Ch01. Preliminaries

### 목차

- [Preprocessing](#Preprocessing)
- [Feature Extraction](#Feature-Extraction)
- [Classification](#Classification)


컴퓨터에게 어떤 연산을 시키기 위해 명시적으로 그 과정을 일일이 프로그래밍 해줄 수도 있지만('이런 연산을 해라~' 라고.), 컴퓨터가 연산 과정을 스스로 도출해내도록 데이터만 주고 학습시킬 수도 있다.
이를 기계학습, **Machine Learning**이라고 하는데 **Deep Learning**은 특히 머신러닝 중에서도 수학적인 함수를 만들어내서 컴퓨터를 학습시키는 기법이다.<br>
딥러닝 과정은 크게 Preprocessing → Feature Extraction → Classification으로 나눌 수 있다. 이 세 과정에 대해서 정리해보려고 한다.

## Preprocessing

Preprocessing, 전처리 과정은 학습을 수월하게 하기 위해 입력 데이터를 가공하는 과정이다.<br>
Normalization, De-noising, Cropping 등의 작업을 할 수 있다.<br>

normalization은 배열 형식의 입력 데이터를 말 그대로 정규분포 하게 만드는 것이고, de-noising은 입력 신호에 낀 잡음을 제거하는 것이다.
그리고 cropping은 예를 들어 이미지 데이터의 필요한 부분만 사용하도록 이미지를 자르는 것이다.

## Feature Extraction

- feature<br>
  : 전처리 작업을 마친 입력 데이터에 대해 feature를 뽑아낼 수 있다. 여기서 `feature`란 데이터 간에 구별되는 독창적인 특징을 말한다.<br>
  효과적인 구별을 위해선 feature 수가 충분히 많아야 하는데, 그렇다고 feature 수가 너무 많으면 redundancy가 생겨서 error rate이 높아질 수 있다.
  
- prototype<br>
  : 정답이 있는 학습 데이터의 sample, 즉 `labeled training sample`을 prototype이라고도 한다.
  만약 feature 개수가 2개라고 하면, 각 prototype들은 2차원의 feature vector를 가지게 된다.
  
이제 이 feature vector를 통해 어떤 데이터가 무엇을 가리키는지 그 답을 찾아가는 과정을 수행하게 되는데, 바로 다음에 나올 Classification이다.

## Classification

입력 데이터들이 두 가지 feature에 따라 다음과 같이 plotting 되어 있다고 하자.

![img](https://github.com/hei-jung/deep-learning-study/blob/main/ref_img/ch01_img_01.jpeg)

위 그림에서 파란 점들과 빨간 점들을 얼추 구분(classification) 지을 수 있는 classifier 선을 그을 수 있는데,

![img](https://github.com/hei-jung/deep-learning-study/blob/main/ref_img/ch01_img_02.jpeg)

이 선을 `decision boundary`라고 하고, 특히 여기선 decision boundary가 직선 형태이므로 linear boundary라고 할 수 있다.<br>
그런데 그림을 보면 파란색과 빨간색을 구분하는 선이 있지만 근소한 차이로 파란 점들 사이에 빨간 점이 끼어있기도 하고, 반대로 빨간 점들 사이에 파란 점이 끼어있기도 한다.
즉, linear boundary는 딱딱하게 직선을 그어 데이터들을 분류하다 보니, 분류 작업에 있어서 약간의 오류를 일으킬 수 있다.

![img](https://github.com/hei-jung/deep-learning-study/blob/main/ref_img/ch01_img_03.jpeg)

그렇다고 boundary를 저렇게 구불구불, 복잡하게 정하면 지금 가지고 있는 데이터들에 과적합(`overfitting`)이 돼서 나중에 저 boundary에 맞지 않는 새로운 입력 데이터가 들어왔을 때 오답을 말하게 되어, 오히려 정확도가 떨어지게 된다. 그럼 decision boundary를 어떻게 정해야 좋을까?

![img](https://github.com/hei-jung/deep-learning-study/blob/main/ref_img/ch01_img_04.jpeg)

이렇게 적당히 모델 성능과 추후에 들어올 새로운 입력 간의 tradeoff를 고려하여 정하는 것이 가장 좋다.


> Discriminant Function

k개의 분류 class {S1, S2, S3, ..., Sk}가 있는 k-class problem에서, 모든 class를 적절히 구별해줄 수 있는 함수 gk(x)를 `discriminant function`이라고 한다.
즉 discriminant function은 decision boundary를 정해주는 수학적 함수이다.<br>
discriminant function을 이용한 boundary의 decision rule은 다음과 같다:

```
x belongs to Si,
if gi(x)>gj(x) for all j≠i 
```

예를 들어 class가 S1과 S2로 2개라면 decision rule을,

```
g1(x)>g2(x) => x∊S1
g1(x)<g2(x) => x∊S2
```

라고 쓸 수 있는데 g1(x)와 g2(x)를 g(x)=g1(x)-g2(x)라는 하나의 함수로 나타내서 이렇게 쓸 수 있다.

```
g(x)>0 => x∊S1
g(x)<0 => x∊S2
```

그럼 여기선 g(x)를 discriminant function이라고 말할 수 있다.


- Linear discriminant function<br>
  k-class problem에서 하나의 input vector 당 N개의 feature가 있을 때, discriminant function gk(x)는 다음과 같이 linear하게 나타낼 수 있다.

![img](https://github.com/hei-jung/deep-learning-study/blob/main/ref_img/ch01_img_05.jpeg)

decision boundary는 feature 개수에 따라 직선(line)이 될 수도 있고, 평면(plane)이 될 수도 있다.
물론 직선이면 discriminant function이 직선 방정식, 평면이면 평면 방정식이겠지?

![img](https://github.com/hei-jung/deep-learning-study/blob/main/ref_img/ch01_img_06.jpeg)

또한 k 크기에 따라 여러 discriminant function의 조합을 통해 decision boundary를 정할 수 있다.
