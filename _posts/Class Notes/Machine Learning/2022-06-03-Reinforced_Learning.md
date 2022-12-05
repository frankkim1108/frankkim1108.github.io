# 강화 학습

- 어떻게 상호작용을 하는가가 중요하다
- 경험을 중요시한다 (trial & error)
- perception $\uparrow$ , cognition $\uparrow$    →    판단력 $\uparrow$
- 과거의 경험을 기반으로 현재의 나의 knowledge $\uparrow$
- 벽돌깨기
    - Agent: computer or machine
    - Environment: Game
    - State: Current game state
    - Action: Moving the bar
    - Reward: Score
    - Policy: 판단력
- policy를 올바르게 세워 나가는 과정

Policy : 더 많은 reward를 받기 위해서 고민한다, function의 형태로 존재, 강화학습에서의 Kernel

- Model-Based RL : 환경에 대해 이미 정보를 다 가지고있다
- Model-Free RL : 환경에 대한 정보가 없을 때
- Agent가 Action을 통해서 Reward를 최대로 받도록 하는게 Policy function을 통해 하는것이다

## Model Based RL

### Markov Decision Process (확률)

- Markov Process $\subset$ Random Process
- Random Process : 시간의 진행에 따라 상태가 확률적으로 변화함
- Markov Process : Markov 속성을 가지는 Random process
- Agent does action and it affects the environment and changes its state and gives a reward back to the agent
- 위와 같은 “closed-loop”을 만들어야한다
- State 0 ~ State t 까지 가서 State t+1에 도달할 확률은 State t에서 State t+1에 도달할 확률과 똑같다
- 순차적인 결정을 내리는것이 강화학습임
- 강화학습에서 최종 목표는 Policy를 최대화 하는것 → State를 도달할때 마다 Policy를 최대화 하면서 Action을 취한다
- State t —policy—> Action —reward—> State t+1
- State → Action : State value function
- Action → State : Action value function

### Bellman Equation

- State-Value function & Action-Value function 의 관계
- 현재의 state/action 과 다음 state/action과의 관계식
- Dynamic Programming의 한 종류이다
- Markov와의 차이점은 Markov는 바로 직전 state만 신경 쓰지만 Bellman은 모두 기억하면서 활용을 한다
- 재귀 vs DP
    - time complexity 차이가 매우 크다
    - 재귀는 여러번 call 해야하지만 dp는 한번에 가져온다

### Monte-Calro Methods

- Model-based DP는 계산 복잡도의 한계로 실제 문제에 적용 불가능
- Model-free : 환경을 모르기 때문에 확률로 접근한다
- Monte-Carlo Method: 무한이 여러번 Sampling 하면 한 특징을 그려낼 수 있다
- 여러번 Sampling 하면서 특징이 결국에는 수렴을 해야하기 때문에 MCMC 사용
    - 넓은 search space를 Markov Chain을 사용해서 space를 줄인다

## Recap

지도 학습 vs 비지도 학습

- 훈련데이터에 타깃 유무

머신러닝의 학습 과정

- 데이터로부터 특성 데이터와 타깃 데이터의 관계, 패턴을 학습하여 분류 혹은 예측
- 파라미터가 최적화 되는 과정에서 특정이 만들어진다

학습이 잘 되기 위해

- 훈련 데이터와 테스트 데이터를 나눠야한다
- 테스트 데이터는 훈련 데이터에 들어가면 안된다 → 예측이 아니라 기억이다
- Cross-Validation : 교차적으로 Train / Validation 세트를 나누어 가며 모델의 학습 정확도 평가
- train data가 validation에 들어가서 검증을 오염시키면 안된다

- 시계열 데이터 (Time series)
    - Sliding Window를 사용해서 data augmentation을 하기 때문에 데이터 중첩이 일어난다
    - Train 과 Validation이 자주 겹친다
    - error가 자주 일어난다
    - A : 나는, C : 기계, B: 나는 기계 사이
    - 문제가 생긴다
    
- 결정계수 (Coefficient of determination, $R^2$): 회귀의 정확도를 표현
    - $R^2 = 1 - {(타깃 - 예측)^2의\space 합 \over (타깃 - 평균)^2 의 \space 합}$고
    - 과대적합과 과소적합 확인 가능

Accuracy의 한계: Positive만 물어본다, class imbalance를 알아내기 어렵다

1종 오류: 실제 효과가 없는데 효과가 있다고 나타내는 것

2종 오류: 실제로 효과가 있는데 효과가 없다고 하는 것

### Precision / Recall

Precision : 정밀도 (내 모델이 positive하게 예측한것 중에 실제로 positive 한 것)

Recall : 재현율 (positive data 중에서 내 모델이 얼마나 positive 하게 예측했나)

F1 Score = 2 x ${recall \times precision} \over {recall + precision}$

mAP (ROC 와 연관되어있음 PR과 차이도 봐야함)

- x축: recall
y축: precision
그래프가 그려진 curve의 면적

## Receiver Operating Characteristic (ROC) Curve

- 이진 분류 시스템의 성능 평가 기법
- True Positive Rate = Sensitivity = Recall
- False Positive Rate = Specificity = Precision
- True Positive Rate $\uparrow$   &    False Positive Rate $\downarrow$
- ROC curve는 True Positive Rate 과 False Positive Rate의 관계
- ROC curve 위의 점은 Threshold 값에 대한 TPR과 FPR의 관계
- Curve가 클수록 좋다

### PR curve vs ROC curve

- PR : 세부적이다
ROC : generative
