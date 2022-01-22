# Ch02. Artificial Neural Network

### 목차

- [Artificial Neural Network의 concept](#Artificial-Neural-Network의-concept)
- [Formal Representation of Neural Network](#Formal-Representation-of-Neural-Network)
- [Activation Functions](#Activation-Functions)
- [Optimization](#Optimization)
- [Initialization](#Initialization)
- [Cost Function](#Cost-Function)
- [Forward Propagation](#Forward-Propagation)
- [Back Propagation](#Back-Propagation)
- [Learning Rate Scheduling](#Learning-Rate-Scheduling)
- [Input Normalization](#Input-Normalization)


Discriminant Function을 기반으로 하는 Artificial Neural Network에 대해 공부하자.

## Artificial Neural Network의 concept

인공신경망(Artificial Neural Network)은 실제 신경세포, 다른 말로는 뉴런(neuron)에서 따온 개념이다.
뉴런의 끝과 끝에서 신호가 전달되는 과정을 다음과 같이 모델링한 것이다.<br>

<!--이미지-->

Artificial Neural Network의 목적은 training data `{xj, yj*}`(j=1,2,...,M)에 대해 정답 label인 `yj*`에 가장 가까운 yj를 예측할 수 있는 parameter 값들을 찾는 것이다. 이렇게 parameter 값들을 찾아가는 과정을 **Training**이라고 하고, 정답 labeling이 되지 않은 test data에 대한 예측값을 출력해보는 것을 **Testing**이라고 한다.

## Formal Representation of Neural Network

각각의 뉴런들을 `z=w∙a+b`라고 표시할 수 있다.
`z`는 forward propagation을 벡터로 나타난 것이고 `w`, `a`, `b`는 각각 가중치(weight), 출력 신호(activation), 바이어스(bias)를 의미한다.

여기서 **forward propagation**이란 입력 신호를 다음 layer로 전달에 전달을 거듭해서 네트워크의 마지막 layer까지 보내는 전체적인 연산 과정을 의미한다.

네트워크의 layer라는 건 수직으로 나열된 뉴런 한 묶음을 말하는데, 네트워크에서 어디에 위치해 있느냐에 따라 **input layer**, **hidden layer**, **output layer**로 구분할 수 있다.<br>
보통 대문자 `L`이라 하면 네트워크의 전체 layer 개수를 나타내고, 소문자 `l`을 첨자로 쓰면 l번째 layer를 가리키는 것이다.
그리고 각 layer의 k번째 뉴런이라는 걸 표현하기 위해 `k`를 첨자로 사용한다.

<!--이미지-->

## Activation Functions

<!--activation function이란--->

- ### Sigmoid
- ### Hyper tangent
- ### ReLU
- ### Leaky ReLU

## Optimization

> Gradient Descent

## Initialization

## Cost Function

## Forward Propagation

## Back Propagation

## Learning Rate Scheduling

## Input Normalization
