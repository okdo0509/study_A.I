**Weekly I learned!**  
=================  
## **1.Backpropagation(역전파)** ##  
* backpropagation(역전파)란?  
    * Artificial Neural Network를 학습시키기 위한 일반적인 알고리즘 중 하나이다.  
    * 입력층부터 출력층까지 순서대로 변수들을 계산하고 저장하는 것을 역순으로 진행하여 파라미터의 영향력을 측정하는 것이다.  
* Chain Rule(연쇄 법칙)  
    * $ F=f(g(x))=f∘g $ 라고 하면 $F'(x)=f'(g(x))⋅g'(x)$ 이다. $t = g(x)$라고 하면 $\frac{dy}{dx} =  \frac{dt}{dx}\frac{dy}{dt}$ 이 성립한다.  
    * 이 방식을 이용하면 갱신을 위하여 미분을 수 없이 많이 해야하는 것을 편미분값을 구해서 '한번의 곱셈'으로 아주 간단하게 구할 수 있습니다.  
* 각각의 노드 마다의 역전파  
    * 덧셈 노드의 경우: $z = x+y$라고 하자 $\frac{\partial{z}}{\partial{x}} = 1 $ 이고 $\frac{\partial{z}}{\partial{y}} = 1 $ 이므로 상류에서 보내진 미분 값을 그대로 하류에 흘려 보냅니다.  
    * 곱셈 노드의 경우: $z=x\times y$라고 하면 $ \frac{\partial{z}}{\partial{y}} = x$ 이고 $\frac{\partial{z}}{\partial{x}} = y$ 이므로 상류에서 보내진 미분 값에 입력값을 서로 교체하여 곱하여 하류에 흘려 보냅니다.  
    * Relu 계층: $\frac{\partial{y}}{\partial{x}}= \begin{cases} 1,\;if\;x>0\\ 0,\;if\;x\leq0 \end{cases}$ 이므로 0보다 크면 그대로 보내고 0보다 작으면 0을 보냅니다.  
    * Sigmoid 계층: $\frac{\partial{L}}{\partial{y}}y(1-y)$ 로 정리하여 나타낼 수 있습니다.  
    * Softmax 계층: 손실함수가 '교차 엔트로피 오차'인 경우 역전파의 결과가 $(y_{1}-t_{1},y_{2}-t_{2},y_{3}-t_{3}, \cdots )$ 이렇게 나타난다.($y_{i}$ 는 Softmax 계층의 출력값 $t_{i} $ 는 정답 레이블)
