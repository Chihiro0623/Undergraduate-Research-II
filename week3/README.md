# 연구노트 3주차 (9/15 - 9/21)
## RGB Integration
우리는 물체를 인식할 때, 빛의 삼원색에 따라 인지하는 것이 아닌 종합하여 인지하게 된다. 따라서 이미지의 세 Layer(R,G,B)를 모델에 들어오는 순간 Convolution으로 종합하는 방식을 생각해보았는데, 결과는 좋지 않았다.

## Image Enlargement
이미지 사이즈를 크게 할 수록 성능이 좋아진다는 이미 알려진 사실 을 응용해, Linear Layer를 통해 스스로 입력된 이미지보다 크게 만들어 학습한다면 (예를 들어 32x32의 입력이 들어왔을 때, 224x224로 스스로 만들어 학습한다면) 더 성능이 개선될 수 있지 않을까 생각했다. 

이에는 이미지의 사이즈가 커질 뿐만 아니라, 모델 자체가 Class별 원형을 학습하는 효과 또한 있을 것이라 예상했다.

## Data Filtering
이미지에 직접 만든 필터를 씌우고 정해진 Epoch마다 그 필터 부분만을 초기화시켜 스스로 이미지를 증강시키면 좋겠다는 생각을 하게 되었다. 더 나아가 이미지를 처음 모델에 넣은 뒤 나온 예측 결과와 입력을 바탕으로 필터를 만들면 해당 Class의 원형을 더 잘 학습시킬 수 있다는 생각이 들어 적용시켜 보았고, 결과는 아래 그림1,2와 같다. Accuracy 결과는 현재 로그가 소실되어 확인할 수 없지만, Baseline보다 좋은 결과를 기록한 적은 없었다.

그림을 보면 모델이 중요한 부분을 제외한 다른 부분들은 배경으로 처리하여 무시하는 것처럼 보인다. 그러나 모델은 중요한 부분과 배경을 따로 지시 받아 설정하는 것이 아니기 때문에, 그림 3와 같은 경우에는 중요한 부분을 한 번 배경으로 오인하여 제거하기 시작하자 계속해서 중요한 부분을 무시하게 되어 결국 잘 학습하지 못하는 것을 확인하였다. 이것이 현재 CNN 모델 학습법의 근본적인 문제일 수도 있겠다는 생각이 들었다.


![pic1](https://github.com/Chihiro0623/Undergraduate-Research-II/blob/main/week3/pic1.png)
![pic2](https://github.com/Chihiro0623/Undergraduate-Research-II/blob/main/week3/pic2.png)
![pic3](https://github.com/Chihiro0623/Undergraduate-Research-II/blob/main/week3/pic3.png)
