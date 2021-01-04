# GAN; Generative Adversarial Network

Created: Jan 4, 2021 10:17 PM
Tags: ML, PR12, Tech

### Generative model

생성 모델. "what I cannot create, I cannot understand" → 생성할 수 있다면 이해/분류 가능 하다는 생각.

### GAN

- discriminator - 생성한 이미지와 원래 이미지 분류
- generator - letent vector z에서 이미지 생성

![GAN;%20Generative%20Adversarial%20Network%20458bf2d288df4a56a3ff395e1ddb3271/SmartSelect_20210104-231638_Samsung_Notes.jpg](GAN;%20Generative%20Adversarial%20Network%20458bf2d288df4a56a3ff395e1ddb3271/SmartSelect_20210104-231638_Samsung_Notes.jpg)

논문에서는 

1. 해당 Loss가  Pg(생성한 샘플) = Pdata(데이터셋) 일때 global optimum을 가짐
2. 해당 global optimum을 찾을 수 있음

을 보였다.

### Results

- 이미지 생성
- word2vec과 같이 letent vector 연산 가능 → 안경쓴 남자 - 남자 + 여자 ⇒ 안경쓴 여자
- super resolution
- Z를 interpolate 하면 자연스럽게 바뀌는 것 확인 가능.
- Img2Img translation (pix2pix)
- InfoGAN, Conditional GAN

### Gan 훈련시 문제점

Discriminator, Generator loss가 출렁이면서 Gradient descent 특정한 궤도를 타게 됨 → 제대로 훈련이 안됨

→ Minibatch Discrimination, Inception Score 도입

- mode collapse: 한 개의 생성 샘플로 수렴해서 빠져나오지 못하는 문제