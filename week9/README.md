# 연구노트 9주차 (10/27 - 11/2)
## 활동 내용
DyTox 외의 다른 모델들, 특히 현재 SOTA 모델들인 BEEF와 TCIL에서도 방법론이 잘 통하는지 확인해 보았다.

## 실험 내용
각 모델별로 Cifar-100 Dataset의 Base0 (Inc5, Inc10, Inc20), Base50 (Inc5, Inc10, Inc20)의 6번씩 실험을 진행하였다.

## 실험 결과
TCIL은 비교적 잘 재현되었으나 BEEF의 성능이 낮게 나오는 경우들이 있었다.  

[WandB Report](https://api.wandb.ai/links/oso0310/ubcqtrfx)  
![table](https://github.com/Chihiro0623/Undergraduate-Research-II/blob/main/week9/TCIL.png)  

[WandB Report](https://api.wandb.ai/links/oso0310/vcizvxwt)  
![table](https://github.com/Chihiro0623/Undergraduate-Research-II/blob/main/week9/BEEF.png)  