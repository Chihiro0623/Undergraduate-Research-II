# 연구노트 5주차 (9/29 - 10/5)
## Top-5 활용
Top-5 정확도는 항상 90% 이상의 높은 성능을 보인다. 따라서 이를 활용하여 Top-1의 성능을 높일 수 있지 않을까 생각했다. Top-5 정확도가 90%라는 것은 5개 안에 정답이 있을 확률이 90%라는 뜻이기 때문이다.

### 실험 과정
모델이 Top-5만을 정교하게 보게 하기 위해서 Loss Function에 들어가기 전 예측 값에서 상위 5개를 제외한 모든 값들을 전부 최하위 값으로 만들어 보았다.

[WandB Report](https://api.wandb.ai/links/oso0310/848pli0j)

## 부분 고정 학습
DyTox의 Finetuning 과정에서는 이미지를 Token으로 변환하는 부분인 Self-Attention Blocks (SAB)만을 Freeze시킨 뒤 Token으로 Class를 예측하는 부분인 Task-Attention Blocks (TAB)와 Classifier Head만을 학습시키고 있다. Finetuning에 사용되는 데이터는 지금까지 있었던 모든 Task의 데이터들 중 각 Class의 평균에 가까운 1000장을 Class별로 균등한 수로 뽑아 사용하고 있다.

### 실험 과정
Finetuning 과정을 응용하여 Finetuning이 아닌 본래 학습 때 SAB, TAB, Head를 일정 Epoch마다 Freeze시켜 학습시킨다면 각 모듈이 각자에 맞게 잘 학습할 것이라고 생각했다.

[WandB Report](https://api.wandb.ai/links/oso0310/k0zog2nn)
