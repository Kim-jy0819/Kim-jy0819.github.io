---
layout: single
title:  "AI부스트 캠프 7주차 학습정리"
categories: ['AI', 'Review']
---


# 1. 강의 복습 내용
### P stage 이미지 분류
1. Image Sementation
2. Object Detection
3. GAN
4. Multi Modal
5. 3D Dataset



# 2. 과제 수행 과정/ 결과물 정리
- 필수 과제 4번과 선택 과제 1번, 2번을 풀어보면서 간단하게 segmentation, gan, hour glass에 대해서 공부해볼 수 있었습니다. segmentation은 이미지 분류 모델인 vgg모델의 fcn 구조만 사용하고 마지막 fc layer를 1 x 1 convolution layer로 사용하고 input size에 맞게 upsampling을 진행하여 픽셀별 클래스 분류를 할 수 있도록 만들어주었습니다. gan은 처음 사용을 해보았고, 빈칸은 채웠지만 정확한 코드 이해는 하지 못했습니다. discriminator와 generator가 서로 학습하는데 영향을 주어 더 잘 이해하는 메커니즘으로 이해하고 있고, 보통은 discriminator가 학습하기 더 쉽기 때문에 scheduler를 사용하여 조절을 한다고 합니다. hour glass는 down sample과 upsample을 반복하는 unet 구조가 반복되어 있는 모레시계 모양을 되어 있는 모델이라고 배웠습니다. 여러 과제를 풀어보며 다양한 모델을 직접 접해보았고, 다양한 task에 응용해볼 수 있을 것으로 기대합니다.



# 3. 피어세션 정리
- 리뷰어가 그날 배운 내용을 정리해주고, 질의 응답과 토론을 했습니다. 팀원 중 한 분이 많이 알고 계셔서 도움을 많이 받았습니다. github를 활용하여 과제를 서로 리뷰해주는 방식으로도 진행해보았고, 알고리즘 스터디도 깃허브를 사용하기로 결정했습니다. 

# 4. 학습 회고 
- 추석 주가 있는데 이 기간 동안 object detection에 대해서 공부를 좀 해봐야 할 것 같습니다. segmentation에 대한 과제는 있었지만, object detection은 없었기에 다음 대회부터 바로 시작할 수 있도록 데이콘이나, 케글에 있는 대회를 참고하여 베이스라인을 미리 짜보면 좋을 것 같습니다. 또, 논문 작성과 같은 것들을 해보며, 가설 설정, 실험, 논리적인 분석 등 체계적으로 실험해 볼 수 있도록 틀을 잡아보는 것도 좋을 것 같습니다. 