**Weekly I learned!**  
=================  
## **1.CNN** ##  
* FNN을 사용할 때 인접 픽셀간의 상관관계를 무시하는 현상을 해결하기 위해 사용됩니다. 여러 개의 필터를 적용시켜 다양한 feature map을 얻고 feature map에 FNN을 적용시켜 결과 값을 구하는 구조 입니다.  
## **2.Activation Function** ##  
* CNN에서 아무리 많은 층을 쌓더라도 결국 하나의 선형변환으로 축소 됩니다. 이러한 함수에 비선형성을 부여하기 위해 Activation Function을 추가 합니다. 대표적인 예시로 ReLU와 sigmoid함수가 있습니다.  
## **3.Normalization(정규화)** ##  
1. 정규화란? 여러 Feature 데이터 값의 범위를 사용자가 원하는 범위로 제한하는 것입니다. 일반적인 정규화는 모든 feature를 0~1사이로 조정하는 것 입니다. 정규화를 거치면 학습 속도를 향상 시킬 수 있습니다.  
2. Batch Normalization(배치 정규화)  
    * Batch Normalization란? 학습 과정에서 각 배치 단위 별 다양한 분포를 가진 데이터를 각 배치별로 평균과 분산을 이용해 정규화하는 것입니다.  
    * Batch Normalization을 사용하면 Internal Covariate Shift(학습 과정에서 계층 별로 입력의 데이터 분포가 달라지는 현상)을 해결 할 수 있습니다.  
    * $BN(X) = γ\frac{X-μbatch}{σbatch} $. (X:입력데이터, γ : 추가 스케일링, β : 편향, μbatch : 배치 별 평균값, σbatch : 배치별 표준 편차)
## **4.Transfer Learning(전이학습)** ##  
* Transfer Learning(전이학습)이란? 한 분야의 문제를 해결하기 위해서 얻은 지식과 정보를 다른 문제를 푸는데 사용하는 방식을 말합니다. 데이터가 매우 부족한 경우 이미 학습된 모델에 마지막 층만 새로운 데스크에 맞춰 수정하여 모델을 생성할 수 있고 데이터가 어느 정도 있는 경우엔 learing rate를 다르게 적용시키고 마지막 층을 새로운 데스크에 맞춰 수정하여 모델을 생성할 수 있습니다.  
## **5.Knowledge Distillation** ##  
* Knowledge Distillation은 미리 잘 학습된 teacher network의 지식을 student network에 전달하는 것입니다. soft label을 사용하여 정보의 손실없이 teacher network를 모방합니다. 이 방식을 이용하여 상대적으로 적은  Parameter로 모델의 성능을 높이는 방법론입니다.