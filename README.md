# model-optimization-level3-cv-09
**모델 경량화 프로젝트 CV-09 하나둘셋Net()**
# Member

|[공은찬](https://github.com/Chanchan2) |  [곽민구](https://github.com/deokgu94)|  [김준섭](https://github.com/Aweseop)  | [김진용](https://github.com/Kim-jy0819)|                  [심용철](https://github.com/ShimYC) |   [최현진](https://github.com/hyeonjini) |
| :-------------------------------------------------------------------------------------------------------------: | :-------------------------------------------------------------------------------------------------------------: | :-------------------------------------------------------------------------------------------------------------: | :-------------------------------------------------------------------------------------------------------------: | :-------------------------------------------------------------------------------------------------------------: | :-----------------------------------------------------------------------------------------------: |
|![은찬님](https://user-images.githubusercontent.com/63527907/147105242-1506b2a9-83fb-4500-ae27-40a96786492f.jpg) |![민구님](https://user-images.githubusercontent.com/63527907/147105286-439b141d-4f0d-4702-aa58-5295c4f57549.png) | ![준섭님](https://user-images.githubusercontent.com/63527907/147105312-fd35fa13-fb8d-475c-a504-39711dc345af.jpg)  | ![진용님](https://user-images.githubusercontent.com/63527907/147105333-cfde0fec-7012-43fe-8f74-6298fed9fa42.png)| ![용철님](https://user-images.githubusercontent.com/63527907/147105350-98c2fcac-d13f-47ff-8897-f7167c431d72.jpg)|  ![현진님 (2)](https://user-images.githubusercontent.com/63527907/147105383-8314f309-d926-44e4-9833-1f16e700f4f5.jpg) |
| [**Notion**](https://flint-failing-3c9.notion.site/006b28bf92104405834e3fb3ef1fdc99)                                                                                                             |                                [**TIL**](https://github.com/deokgu/deokgu/wiki)                                 |   [**Git**](https://github.com/Aweseop)                                                                                                              | [**Blog**](https://near-prawn-9c5.notion.site/Naver-Boost-Camp-AI-Tech-2-2e4303f8bd2e4f36be8916d04cbd123a)                                                                                                                | [**Notion**](https://bubbly-cost-eda.notion.site/AI-boostcamp-memo-2f012708dd2645bb9962679ad51c6490)                                                                                                                |[**Devlog**](https://velog.io/@choihj94)                                                                                        |



# Requirements
- Linux version 4.4.0-59-generic
- Python >= 3.8.5
- PyTorch >= 1.7.1
- conda >= 4.9.2
- tensorboard >= 2.4.1
  
# Hardware
- CPU: Intel(R) Xeon(R) Gold 5220 CPU @ 2.20GHz
- GPU: Tesla V100-SXM2-32GB
  
# 목표성능
- f1: 0.7000
- time: 60.000
- score: 1.1950
  
# 프로젝트 계획
- 경량화에 필요한 module 구현 (ex. FireModule - SqueezeNet)
- optuna를 통한 파라미터, 구조 서치
- wandb로 실험관리
- 높은 성능 모델 구조 탐색 후 구조 튜닝
- Augmentation 적용해 모델 Generalization
- Pruning, Knowledge Distillation 적용

# 모델 탐색(Wandb)

![image](https://user-images.githubusercontent.com/51802825/147258183-309d4234-f53d-413e-a8ef-d682fbeeeb44.png) 

![image](https://user-images.githubusercontent.com/51802825/147258223-f09f4206-bfc2-4f7d-81fe-e4cf1c38a2a0.png)

![image](https://user-images.githubusercontent.com/51802825/147258280-51888d21-4e09-424d-a0e4-de92abd17bef.png)

# 최종모델

  backbone:<br>
    [3, 'Conv', [16, 3, 1, null, 1, 'Hardswish']], <br>
    [3, 'DWConv', [48, 5, 2, null, 'ReLU']], <br>
    [3, 'InvertedResidualv2', [64, 7, 2]], <br>
    [3, 'InvertedResidualv2', [128, 3, 1]], <br>
    [2, 'DWConv', [256, 5, 2, null, 'Hardswish']], <br>
    [1, 'Conv', [384, 1, 1]],<br>
    [1, 'GlobalAvgPool', []],<br>
    [1, 'FixedConv', [6, 1, 1, null, 1, null]],<br>
# 결과
- f1: 0.7194
- time: 63.6555
- score: 1.1415