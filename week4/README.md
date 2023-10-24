# 연구노트 4주차 (9/22 - 9/28)
## Learnable Class Attention
Task가 지나 새로운 학습 데이터들이 들어오더라도 기존의 데이터들에 대해서는 중요하게 여기는 부분들이 계속해서 유지된다면 Continual Learning의 문제인 Catastrophic Forgetting을 방지할 수 있을 것이라고 생각했다. Class Attention을 시각화한 결과는 그림과 같고, Task가 지날수록 중요하게 보는 부분이 옅어진다는 것을 알 수 있다.

### 실험 과정
Attention 값에 2를 곱하는 방식으로 값에 할당되는 가중치를 두 배로 향상시켜 보았다.

### 실험 결과
Average 기준 10 Steps에서는 1.5%p라는 큰 성능 향상이 있었으며, 50 Steps에서도 소소한 성능 향상을 보였다. 그러나 20 Steps에서는 큰 성능 향상을 보이지 않았기 때문에 20 Steps의 성능을 향상시키기 위한 개선법에 대해 생각하던 중, 단순히 2를 곱하는 것이 아닌 Learnable Parameter를 곱하는 Learnable Class Attention 방식을 생각해보았다. 그러나 이 방식 또한 성능의 개선을 보이지 않았고, 오히려 10 Steps의 성능도 저하시켰다.
[WandB Report](https://api.wandb.ai/links/oso0310/s9lp7w0x)


![table](https://github.com/Chihiro0623/Undergraduate-Research-II/blob/main/week4/table.png)

## New Teacher
DyTox에서 Knowledge Distillation을 위해 사용하는 Teacher Model이 이전 Task까지의 학습이 완료된 Model이었다. 그러나 각 Task에서 사용하는 학습 데이터에서 이전 Task까지의 데이터가 차지하는 비중은 몹시 작기 때문에 Teacher Model은 대부분이 자신도 잘 모르는 새로운 데이터에 대해 Teacher 역할을 수행하고 있었다는 모순적인 상황을 확인할 수 있었다. 그러나 Knowledge Distillation을 아예 사용하지 않는 것보다는 훨씬 좋은 성능을 보여주었지만, 이 부분을 더욱 개선시킬 수 있을 것이라는 생각이 들었다.

각 Task만을 학습하는 경우 대개 80대 후반에서 90대 초반 정도의 높은 정확도를 보여준다. 이를 활용해 새로운 Task만 학습한 전문적인 Teacher 모델을 만들어 새롭게 들어오는 데이터에는 
새로운 Teacher가, 옛날 데이터에는 옛날 Teacher가 각각 Knowledge Distillation을 수행하는 방식을 구현해보았으나 성능이 좋지 않았다. 추가적으로 각 Task만을 학습한 모델들을 만들어 각 Weight들을 더한 후 학습을 시작해보았으나 좋은 결과가 나오지 않았다.
[WandB Report](https://api.wandb.ai/links/oso0310/kgtzsczr)
