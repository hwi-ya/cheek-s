---
created: 2025-04-01
updated: 2025-04-01
dg-publish: true
---

## p.1(Parameter Tuning)
  **The last thing we will learn in designing genetic algorithms before we start solving real problems is studying global algorithm parameters – population size, crossover probability, mutation probability**
  우리가 실제 문제를 풀기 시작하기 전에 유전 알고리즘 설계에서 마지막으로 배울 것은 전역 알고리즘 매개변수인 집단 크기, 교차 확률, 돌연변이 확률을 연구하는 것이다.<br/>
  
  **These parameters govern the dynamics of genetic algorithm flow**
  이 매개변수들은 유전 알고리즘의 흐름을 지배하는 동작을 결정한다.<br/>
  
  **We will study each parameter influence, and try to get the intuitive understanding of how each parameter affects the algorithm**
  우리는 각 매개변수의 영향을 살펴보고, 각 매개변수가 알고리즘에 어떤 영향을 미치는지 직관적으로 이해하려고 할 것이다.<br/>
<br/>
  <hr>

## p.2(Structure)
  **Population size**  
  집단 크기<br/>
  
  **Crossover probability**  
  교차 확률<br/>

  **Mutation probability**  
  돌연변이 확률<br/>
<br/>
  <hr>

## p.3(Population size)
  **we already studied this parameter and concluded that the larger the population size, the higher the probability of finding the best solution**  
  우리는 이미 이 매개변수를 공부했고, 집단 크기가 클수록 최적의 해를 찾을 가능성이 높다는 결론에 도달했다.<br/>
  
  **But is it very difficult to maintain a big population**  
  하지만 큰 집단을 유지하는 것은 매우 어렵다.<br/>
  
  **Understanding the effect of population size will help in finding the smallest population size that achieves the best solution**  
  집단 크기의 영향을 이해하는 것은 최적의 해를 도출할 수 있는 가장 작은 집단 크기를 찾는 데 도움이 된다.<br/>
  
  **Each individual can be compared to an explorer who studies the environment in search of the best place – the coordinates of each explorer are determined by his set of genes**  
  각 개체는 최적의 장소를 찾기 위해 환경을 탐색하는 탐험가에 비유할 수 있으며, 각 탐험가의 좌표는 그의 유전자 집합에 의해 결정된다.<br/>
  
  **Each individual has its own unique set of genes, which means it has its own unique location on the map**  
  각 개체는 고유한 유전자 집합을 가지고 있으며, 이는 지도의 고유한 위치를 의미한다.<br/>
  
  **The more individuals we have, the higher the probability that someone will find some good place, and spread their location among other individuals, passing its gene set to others; so gradually the entire population will be able to move to the place found by one of the individuals, and continue searching there**  
  개체 수가 많을수록 누군가가 좋은 장소를 발견할 확률이 높아지고, 그 위치가 다른 개체들에게 퍼지면서 자신의 유전자 집합을 전달하게 된다; 그래서 점차 전체 집단이 그 개체가 발견한 장소로 이동하고, 그곳에서 탐색을 계속할 수 있게 된다.<br/>
  
  **Initially, all individuals are in random places, which from the point of view of fitness functions are of no interest – it's like a desert**  
  처음에는 모든 개체가 무작위 위치에 있으며, 적합도 함수의 관점에서 보면 아무런 가치가 없는 장소에 있다 – 마치 사막과 같다.<br/>
  
  **One of the individuals finds the river, and the entire population strives for it, but the river also has a lot of different places to stay in terms of suitability, and our population already continues to search in the vicinity of the river**  
  개체 중 한 명이 강을 발견하면, 전체 집단이 그곳을 향해 나아가게 되지만, 강 주변에도 적합성 면에서 머물 수 있는 다양한 장소가 있으며, 우리의 집단은 이미 강 주변에서 계속 탐색을 이어가게 된다.<br/>

  <img src="https://github.com/user-attachments/assets/a76b161c-8c6d-4fcf-9b1e-2f9234229eb9" width="400" height="270"/>
  <br/>
  
  - **one of the individuals notifies other about the place with high fitness value**  
    개체 중 한 명이 높은 적합도 값을 가진 장소에 대해 다른 개체들에게 알린다.<br/>

  **There is no recipe according to which the optimal population size could be calculated, but it should be understood that the entire population will tend to one point**  
  최적의 집단 크기를 계산할 수 있는 공식은 없지만, 전체 집단이 하나의 지점으로 수렴하려는 경향이 있다는 것은 이해해야 한다.<br/>
  
  **Let's look at the heat map of the two variable function $f(x,y)$ on the square $[-10, 10]$ and try to find its maxima**  
  두 변수 함수 $f(x, y)$의 $[-10, 10]$ 구간에 대한 히트맵을 살펴보고, 그 최대값을 찾아보자.<br/>
  
  **In this square, we see that there are 2 red zones that are most suitable for the population in terms of the fitness function**  
  이 정사각형 안에는 적합도 함수의 관점에서 집단에게 가장 적합한 두 개의 빨간 영역이 있다.<br/>
  
  **The redder the area, the better the place for the population**  
  영역이 붉을수록 집단에게 더 좋은 장소를 의미한다.<br/>
  
  <img src="https://github.com/user-attachments/assets/dfa53d40-d1e4-4c1e-b109-761897442452" width="400" height="332"/>
  <br/>
  
  - **two variable function heat map. red areas are most appropriate places for the population.**  
    두 변수 함수의 히트맵. 빨간 영역은 집단에게 가장 적합한 장소들이다.<br/>

  **Let’s study how population migrates in search of the best place**  
  집단이 최적의 장소를 찾기 위해 어떻게 이동하는지 살펴보자.<br/>

  <img src="https://github.com/user-attachments/assets/eab9bdb9-f340-4648-96f7-acd4feb90189" width="400" height="365"/> <br/>
  <img src="https://github.com/user-attachments/assets/49789a58-6a04-4396-b481-73f32b3baa56" width="400" height="367"/> <br/>
  <img src="https://github.com/user-attachments/assets/bfdafcf7-5ed1-49e4-a583-b25bba582ffe" width="400" height="369"/> <br/>  

  **the whole population is concentrated in one area**  
  전체 집단이 한 영역에 집중되어 있다.<br/>
  
  **This area is good, but far from the best**  
  이 영역은 괜찮지만, 최적의 장소와는 거리가 있다.<br/>

  <img src="https://github.com/user-attachments/assets/608cbcaf-137a-4f8e-9d8f-289c1c39e7f1" width="800" height="354"/>
















  

