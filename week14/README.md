# 연구노트 14주차 (12/1 - 12/7)
## 활동 내용
모든 모델에서 적용될 수 있는 모델의 발견에 실패하였고, 방법론 자체도 전체적으로 학습이 잘 되게 만드는 것이 아니라 일부 Class의 성능은 오르고 일부는 내리는데 오른 폭이 더 높을 경우에 결과가 좋게 보이는 눈속임일 수도 있다는 가능성을 생각하게 되었다.

## 실험 내용
가장 처음의 관측(항상 잘 맞추는 Class와 그렇지 않은 Class가 있다)으로 돌아가서 메모리 구성을 효율적으로 개선하는 방식의 새로운 방법론을 설계하고 있다.
쉬운 Class와 어려운 Class를 나누기 위해 Validation Statistics를 참고하고자 한다.

## 실험 결과
Validation Set 5%를 뺀 95%로 학습시켜 보았는데, 중반 이후로 성능이 오히려 증가하는 이상한 상황을 발견하였다.

[WandB Report](https://api.wandb.ai/links/oso0310/z3f3rjd8
![chart](https://github.com/Chihiro0623/Undergraduate-Research-II/blob/main/week14/chart.png)  