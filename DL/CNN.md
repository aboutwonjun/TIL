# Convolutional Neural Network (CNN)

**Convoultion layer + Neural Network

DNN은 1차원 데이터를 입력으로 받는다. 

하지만 이미지 처리 같은 경우 이미지는 3차원 데이터이기에 flatten 과정 후 기존의 DNN으로 학습시키는 것은

이미지의 공간적/지역적 정보가 손실되고 추상화 과정없이 바로 연산과정으로 진행하기에 학습의 효율성이 낮다.
즉, 이미지 전체를 하나의 데이터로 입력하기에 이미지의 특성을 찾지 못하고, 이미지 위치 변경, 왜곡시 올바른 성능을 기대할 수 없다.

이미지의 공간 정보를 유지한 상태로 학습이 가능한 모델 => CNN

이러한 문제점에서 만들어진 것이 CNN 

![image](https://user-images.githubusercontent.com/76649707/150454229-f7456199-21cb-4c03-8f2b-6e66f52284ac.png)

CNN은 이미지의 특징을 추출하는 부분, 클래스를 분류하는 부분으로 나눌 수 있다.

Feature extraction은 Convolution layer 와 Pooling layer를 여러겹 쌓아 반복하는 형태로 구성된다.

Classification 부분은 이미지 분류를 위해서 Fully Connected Layer가 추가 된다. 


![image](https://user-images.githubusercontent.com/76649707/150454671-b3a2a757-34d2-4149-9657-b1c7a742242e.png)

* Convolution Layer

입력된 이미지를 필터 혹은 커널을 통해 이미지 전체를 훑어줌으로써 특징을 추출하는 과정이다. 
데이터의 특징을 추출하는 과정으로 데이터에 각 성분의 인접 성분들을 조사해 특징을 파악하고 파악한 특징을 한장으로 도출시키는 과정이다. 
여기서 도출된 장을 Convolution Layer라고 한다. 이 과정은 하나의 압축 과정이며 파라미터의갯수를 효과적으로 줄여주는 역할을 합니다

* Stride 

필터가 입력 데이터를 훑는 과정에서 얼만큼 움직이는 지를 Stride라고 한다



![image](https://user-images.githubusercontent.com/76649707/150458121-504d4026-273e-476f-a8f1-cb754986c568.png)

* Padding
합성곱을 계속 수행하게 되면 출력 이미지의 크기가 입력 이미지의 크기보다 작아지게 된다.
이러한 경우 이미지는 점점 작아지며, 픽셀들의 정보가 사라진다. 이러한 점을 해결하기 위해 이용되는 것이 패딩


* Pooling
세로, 가로 방향의 공간을 줄이는 연산.
이미지의 크기를 계속 유지한채 연산을 수행한다면, 연산량이 엄청나게 많아질 것이다.
적당히 크기도 줄이며, 특정 Feature를 강조할 수 있게 만드는 역할 
이는 Convolution 과정을 거친 레이어의 사이즈를 줄여주는 과정입니다.
단순히 데이터의 사이즈를 줄여주고, 노이즈를 상쇄시키고 미세한 부분에서 일관적인 특징을 제공합니다.

- Max, Average, Min으로 나눠짐 

![image](https://user-images.githubusercontent.com/76649707/150459543-9fff1c37-9c2c-4923-8664-2124d1f13692.png)


* Flatten, Fully Connected Layer(Dense)
Flatten 과정은 convolution과 pooling층의 결과인 feature map을 1차원 벡터로 쫙~펴는 것을말한다. CNN 모델의 특징이 전체가 아닌 부분의 특징을 추출하는 것이라고 했던 것처럼 이미지의 특징들은 이미 잘게잘게 쪼개져 서로 독립적으로 존재하는 상태이기 때문에 1차원 벡터로 연결해도 문제가 되지않는다.
이렇게 flatten과정을 거친 특징들은 fully connected 층에서 모두 연결되어 마치 MLP와 같은 구조를 가지며 최종적으로 Softmax 활성 함수를 통해 이미지가 분류된다.



## CNN은 Convolution과 Pooling을 반복적으로 사용하면서 이미지의 불변적 특징을 찾고, 그 특징을 입력데이터로 Fully-connected 신경망에 보내 Classification을 수행하는 것이다.


https://halfundecided.medium.com/%EB%94%A5%EB%9F%AC%EB%8B%9D-%EB%A8%B8%EC%8B%A0%EB%9F%AC%EB%8B%9D-cnn-convolutional-neural-networks-%EC%89%BD%EA%B2%8C-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0-836869f88375

