# Paper-review
관심있게 보았던 논문의 리뷰를 올리도록 합니다.. 내용은 최대한 압축하여 작성하였으며, 자세한 내용은 pdf를 보시면 됩니다.

# Meta-Learning
최근 관심있게 보았던 학습 방법입니다. 이 학습의 목적은 컴퓨터가 사람과 동등한 인지능력을 가지도록 만드는 것입니다.. 특히, 사람과 마찬가지로 Train set과 Test set의 label이 겹치지 않습니다. 
크게 Metric-based, Model-based, Optimized-based Approach로 나눌 수 있습니다.

## Siamese Neural Networks
Metric-based Appoach 에서 가장 기본적인 알고리즘이다. 입력 데이터는 2개가 들어가며 학습을 진행하게 됩니다..

다른 Deep-learning과의 차별점은 2개 각각의 입력 데이터의 특징을 찾는 CNN의 구조가 서로 같다는 점과 loss function을 L1-distance로 사용했다는 점입니다.. 즉, 두 개의 입력 데이터에 대해 같은 특징을 추출하였으며, L1-distance를 사용하여 유사도를 측정했다는 의미입니다.

![image](https://user-images.githubusercontent.com/37894081/111735681-c3cc2880-88bf-11eb-8652-a9b45fc97958.png)

Train set 과 Test set은 Omniglot Dataset을 사용했으며, 학습 데이터와 테스트 데이터의 label은 절대 겹치지 않는다.

결과는 사람이 직접 분류했을 때("Humans")보다 3.5%정도 낮았으며, MNIST 데이터만으로 테스트를 진행했을 시 70.3%의 결과가 나오게 되었다.

![image](https://user-images.githubusercontent.com/37894081/111735984-5076e680-88c0-11eb-968e-ca351bd85537.png)

![image](https://user-images.githubusercontent.com/37894081/111735992-54a30400-88c0-11eb-9468-0d6270696aa2.png)

# Reinforcement Learning
이 알고리즘은 에이전트가 보상을 통해 학습하는 방법입니다. 기본적으로 Markov Decision Process (MDP)의 요소인, 에이전트의 State, Action, Reward, Transition probability, Discount factor로 구성되어 있습니다. State는 현재 에이전트의 상태,상황이며 Action은 현재 에이전트가 실행하는 행동을 뜻합니다. Reward는 에이전트가 Action을 통해 환경으로부터 받는 보상이며, Discount factor는 이전에 받았던 reward의 가중치를 뜻합니다. Transition probability는 에이전트가 Action을 했을 시, 실제로 그 행동을 얼만큼의 확률로 갈 수 있을지를 나타낸 변수입니다.

## Salsa to DQN
본 pdf는 대학원 1학기 머신러닝 수업때 발표했었던 내용입니다. Salsa ~ Deep Q-Network까지의 내용을 담고있습니다.

## Grandmaster level in StarCraft II using multi-agent reinforcement learning
본 내용은 연구실에서 진행하는 저널 미팅때 발표했었던 내용입니다.

이 내용을 이해하려면 기본적으로 Deep Q-Network와 Supervised Learning을 이해하셔야 합니다. 본 내용의 간단한 설명은 Starcraft2 게임에서 여러 에이전트가 서로 대결을 하며 학습하는 것입니다. 에이전트가 학습하기 이전에 우선 스타크래프트2의 replay 데이터를 이용하여 통계를 내어 사용하게 됩니다(Supervised Learninig). 이후 이 통계를 사용하여 에이전트는 참고를 하면서 학습합니다. 현재 에이전트가 가장 게임을 잘 할수 있도록 여러 트릭을 사용하여 이전에 싸워서 졌던 자신과 싸우며, 다른 전략을 지속적으로 시도하도록 합니다.

![image](https://user-images.githubusercontent.com/37894081/111737301-b2d0e680-88c2-11eb-88f4-5b91bb9e2768.png)

결과는 Supervised만 했을 시, 다이아몬드 티어까지 갔습니다. 44일동안 학습을 모두 마친 에이전트는 상위 0.4% 미만의 Grand Master 티어가 되었습니다.

![image](https://user-images.githubusercontent.com/37894081/111737319-bc5a4e80-88c2-11eb-9485-6eb731e086d8.png)

# Graph Neural Networks
이 알고리즘은 CNN과 비슷한 알고리즘입니다. 하지만 CNN과 달리, 각 특징마다 연결된 edge가 있으며 연결된 edge끼리 Neural Networks를 업데이트합니다. 따라서 CNN처럼 근처의 모든 레이어의 값으로 업데이트를 하지 않고 연결된 레이어 값들로 업데이트를 하기 때문에 CNN보다 더욱 활용성 있다고 보여집니다. 하지만 특징마다 연결 edge를 어떻게 설정할 것이며, 어떻게 연결할 지에 대한 것이 큰 이슈입니다.

## Graph Attention Networks
본 내용은 연구실에서 진행하는 저널 미팅 때 발표했었던 내용입니다. 이 논문은 GNN의 기존 업데이트 방식에 추가로 Self-Attention을 추가한 내용입니다. 내용은 기존 GNN과 크게 다르지 않기 때문에 생략하도록 하겠습니다.

![image](https://user-images.githubusercontent.com/37894081/115142860-ed26d280-a07e-11eb-8581-5eda36873075.png)

Self-Attention을 추가하여 자신과 비슷한 특징들이 더 많은 Attention Value를 가져가므로 GCN보다 더 좋은 결과를 도출하게 됩니다. 본 논문은 GNN의 논문들을 이해하기 위해 필수로 이해해야 하는 내용이므로 반드시 읽어야합니다.

![image](https://user-images.githubusercontent.com/37894081/115142869-f617a400-a07e-11eb-936c-21f3ca686297.png)


