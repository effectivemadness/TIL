# GANs In Action 책

Created: Jan 8, 2021 12:50 AM
Tags: Book, GAN, ML

Ch.6 이후 각 모델별 신기한것들

- ProGAN
    - 저해상도 Conv 층에서 출발해서 여러개의 고해상도 층으로 이동하며 훈련.
    - 저해상도일때 parameter 공간이 탐색하기에 쉬움(Local minimum에 빠지는것 피하기 가능)
    - 16x16으로 훈련 → 32x32 붙이고 a만큼 섞음 → 32x32에 확신이 생기면 16x16 - 32x32 이어진 모델 학습
    - 미니배치 표준편차 : Mode Collapse 해결하기 위해 추가. 샘플이 충분히 다양한지 알려줌. 다양성이 낮으면 가짜일 가능성 높음.
- SGAN(Semi-supervised generative adversarial network)
    - 판별자가 진짜/가짜 구분 뿐만 아니라 각 클래스를 구별하도록 학습.
    - 판별자는 두개의 출력 가짐. 진짜 클래스에 대한 예측(지도 학습 판별자), 진짜/가짜 확률(비지도 학습 판별자)
    - 적은 데이터셋으로도 높은 성능의 판별자 학습 가능.
- CGAN(Conditional GAN)
    - 생성자가 Class와 잡음 z를 입력으로 하여, 해당 클래스에 맞는 가짜 이미지 생성
    - 판별자는 Class와 샘플(해당 class의 이미지 or 생성자가 생성한 이미지)을 받아 해당 이미지가 class에 맞는지 판별.
    - (구현 측면) 이미지랑 클래스를 판별자끼리 주고 받거나, 클래스와 잡음을 입력으로 줘야 하는데, 이 때 class를 임베딩 층을 통과한 결과값을 사용하여 잡음과 붙여 조인트 표현을 사용하는 방법.
- CycleGAN
    - 사이클-일관성 손실(Cycle-consistency loss) : 사과에서 오렌지로, 이걸 다시 사과로 바꾸는 과정 학습. 갔다 왔을때 픽셀 단위 비교
    - 적대 손실 : A→B 생성, B→A 생성 모두 판별자가 확인
    - 동일성 손실 : 전반적인 색 구성, 색 온도 유지하기 위해 추가.
- 적대 샘플(Adversarial Example)
    - 분류기의 Grad가 상승되도록 픽셀을 업데이트.
    - ex. FSGM(fast sign gradient method) ; grad를 업데이트 후 부호 확인 후 반대방향으로 조금 이동
    - 가우시안 노이즈 생성 → PGD(projected gradient descent) 사용하면 비슷한 노이즈를 다양한 클래스로 분류 가능하게 공격 가능.