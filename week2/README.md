# 연구노트 2주차 (9/8 - 9/14)
## Dataset Order
저번주의 결과에서 Baseline의 정확도가 76.75로 너무 낮기 때문에 좀 더 좋은 Hyperparameter를 Baseline으로 교체해보라는 대학원생 멘토의 조언을 듣고, Batch 100에서 79.21의 정확도를 내는 모델을 Baseline으로 재설정하였다. 그런데 코드를 새로 만들던 중, 이전의 결과는 학습 데이터를 두 배로 학습하였기 때문에 좋은 결과를 내고 있었다는 점이 발견되었고, 그 점을 수정한 결과 성능은 Baseline보다 떨어지게 되었다.  

Accuracy는 떨어지지만 Train Loss는 더 낮은 점에 착안하여, ‘제안하는 방법론이 학습은 더 잘 되지만 Robustness가 부족하여 새로운 Test Data에 대해 예측을 잘 하지 못하는 것이 아닐까?’라는 생각을 하게 되었고, 이를 해소하기 위해 매 N Epoch마다 Shuffle된 Dataset과 모든 Class가 한 번씩 나오게 되는 Dataset을 번갈아가면서 학습시켜 보았으나 성공하지 못했다.
[WandB Report](https://api.wandb.ai/links/oso0310/g9hmwhgo)

이어서 시작은 정렬된 Dataset으로 학습하지만, N번째 Epoch부터 Shuffle된 Dataset으로 학습하는 것을 시도했지만 성공하지 못했다. Optimizer를 AdamW로 바꿔보기도 했지만 큰 성과는 없었다.
[WandB Report](https://api.wandb.ai/links/oso0310/4wgpq95b)

계속해서 방안을 모색하던 중, Batch Size 100을 기준으로 매 Batch마다 Shuffle시 100개 중 보통 65-70개 종류의 Class들이 포함된다는 것에 착안하여, 인위적으로 Batch마다 등장하는 Class의 개수를 N개로 제한하여 보았지만 실패하였다.
[WandB Report](https://api.wandb.ai/links/oso0310/uztqgvbc)
