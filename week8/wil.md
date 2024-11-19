**Weekly I learned!**  
=================  
## **1.Attention** ##  
* attention이란  Key와 Query간의 유사도를 구해서, 유사도에 따라 Value를 averaging(weighted sum)하고, 이렇게 averaging된 value를 반환하는 것이고 미분 가능한 key-value function입니다.  
    * Query : 현재 timestep의 decoder output  
    Keys : 각 timestep별 encoder output  
    Values : 각 timestep별 encoder output
* 나오게 된 배경은 seq2seq에서 문장이 길어질수록 정확도가 낮아지는 현상은 해결하고자 제시되었습니다.  
* Scaled Dot-Product Attention: 각 timestpe별 Query벡터와 Keys벡터들 간의 유사도를 구하고 각 timestpe의 values에 곱해서 더하면 context vector가 생성됩니다.이후 Query와 context vector를 concat(이어 붙이는 것)한다. 그리고 이 벡터를 적절한 출력 벡터로 변환한 후 softmax함수에 적용시켜 출력 확률 분포를 얻습니다.  
* Multi-Head Attention: 여러개의 독립적인 어텐션을 병렬로 수행한 후, 결과를 합산하는 방식입니다. Q,K,V를 선형화 한 후 선형화 된 벡터들에 대하여 Scaled Dot-Product Attention를 수행하는 것을 여러번 병렬적으로 수행한다. 그리고 그 결과들을 concat해서 선형화 시키는 것입니다.  
## **2.ViT(Vision Transformer)** ##  
* Transformer를 Vision Task에 적용시킨 것입니다. 이미지를 여러 패치로 나누어 패치 자체를 단어처럼 보이게 하여 분류합니다.  
* Positional Encoding: 위치 정보를 주입해주는 것입니다. Positional Encoding vector의 dimension인 i값이 짝수면 sin, 홀수면 cos을 적용시킵니다. $ PE_{(pos,2i)} = sin(4/10000^{2i/d_{model}}) , PE_{(pos,2i+1)} = cos(4/10000^{2i/d_{model}}) $  
* CNN과 ViT의 차이점으로는 CNN은 이미지의 Inductive Bias를 효과적으로 활용하지만 Vit는 Inductive Bias를 효과적으로 활용하지 못합니다.  
* ViT는 데이터의 크기가 커지면 커질수록 성능향상이 급격하게 일어납니다.
