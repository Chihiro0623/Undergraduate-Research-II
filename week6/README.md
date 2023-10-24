# 연구노트 6주차 (10/6 - 10/12)
## Intentional Forgetting
이전 실험에서 10개의 Class만을 학습시키더라도 90%의 정확도를 넘지 못하는 몇 Task를 확인할 수 있었다. 그래서 DyTox를 학습시키는 동안 Class별 결과를 확인해보니, 어떤 Class는 자신이 처음 도입된 Task에서 얼마 지나지 않았는데도 나쁜 결과를 내는 경우도 있고 어떤 Class는 자신이 처음 도입된 Task에서 많이 지났음에도 높은 결과를 내는 경우도 있었다. 


### 실험 과정
에빙하우스의 망각곡선에 따르면 ‘7번 잊고 난 후 외우는 것은 긴 시간동안 잊지 않는다는 것’이 떠올랐다. 실험으로 이를 구현해보기 위해 현재 Task의 데이터만을 포함한 데이터셋 A와 이전 Task들의 데이터도 함께 포함한 데이터셋 B를 번갈아가면서 학습시켜 보았다.

### 실험 결과
A로 학습시키는 경우 이전 Task의 Class들은 잊혀지게 되어 정확도는 떨어지지만, 그 후 B로 학습시키는 경우 A로 향상된 성능이 거의 유지되면서 이전 Task의 Class들의 성능이 오르게 되어 결국 전체적인 성능도 오르는 것을 확인할 수 있었다. 10 Steps과 20 Steps에서는 좋은 개선을 보였는데, 이는 해당 방법론이 추가적인 메모리와 시간을 요구하지 않는다는 점을 고려하면 꽤나 큰 개선으로 보인다.

[WandB Report](https://api.wandb.ai/links/oso0310/bly07y98)  
![table](https://github.com/Chihiro0623/Undergraduate-Research-II/blob/main/week6/table.png)

그러나 50 Steps에서는 딱히 좋은 성능을 보여주지 않고 있기 때문에, 50 Steps에서도 성능을 개선시킬 수 있도록 Epoch 주기를 Tuning하는 등의 방식을 통해 Forgetting 방법론을 개선시켜야 할 것 같다.
