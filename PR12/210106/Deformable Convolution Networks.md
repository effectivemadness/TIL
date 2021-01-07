# Deformable Convolution Networks

Created: Jan 6, 2021 11:07 PM

### Introduction

Convolution 이나 RoI pooling 에 Learnable offset을 적용.

고정된 크기의 convolution filter를 사용해야만 하는 이유가 없음.

![Deformable%20Convolution%20Networks%20a94f8053d46f45daa4cae2ab8eb36860/SmartSelect_20210106-231211.jpg](Deformable%20Convolution%20Networks%20a94f8053d46f45daa4cae2ab8eb36860/SmartSelect_20210106-231211.jpg)

convolution 커널의 정보를 받아오는 위치를 학습하여 다양한 offset을 가지게 됨

Spatial Transformer Network → Input이 어떻게 변형된건지 알아내 변형 이루어지기 전으로 다시 변형.

![Deformable%20Convolution%20Networks%20a94f8053d46f45daa4cae2ab8eb36860/SmartSelect_20210106-231808.jpg](Deformable%20Convolution%20Networks%20a94f8053d46f45daa4cae2ab8eb36860/SmartSelect_20210106-231808.jpg)

### Deformable Convnet

![Deformable%20Convolution%20Networks%20a94f8053d46f45daa4cae2ab8eb36860/SmartSelect_20210106-231918.jpg](Deformable%20Convolution%20Networks%20a94f8053d46f45daa4cae2ab8eb36860/SmartSelect_20210106-231918.jpg)

커널의 offset, RoI Pooling의 offset을 따로 학습해 값을 산출.

![Deformable%20Convolution%20Networks%20a94f8053d46f45daa4cae2ab8eb36860/SmartSelect_20210106-232128.jpg](Deformable%20Convolution%20Networks%20a94f8053d46f45daa4cae2ab8eb36860/SmartSelect_20210106-232128.jpg)

그냥 Convolution보다 Receptible field가 더 넓어지는 효과가 있다.

![Deformable%20Convolution%20Networks%20a94f8053d46f45daa4cae2ab8eb36860/SmartSelect_20210106-232103.jpg](Deformable%20Convolution%20Networks%20a94f8053d46f45daa4cae2ab8eb36860/SmartSelect_20210106-232103.jpg)

어떤 object를 인식하느냐에 따라 offset의 변화를 보면 object의 특성에 따라 offset 학습 차이를 확인 가능

### in Context of Related Works

- Spatial Transform Networks
    - 변형된 object 찾고, 그 찾은 것을 다시 원래로 interpolate 해야하는데 이 때 cost가 높음
- Effective Receptive Field
    - 3by3 → 9by9 → 27by27 같이 linear 하게 커지는게 아니라 root에 비례해서 커짐
    - 중간에 겹치는 애들때문에