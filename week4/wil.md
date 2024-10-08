**Weekly I learned!**  
=================  
## **1.Loss Function** ##  
* Loss Function은 Weight matrix(가중치 행렬)의 값을 최적화하기 위해 사용됩니다.즉, Weight의 업데이트 방향을 제시해 주는 역할입니다. Loss가 적을 수록 분류의 정확도가 높습니다.  
* Loss Function은 문제의 특성과 데이터의 타입에 따라 사용되는 함수가 다릅니다.  
    * 회귀 문제에서는 주로 MSE(Mean Squared Error)를 사용합니다.  
        * $ MSE = \frac{1}{2} \displaystyle\sum (y - \hat{y})^2 $  
    * 분류 문제에서는 주로 SVM Loss와 Cross-Entropy Loss를 사용합니다.  
        * Multiclass SVM loss  
            * $ L_i = \displaystyle\sum_{j \ne y_i} max(0,s_{y_i}-s_j+1) $  
            safety margin을 두고 정답 클래스 점수와 예측 클래스 점수의 대소 비교하는 것, safety margin을 허용가능한 범위 내에서 가장 크게 만드는것이 목표이다.
        * Cross-Entropy Loss  
            * 네트워크의 출력을 확률로 계산하기 위해 softmax함수를 이용하여 출력을 의미있는 확률 분포로 변환 시키는 것, $ p_i = \frac{e^{z_i}}{\sum_{j=1}^c e^{z_i}} $      
        * Cross-Entropy Loss가 Multiclass SVM loss보다 확률분포의 차이에 민감하게 반응합니다.  
## **2.Regularization** ##  
* Regularization은 Overfitting 과 Underfitting을 방지하기 위해 Loss 함수에 parameter에 대한 term을 추가하여 가중치 W가 작아지도록 학습시키는 것입니다.  
    * L2 Regularization  
        * $ Cost = \frac{1}{n} \displaystyle\sum_{i=1}^n \{L(y - \hat{y})^2 + \frac{\lambda}{2}|w|^2 \} $  
        * 매끄러운 그래프를 원할 때 사용하는 정규화로 큰 가중치에는 더 큰 패널티를, 극단적인 가중치를 피하면서 모든 특성이 균등하게 
    * L1 Regularization  
        * $ Cost = \frac{1}{n} \displaystyle\sum_{i=1}^n \{L(y - \hat{y})^2 + \frac{\lambda}{2}|w| \} $  
        * 가중치의 크기에 상관없이 일정한 상수값을 더하거나 빼주는 방식, 특정 가중치를 0으로 만들어 모델의 복잡도를 낮추고 feature selection의 역할을 할 수 있습니다.  
## **3.Optimization** ##  
* 모델의 오차를 최소화하거나 정확도를 최대화하기 위해 파라미터를 조정하는 것  
* 최적화 알고리즘은 크게 Gradient 조절하는 알고리즘과 Learning rate를 조절하는 알고리즘으로 분류됩니다.  
    * 경사하강법: 손실함수의 기울기에 따라 최소지점을 찾을 때까지 반복하는 방법  
    * 모멘텀 최적화(Gradient 조절): 경사하강법에서 관성을 도입하여 이전 업데이트를 기반으로 파라미터를 업데이트  
    * AdaGrad(Learning rate 조절): 각 매개변수에 서로 다른 학습률을 적용시키는 방법, 처음에는 크게 나중엔 작게  
    * Adam:RMSprop Algorithm(아다그리드에서 지수 이동 평균을 활용)과 모멘텀 최적화를 결합