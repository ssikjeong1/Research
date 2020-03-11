# Research
## Meta Learning
*Learning하는 방법을 Learning* 하는 개념으로,
**새로운 데이터에 대한 빠른 adaptation, generalization 등을 목표**로 합니다.

1. Main network (task: classification)에 sub-network를 붙임으로써,
input data에 따라 main network의 parameter들을 학습하도록 합니다 (adaptive parameter).

2. Main network (task: classification)에 sub-network를 붙여, 학습시 backpropagation되는 gradient를 예측합니다.
새로운 데이터에 대한 grdient를 sub-network가 예측한다면, 후에 main network를 새로운 데이터에 대해 학습시킬 때 sub-network를 사용함으로써
grdient를 예측하여 학습 속도를 빠르게 하는 이점이 있습니다.

3. 학습시키는 Task를 변경하는 것으로, 이 경우 sub-network는 없고 내부 parameter나 학습 grdient를 따로 예측하는 것은 아니지만,
새로운 query에 대한 "feature"를 바로 추출하여, support set에 있는 data와 feature들과 matching이 가능하게 learning하는 과정에서, 
새로운 data에 대한 generalization ability가 높아집니다.

해당 방법의 문제점은 "학습하는 것 뿐만 아니라 학습하는 방법까지 고려해야하니 학습 시간이 기존 방법에 비해 많이 걸리고 학습과정의 variance가 높아진다고 합니다.

### (a) MAML
### (b) MANNs
### (c) Matching Nets
### (d) Prototypical Nets

위 (a)~(d)의 실험 세팅은 Omniglot과 같은 single distribution에서 여러 task를 sampling하고 meta-learning을 수행하며, 
meta-test를 할때 같은 distribution에서 샘플링되지만 task가 다른 경우 새로운 task라고 정의하여, fast adaptation 이후(or direct) 성능을 측정합니다. 

위 가정에서 distribution안에 Omniglot만 있는 것이 아니라 다른 데이터셋(mini-ImageNet, CUB, FC100, etc) multimodal distribution에서 task가 수행된다면, 기존의 single distribution에서 우수한 성능을 보인 meta-learner model들의 성능이 저하되는 것을 볼 수 있다.
(해당 방법을 사용하는 이유는 single distribution 보다 multi-modal distribution에서의 관점이 real world와 유사하기 때문입니다.)

### [Multimodal Model-Agnostic Meta-Learning via Task-Aware Modulation, NeurIPS 2019](https://arxiv.org/pdf/1910.13616.pdf)
[Code](https://vuoristo.github.io/MMAML)

각각의 데이터셋 distribution을 하나의 mode로 정의하고 이 mode에 대한 task identity information을 반영해야 한다고 주장하며 MAML에 대해 일련의 task modulation 기법을 제안 -정창훈 님의 자료 인용-

