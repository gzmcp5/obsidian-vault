
1. [[SimpleCNN (MNIST)]]
2. [[SqueezeNet (CIFAR10)]]
4. [[얼굴 인식]]
5. OpenFHE

- 오픈소스 라이브러리에서 GPU 연산을 지원하지 않는 이유
modular exponential, polynomial multiplication, DFT 등의 연산은 병렬처리가 쉽지 않음

- maxpool, avgpool 레이어 지원 여부
Convolution & AveragePool 레이어는 Vector-Matrix Multiplication 연산을 사용하여 구현 가능

- cuFHE(NVIDIA) : TFHE 스킴 지원
- nGraph-HE(Intel) : 딥러닝 연산 지원
