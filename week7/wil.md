**Weekly I learned!**  
=================  
## **1.Object Detection(객체 탐지)** ##  
* 객체 탐지란, 이미지의 객체들의 위치를 탐지하고 클래스를 분류하는 기술을 의미합니다.  
* 이미지의 범위를 확장시켜 객체같은 것을 박스로 잘라와 클래스를 분류하는 방식입니다.  
* two stage 방식으로는 R-CNN, Fast R-CNN, RPN, Faster R-CNN 등이 있고, one stage 방식으로는 YOLO 시리즈가 있습니다.  
## **2. Two stage Detector** ##  
* 개념적으로는 객체의 위치를 찾는 stage와 객체의 클래스를 분류하는 stage로 나뉘어 있습니다.  
* 객체의 위치를 찾는 stage  
    * NMS: 출력가능한 모든 박스들을 구한 후 점수별로 나열한 후 IoU를 비교하여 적절한 값을 가진 박스들만 출력하는 것입니다.  
    * IoU: 박스의 교집합/박스의 합집합  
* R-CNN: 물체의 영역을 찾고(Region Proposal) -> 고정된 크기의 Feature Vector를 warping하여 CNN에 입력합니다. -> feature map을 활용하여 SVM(Bounding Box Regression, classify)을 통해 분류하여 결과값을 제공합니다.  
* fast R-CNN: 이미지를 CNN에 적용시키고 RoI Projection를 통해 feature map에서 각 region proposals에 해당하는 영역을 추출합니다.  
    * ROI Pooling: Proposal 단계에서 나온 여러 사이즈들의 RoI들을 FC layer에 넣기 위해 사이즈를 통일시켜주는 것입니다. RoI를 원하는 사이즈에 맞게 나눈 후 각 grid에 pooling을 적용시키는 것입니다.  
    * Selective Search: segmentation을 실시하여 seed를 설정하고 이들을 적절하게 통합한다. 그러면 고정된 window를 사용하는 것보다 더 다양한 크기와 비율의 window를 만들어 더욱 정확하게 포착할 수 있다.  
* RPN: 일련의 anchor box를 각 위치에 적용시켜가며 물체가 있을 가능성을 측정하고 NMS를 통해 가장 가능성이 있는 영역만 남기는 방식입니다.  
* Faster R-CNN: fast R-CNN에서 Selective Search 대신 RPN를 사용하는 방식입니다.  
## **3. One stage Detector** ##  
* classification과 localization문제를 동시에 해결하는 방법입니다.  
* YOLO시리즈: 입력된 이미지를 가로 세로 동일한 크기의 gird로 나눈 후 classification와 바운딩박스와 박스에 대한 신뢰도 점수를 예측하는 것을 동시에 실행 합니다. 그 후 NMS알고리즘을 이용하여 최종 경계 박스들을 선정합니다. 1차원 텐서에는 5+5+클래스의 수가 들어갑니다.  
* 이 Detector은 빠르고 단순하지만 정확도가 떨어지는 문제를 가지고 있습니다.  
## **4. Feature Pyramid Network(FPN)** ##  
* Bottom-up pathway: CNN을 적용하여 2배씩 작아지는 feature map을 추출하는 과정입니다.  
* Top-down pathway: pyramid level에 있는 feature map을 2배로 upsampling하고 channel 수를 동일하게 맞춰주는 과정입니다.
*  Lateral connections: 바로 아래 level의 feature map과 element-wise addition 연산을 하는 과정입니다.