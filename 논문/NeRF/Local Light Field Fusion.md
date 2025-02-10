---
sticker: emoji//1f5d2-fe0f
---
>[!Abstract]
>**<u>정의</u>** : 복잡한 실세계 장면으로부터 새로운 시점을 렌더링하기 위한 딥러닝 솔루션
>
>**<u>기존 접근법</u>** : 샘플링 시점이 밀도있어야 하고, 샘플링 방법에 대한 가이드가 없다.
>
><u>제안 **방법**</u> : 불규칙적인 그리드로 촬영된 시점 이미지를 local light field로 확장하고, MPI 표현을 통해 인접한 local light field를 혼합하여 새로운 시점 이미지를 합성
>
>본 알고리즘을 사용할 때, 얼마나 조밀한 간격으로 촬영해야 하는지를 결정하기 위해 전통적인 plenoptic sampling theory를 확장한다.

## 1. 서론

- 장면을 Light Field로 촬영하고 시점을 보간하여 새로운 시점을 렌더링 할 수 있다. (간단한 방법)
	- Light Field 전략은 IBR(Image-Based Rendering)의 문제로 다룰 수 있고, 이는 샘플링 시점의 밀도와 패턴을 직접 추론 가능
	- 그러나 Nyquist 샘플링 이론에 따라 물체가 카메라에 가까울수록 필요한 이미지의 수가 기하급수적으로 증가
		- 예) 카메라 FoV(64°), 해상도(1M), 물체 거리(0.5m) 일 때 필요한 sampling rate : $1m^2$당 2.5M개의 이미지 필요 --> 실현 불가능
	- 그래서 Light Field 대신 Geometric estimation을 활용하는 방향으로 바뀌고 있음
- **SOTA 알고리즘** : 임의의 sparse grid 시점 이미지들로 새로운 시점을 예측
	- 이 방법은 Plenoptic 프레임워크와 달리, 시점 샘플링 방법와 그에 따른 결과 성능의 예측이 어렵기 때문에, trial and error 방법을 사용하게 된다.
- **제안 방법** : Plenoptic 샘플링 프레임워크에 기반하면서 사용자가 어떤 밀도로 장면을 촬영해야 하는지를 결정할 수 있음
	- 촬영된 시점 이미지를 딥러닝을 사용하여 layered representation으로 표현
	- MultiPlane Image(MPI) 사용
	- 인접한 layered representation에서 새로운 시점을 합성
- Nyquist 제약을 깨는것은 불가능하지만, 자연 이미지로 한정한다면 크게 줄어든 시점 샘플 수로 Nyquist 수준을 달성할 수 있음

>[!Note]- Key Contribution
>1) plenoptic framework를 확장하여 높은 품질의 이미지 합성을 위해 사용자가 이미지를 어떻게 capture 해야하는지 직접 알려준다
>2) 복잡한 실세계를 capture 및 render 한다
>3) local layered scene representation을 활용한 딥러닝. SOTA 달성

