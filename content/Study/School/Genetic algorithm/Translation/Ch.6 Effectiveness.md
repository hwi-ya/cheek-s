---
created: 2025-03-30
updated: 2025-04-08
dg-publish: true
draft: true
---

## p.1(Effectiveness)
  **there are a vast number of options for constructing a GA**  
  유전 알고리즘을 구성하는 방법에는 다양한 옵션이 존재합니다.<br/>

  **Thus, the following questions arise**  
  따라서, 다음과 같은 질문들이 발생합니다.<br/>

  - **How to compare the two architectures of the GA with each other?**  
    두 개의 유전 알고리즘 구조를 서로 어떻게 비교할 것인가?<br/>

  - **How do we know that the change we made to the architecture improved its effectiveness in finding a solution?**  
  우리가 아키텍처에 변경을 가했을 때, 그것이 해결책을 찾는 데 효과성을 향상시켰는지 어떻게 알 수 있을까?<br/>

     ![image](https://github.com/user-attachments/assets/37a0a727-38d7-4620-b31c-a5cb32619972)  
<br/>
  <hr>

## p.2(Structure)
  **Best individual**  
  최고의 개체<br/>
  
  **Total number of individuals**  
  전체 개체 수<br/>
  
  **Genetic algorithm as random variable**  
  랜덤 변수로서의 유전 알고리즘<br/>
  
  **Monte-Carlo simulation**  
  몬테카를로 시뮬레이션<br/>
<br/>
  <hr>

## p.3(Objectives)
  **Understand how to measure the effectiveness of a GA**  
  유전 알고리즘의 효과성을 측정하는 방법을 이해하다.<br/>
  
  **Get a clear criteria of GA quality**  
  유전 알고리즘 품질에 대한 명확한 기준을 얻다.<br/>
  
  **Get an intuitive view of the GA as a random variable**  
  유전 알고리즘을 랜덤 변수로서 직관적으로 이해하다.<br/>
  
  **Compare different implementations of GA**  
  유전 알고리즘의 다양한 구현 방식을 비교하다.<br/>
<br/>
  <hr>

## p.4(Best individual)
  **we formalized the problem, and built the architecture of the GA**  
  우리는 문제를 공식화하고, 유전 알고리즘의 구조를 구축했다.<br/>
  
  **What will we consider as the solution to the problem?**  
  우리는 문제의 해결책으로 무엇을 고려할 것인가?<br/>
  
  **As a rule, the solution is the individual who has shown the best fitness in the entire history of evolution**  
  일반적으로 해결책은 진화의 전체 역사에서 가장 좋은 적합도를 보인 개체가 된다.<br/>
  
  - **NOTE: It is not at all necessary that the best individual will be in the last generation**  
    참고: 가장 좋은 개체가 반드시 마지막 세대에 있을 필요는 없다.<br/>
    
  - **In evolution, it does not always happen that each subsequent generation is better than the previous one**  
    진화에서는 각 후속 세대가 이전 세대보다 항상 더 나은 결과를 보이는 것은 아니다.<br/>
    
  - **Therefore, we choose the best from the entire history of evolution**  
    따라서, 우리는 진화의 전체 역사에서 가장 좋은 개체를 선택한다.<br/>

  **Let's study an example of searching for the best individual, and analyzing the population fitness curve's behavior**  
  가장 좋은 개체를 찾는 예시와 개체군 적합도 곡선의 행동을 분석하는 예제를 살펴보자.<br/>
  
  **Say we want to find the maxima of some complicated function:**  
  우리가 어떤 복잡한 함수의 최대값을 찾고자 한다고 가정하자:<br/>
  
  - **$𝑠𝑖𝑛𝑥 𝑐𝑜𝑠𝑥 + (\frac{|(𝑥+50)(𝑦−10)|}{10})^{0.1}$**  
  
  **We will keep tracking the best individuals, the average fitness, and the best fitness for each generation**  
  우리는 각 세대에 대해 가장 좋은 개체들, 평균 적합도, 그리고 최고의 적합도를 계속 추적할 것이다.<br/>

  ![image](https://github.com/user-attachments/assets/e7f10aed-19dc-4fa4-a6d0-12b8dc53ec28)
<br>

  **Obviously, the metric best fitness ever (that is, best fitness), can be used as a metric of GA effectiveness**  
  명백히, "최고의 적합도" (즉, 최고의 적합도)는 유전 알고리즘의 효과성을 측정하는 지표로 사용할 수 있다.<br/>
  
  **NOTE: It is important to note how the curves – the best fitness of the generation and the average fitness of the generation behave**  
  참고: 세대의 최고의 적합도 곡선과 세대의 평균 적합도 곡선이 어떻게 행동하는지 주의 깊게 살펴보는 것이 중요하다.<br/>
  
  **In some generations, these curves can go down, but they go up in the global view**  
  일부 세대에서는 이러한 곡선이 내려갈 수 있지만, 전반적으로 보면 상승한다.<br/>
  
  **That is why it is essential to take the best individual of the whole history, but not the best of the last generation**  
  그래서 중요한 것은 마지막 세대에서 가장 좋은 개체가 아니라, 전체 역사에서 가장 좋은 개체를 선택하는 것이다.<br/>
<br/>
  <hr>

## p.8(Total number of individuals)
  **The speed at which the algorithm makes decisions is a critical parameter**  
  알고리즘이 결정을 내리는 속도는 중요한 파라미터이다.<br/>
  
  **In the GA, the most complex operation calculates the fitness function; in turn, the fitness function is calculated once for each individual**  
  유전 알고리즘에서 가장 복잡한 연산은 적합도 함수 계산이다; 그에 따라, 적합도 함수는 각 개체마다 한 번씩 계산된다.<br/>
  
  **Accordingly, the problem of the algorithm's speed can be reduced to the number of individuals required for evolution**  
  따라서 알고리즘의 속도 문제는 진화를 위해 필요한 개체 수로 축소될 수 있다.<br/>

  **NOTE: It is crucial to ensure that the fitness function is calculated only once for each individual. Avoid doing that!**  
  참고: 적합도 함수는 각 개체에 대해 한 번만 계산되도록 보장하는 것이 중요하다. 이를 반복하지 않도록 하라!<br/>
<br/>
  <hr>

## p.10(Genetic algorithm as random variable)
  **The GA contains many elements of randomness in its work**  
  유전 알고리즘은 작업에서 많은 요소의 무작위성을 포함한다.<br/>
  
  **It is impossible to tell in advance what decision the GA will come to, in most cases**  
  대부분의 경우, 유전 알고리즘이 어떤 결정을 내릴지 미리 알 수 없다.<br/>

  **We can consider the GA as a random variable that returns several values**  
  우리는 유전 알고리즘을 여러 값을 반환하는 랜덤 변수로 간주할 수 있다.<br/>
  
  **The number of individuals is not 100% predictable too**  
  개체 수 역시 100% 예측할 수 없다.<br/>
  
  **Because GA architecture has parameters like and thus, we don’t know in advance how often crossover and mutation occur**  
  유전 알고리즘 구조에는 교차와 돌연변이와 같은 파라미터가 있기 때문에, 우리는 미리 교차와 돌연변이가 얼마나 자주 발생할지 알 수 없다.<br/>
  
  **Let's examine the implementation of the GA as a random variable**  
  유전 알고리즘을 랜덤 변수로서 구현한 예제를 살펴보자.<br/>
  
  **We will run the GA on the same problem 1000 times, and see the results.**  
  우리는 같은 문제에 대해 유전 알고리즘을 1000번 실행하고 결과를 확인할 것이다.<br/>
  
  ![image](https://github.com/user-attachments/assets/b196a882-3385-4bd9-9282-f533bdfe1059)
<br/>

  **Let’s try to change something in our algorithm, like, increase the number of population**  
  우리 알고리즘에서 무언가를 변경해 보자, 예를 들어 개체군 수를 늘려보자.<br/>
  
  ![image](https://github.com/user-attachments/assets/76d3fa05-d436-4bd7-ab6e-b925ab9549f3)
<br/>

  **Consider how best fitness, and total number of individuals are related**  
  최고 적합도와 전체 개체 수가 어떻게 관련되는지 고려해보자.<br/>
  
  **Let’s run the same algorithm for different population sizes and analyze dependency on these two parameters**  
  같은 알고리즘을 다른 개체군 크기로 실행하고, 이 두 파라미터에 대한 의존성을 분석해보자.<br/>
  
  ![image](https://github.com/user-attachments/assets/614bcba0-9309-4658-a206-f7c0724a0d70)
<br/>

  **The more the number of individuals participate in evolution, the higher the probability that the best fitness parameter will be higher**  
  진화에 참여하는 개체 수가 많을수록 최고의 적합도 파라미터가 더 높을 확률이 커진다.<br/>
  
  **GA is a random variable that returns values like – best individual, best fitness, number of individuals**  
  유전 알고리즘은 다음과 같은 값을 반환하는 랜덤 변수이다: 최고의 개체, 최고의 적합도, 개체 수.<br/>
  
  **Good GA architecture has the right balance between the high probability of getting acceptable best fitness and a low number of individuals**  
  좋은 유전 알고리즘 구조는 수용 가능한 최고의 적합도를 얻을 높은 확률과 적은 개체 수 사이의 적절한 균형을 갖고 있다.<br/>
<br/>
  <hr>

## p.15(Monte-Carlo simulation)
  **Monte-Carlo simulation applies to multiple repetition tasks when each task can be solved in the foreseeable time**  
  몬테카를로 시뮬레이션은 각각의 작업이 예측 가능한 시간 안에 해결될 수 있을 때, 반복 작업에 적용된다.<br/>
  
  **For example, solving routing problems at the airport, optimizing the flight movement of an artificial insect, building an optimal investment portfolio**  
  예를 들어, 공항에서의 경로 문제 해결, 인공 곤충의 비행 움직임 최적화, 최적의 투자 포트폴리오 구축 등이 있다.<br/>
  
  **Sometimes, GAs are applied to unique problems that are solved just once, and you need to find an acceptable solution only once**  
  때때로, 유전 알고리즘은 한 번만 해결되는 고유한 문제에 적용되며, 이 경우에는 한 번만 수용 가능한 해결책을 찾으면 된다.<br/>
  
  **Such tasks can be very time-consuming, and it makes no sense for them to answer the questions – How to make the algorithm work effectively?**  
  이러한 작업들은 매우 많은 시간이 소요될 수 있으며, 그 경우에는 "어떻게 알고리즘을 효율적으로 작동하게 할 것인가?"라는 질문에 답하는 것이 의미가 없을 수 있다.<br/>
  
  **It is important just to find any solution**  
  중요한 것은 단지 어떤 해결책이든 찾는 것이다.<br/>
  
  **The flow of Monte-Carlo simulation**  
  몬테카를로 시뮬레이션의 흐름<br/>
    ![image](https://github.com/user-attachments/assets/57f6c07c-0004-4f48-8277-3a63c72f8c47)
<br/>

  **We have an interesting step here called generate That is very important to test the architecture of GA on different datasets, that is, problems, from the same area**  
  여기서 "generate"라는 흥미로운 단계가 있는데, 이는 유전 알고리즘의 구조를 같은 영역의 서로 다른 데이터셋, 즉 문제들에 대해 테스트하는 데 매우 중요하다.<br/>
  
  **If we are testing an implementation of a routing problem solver, we must check it on various route problems**  
  만약 우리가 경로 문제 해결기의 구현을 테스트하고 있다면, 다양한 경로 문제에 대해 그것을 검증해야 한다.<br/>
  
  **It is possible to test a GA on historical data or to try generating it**  
  유전 알고리즘을 과거 데이터에 대해 테스트하거나, 데이터를 생성하여 테스트하는 것이 가능하다.<br/>
  
  **We will use this method in future chapters, and we will see how we can compare different architectures for the same problem**  
  우리는 이후 장에서 이 방법을 사용할 것이며, 동일한 문제에 대해 서로 다른 아키텍처들을 어떻게 비교할 수 있는지 살펴볼 것이다.<br/>
<br/>
  <hr>

## p.19(Conclusion)
  **Although the GA is a random variable, and in most real-life problems, it is impossible to say with 100% accuracy as to which answer will be obtained**  
  비록 유전 알고리즘이 랜덤 변수이긴 하지만, 대부분의 실제 문제에서는 어떤 해답이 도출될지 100% 정확하게 말하는 것은 불가능하다.<br/>
  
  **We can compute characteristics of the GA efficiency, and compare different implementations with each other**  
  우리는 유전 알고리즘의 효율성 특성을 계산하고, 서로 다른 구현들을 서로 비교할 수 있다.<br/>
  
  **In the next chapter, we will go through the last aspect of GA architecture – parameter tuning**  
  다음 장에서는 유전 알고리즘 구조의 마지막 측면인 파라미터 튜닝에 대해 살펴볼 것이다.<br/>
  
  **We already know that GAs have parameters – population size, crossover probability, mutation probability. We will study how they affect the performance of an algorithm.**  
  우리는 이미 유전 알고리즘에 개체군 크기, 교차 확률, 돌연변이 확률과 같은 파라미터들이 있다는 것을 알고 있다. 우리는 이러한 파라미터들이 알고리즘의 성능에 어떤 영향을 미치는지 공부할 것이다.<br/>
<br/>










  
