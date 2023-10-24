# 연구노트 1주차 (9/1 - 9/7)
## Dataset Order
제일 처음 떠올린 개선 방안은 Dataset의 순서를 정해주는 것이었다. 현재 대부분의 Data Loader에서는 Data를 Random하게 Shuffle된 순서로 제시한다. 그런데 개인적으로 진행한 Continual Learning과 관련된 실험 에서는 하나의 Class만을 담은 Batch를 학습시키면 모델은 금방 그 Class만을 예측하도록 변경된다.
그렇다면 Shuffle되었을 때 해당 Batch에 포함되지 않은 Class에 대해서 순간적으로 Forgetting이 일어날 수도 있겠다는 생각이 들었다. 또한 매 학습마다 Shuffle을 시킨다면 학습마다 결과에 조금씩 차이가 있을 것이고, 그렇다면 최고의 결과가 나왔을 때 학습 순서를 파악하고 분석하면 학습에 도움이 되지 않을까 생각했다.

### 실험 과정
실험을 위해 Batch Size는 Class 수의 배수 (Cifar-100에서는 100의 배수)로 설정하였고, 매 Batch별로 모든 Class가 한 번씩 나오도록 구현하였다. 다른 Hyperparameter들은 모두 똑같이 유지하였다.


### 실험 결과
ResNet18, Batch Size 100에서 좋은 결과가 나왔다. 이에 좀 더 큰 모델인 ResNet50에서도 잘 작동하는지 확인해보기 위해 추가적인 실험을 진행하였다. 이미지 사이즈를 224와 32 사이에서 바꿔보고, Batch Normalization에 다양한 Sample들이 골고루 들어갈 수 있도록 epoch마다 Class별 등장 순서를 Shuffle하기도 하였다. 그 결과, Image Size가 32일 때에는 성능이 저하되었으나, 224일 때에는 약 1.7%p의 성능 향상을 볼 수 있었다.
[WandB Report](https://api.wandb.ai/links/oso0310/u6s45ncx)
