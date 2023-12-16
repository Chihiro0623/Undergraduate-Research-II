# 연구노트 12주차 (11/17 - 11/23)
## 활동 내용
해당 방법론이 잘 작동하는지 확인하기 위해 다른 모델들의 Repository를 Clone하여 결과를 Reproduce하는 작업을 진행하였다. 실험의 대상으로 삼은 모델들은 WA, iCaRL, DER, MEMO, BiC, FOSTER이 있다. 해당 논문의 재현 결과를 보고 높은 성능을 보이거나 중요하게 여겨지는 Baseline 모델들을 기준으로 선정하였다. https://arxiv.org/abs/2302.03648

## 실험 내용
각 모델별로 Cifar-100 Dataset의 Base0 Inc5, Base0 Inc10, Base0 Inc20, Base50 Inc10의 4번씩 실험을 진행하였다.

## 실험 결과
성능이 낮게 나오는 모델들이 있었지만 대부분은 똑같이 재현되었다.  

[WandB Report](https://api.wandb.ai/links/oso0310/u2l9fobh)  
![table](https://github.com/Chihiro0623/Undergraduate-Research-II/blob/main/week12/table.png)  