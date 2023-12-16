# 연구노트 11주차 (11/10 - 11/16)
## 활동 내용
DyTox에서 잘 되던 방법론을 BEEF와 TCIL에 적용시켜 Baseline 결과와 비교 작업을 진행하였다.

## 실험 내용
방법론이 잘 통하지 않아 방법론에 여러가지 변화를 주어서 실험하였다.

## 실험 결과
일정 Epoch마다 Forgetting 하는 것이 아니라 학습이 끝나기 전 마지막 40 Epoch 시점에서만 Forgetting을 20 Epoch정도 진행하는 방식으로 TCIL의 성능을 개선시킬 수 있었다.  

[WandB Report](https://api.wandb.ai/links/oso0310/r701zxup)  
![table](https://github.com/Chihiro0623/Undergraduate-Research-II/blob/main/week11/TCIL130150.png)
