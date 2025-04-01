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

  <img src="https://github.com/user-attachments/assets/608cbcaf-137a-4f8e-9d8f-289c1c39e7f1" width="800" height="354"/> <br/>

  **Now, let’s study the evolution path of population size 10**  
  이제 집단 크기 10의 진화 경로를 살펴보자.<br/>

  <img src="https://github.com/user-attachments/assets/f6d42e85-5260-42a0-9a46-9efc7f871e30" width="800" height="361"/> <br/>

  **Evolution finishes in a similar manner like the evolution for 6 individuals in the population, but evolution with 10 individuals has found a slightly better solution than the previous one**  
  진화는 집단 내 6개의 개체가 있었을 때와 유사한 방식으로 종료되지만, 10개의 개체로 진행된 진화는 이전보다 약간 더 나은 해를 찾아냈다.<br/>

  <img src="https://github.com/user-attachments/assets/eaeb451d-d6b0-472e-b473-2e3cba2ef5ee" width="400" height="367"/> <br/>

  **Looking at the evolution path of the population with size 20**  
  집단 크기 20의 진화 경로를 살펴보면<br/>

  <img src="https://github.com/user-attachments/assets/6275413e-5c50-4a3e-b8e5-a6b0170b00c4" width="400" height="364"/> <br/>

  **let’s see what happens if the number of individuals is equal to 50**  
  개체 수가 50일 경우 어떤 일이 발생하는지 살펴보자.<br/>

  <img src="https://github.com/user-attachments/assets/c5f73858-34ee-4bc6-8d89-429f52b176b3" width="400" height="368"/> <br/>
  <img src="https://github.com/user-attachments/assets/b8066893-ce60-40bb-884a-303a8bc1c627" width="800" height="356"/> <br/>
  <img src="https://github.com/user-attachments/assets/9ebbbeaa-50ba-40c4-879b-f84b1533e354" width="800" height="366"/> <br/>

  **Let’s get an intuitive understanding of this paradox**  
  이 역설에 대해 직관적으로 이해해보자.<br/>
  
  **Small populations are more easily influenced by one or more leaders**  
  작은 집단은 한 명 또는 그 이상의 리더에게 더 쉽게 영향을 받는다.<br/>
  
  **It is enough for one or several individuals to find an acceptable place, which then makes it is easier for them to call the entire population**  
  한두 개체가 적절한 장소를 찾기만 해도, 그들이 전체 집단을 그곳으로 이끄는 것이 더 쉬워진다.<br/>
  
  **In case of a large population, there is a lot of noise**  
  큰 집단의 경우에는 잡음이 많다.<br/>
  
  **Different individuals call others to completely different places, and most call on, not to move anywhere at all**  
  서로 다른 개체들이 다른 장소로 다른 개체들을 부르고, 대부분은 아예 이동하지 말자고 부르기도 한다.<br/>
  
  **Large populations have very high inertia and take much longer to organize themselves**  
  큰 집단은 매우 높은 관성을 가지고 있어서 스스로를 조직하는 데 훨씬 더 오랜 시간이 걸린다.<br/>

  <img src="https://github.com/user-attachments/assets/6e7b382b-72ed-4949-bd07-a32293be344f" width="400" height="229"/> <br/>

  **Now you may think that large populations are not suitable for organized search at all**  
  이제는 큰 집단이 조직적인 탐색에 전혀 적합하지 않다고 생각할 수도 있다.<br/>
  
  **But we have another paradox here**  
  하지만 여기 또 다른 역설이 존재한다.<br/>
  
  **Look at the last generation of population sized 50**  
  집단 크기 50의 마지막 세대를 살펴보자.<br/>
  
  **It seems that this population has no change to on the top of the but let’s look at what will happen after 200 generations**  
  이 집단은 정상에 도달할 가능성이 없어 보이지만, 200세대 후에 어떤 일이 일어날지 살펴보자.<br/>

  <img src="https://github.com/user-attachments/assets/4362fc5f-b159-47f8-8e30-18fdcf142385" width="400" height="369"/> <br/>

  **This population has found both absolutely best solutions!**  
  이 집단은 두 개의 절대적으로 최적의 해를 모두 찾아냈다!<br/>
  
  **It seemed that there was no chance for this to happen, but it happens**  
  그럴 가능성이 전혀 없어 보였지만, 실제로는 그렇게 일어났다.<br/>
  
  **Larger populations take much longer to organize themselves, but are able to construct much more complex solutions**  
  더 큰 집단은 스스로를 조직하는 데 훨씬 더 오랜 시간이 걸리지만, 훨씬 더 복잡한 해를 만들어낼 수 있다.<br/>
  
  **Smaller population moves faster, but gets stuck earlier**  
  더 작은 집단은 더 빨리 움직이지만, 더 일찍 막히게 된다.<br/>
  
  **Larger population moves slower, but keeps moving farther than the smaller ones and constructs more complicated solutions.**  
  더 큰 집단은 더 느리게 움직이지만, 더 작은 집단보다 더 멀리 이동하며 더 복잡한 해를 만들어낸다.<br/>
<br/>
 <hr>
 
## p.23(Crossover probability)
  **Crossover is a mechanism for the exchange of information between two individuals**  
  교차는 두 개체 간의 정보 교환을 위한 메커니즘이다.<br/>
  
  **In the architecture of the GA, individuals make a crossover with a certain probability**  
  유전 알고리즘의 구조에서 개체들은 일정한 확률로 교차를 수행한다.<br/>
  
  **Let's study what the crossover probability is, and how it affects the evolution of the population**  
  교차 확률이 무엇이며, 그것이 집단의 진화에 어떤 영향을 미치는지 살펴보자.<br/>
  
  **Let's say we have two individuals that have passed the selection, which means it is highly possible that those two individuals already have something valuable in their genes**  
  선택을 통과한 두 개체가 있다고 가정해보자. 이는 이 두 개체가 이미 유전자에 어떤 가치 있는 것을 가지고 있을 가능성이 높다는 것을 의미한다.<br/>

  **And in the next step, the following can happen:**  
  그리고 다음 단계에서는 다음과 같은 일이 일어날 수 있다:<br/>
  
  **Either with probability p, they can make a crossover, thereby making an attempt to generate a new solution, perhaps a fundamentally new solution that will greatly help the population in the process of evolution**  
  확률 $p$로 그들은 교차를 수행할 수 있으며, 이를 통해 집단의 진화 과정에 크게 도움이 될 수 있는 근본적으로 새로운 해를 생성하려는 시도를 하게 된다.<br/>
  
  **Or with probability 1-p they can do self-cloning to allow good individuals to develop further without any crossover**  
  혹은 확률 $1−p$로 교차 없이 자기 복제를 수행하여, 우수한 개체가 더 발전할 수 있도록 한다.<br/>
  
  **This probability p is called crossover probability**  
  이 확률 $p$를 교차 확률(crossover probability)이라고 한다.<br/>

  <img src="https://github.com/user-attachments/assets/35d06064-7a76-4ba7-abab-a4c0f966a393" width="400" height="337"/> <br/>

  **There is always a risk that the crossover will be unsuccessful and the offspring will not only not give anything useful for the rest of the population, but will also lose what the parents had**  
  교차가 실패할 위험은 항상 존재하며, 그 자식 개체는 집단 전체에 유용한 것을 제공하지 못할 뿐만 아니라 부모가 가지고 있던 것마저 잃을 수 있다.<br/>
  
  **therefore, crossover itself can both increase the average fitness function of the population and lower it**  
  따라서 교차는 집단의 평균 적합도 함수를 증가시킬 수도 있고, 감소시킬 수도 있다.<br/>
  
  **Let's study the variations of the evolution to find the maxima of some function f(x,y) for different values of crossover probability**  
  이제 교차 확률의 다양한 값에 따라 함수 $f(x,y)$의 최댓값을 찾기 위한 진화의 변화를 살펴보자.<br/>

  <img src="https://github.com/user-attachments/assets/7ff17da9-4267-4cb0-af9a-12b213f3bf86" width="400" height="327"/> <br/>
  - **Two variable function heat map. Red areas are the most appropriate places for the population**  
    두 변수 함수의 히트맵. 빨간 영역은 집단에게 가장 적합한 장소들이다.<br/>

  **Let’s look at the evolution of population with crossover probability equal to 0 (no crossover);**  
  교차 확률이 0 (교차 없음)일 때 집단의 진화 과정을 살펴보자.<br/>

  <img src="https://github.com/user-attachments/assets/c11cbb97-f33f-4573-976b-bd69e697d104" width="400" height="370"/> <br/>
  <img src="https://github.com/user-attachments/assets/049eb4da-17a8-47fc-9d9b-aeb8dc4220a2" width="800" height="359"/> <br/>
  <img src="https://github.com/user-attachments/assets/2e9006ba-00a1-43aa-a9e6-a894d83e7b5d" width="400" height="370"/> <br/>

  **In the last generation, practically there is no improvement over the 3rd generation.**  
  마지막 세대에서는 3세대에 비해 실질적인 개선이 거의 없다.<br/>
  
  **Why does this happen? The entire population rushed to individuals that were the best in the very first generation. The solution randomly found at the very beginning practically did not change**  
  왜 이런 일이 발생할까? 전체 집단이 첫 번째 세대에서 가장 우수했던 개체들에게 몰려갔기 때문이다. 처음에 우연히 발견된 해는 사실상 거의 변하지 않았다.<br/>
  
  **This was all because of the lack of crossover**  
  이 모든 것은 교차가 없었기 때문이었다.<br/>
  
  **The population did not have the opportunity to diversify its genes at the expense of others, possibly even bad, individuals**  
  집단은 다른 개체들, 심지어는 좋지 않은 개체들을 통해서라도 유전자를 다양화할 기회를 갖지 못했다.<br/>
  
  **An architecture without crossover is highly likely to quickly get the population stuck in one area, possibly very far from optimal**  
  교차가 없는 구조에서는 집단이 하나의 영역에 빠르게 갇히게 될 가능성이 매우 높으며, 그 영역은 최적 해로부터 매우 멀리 떨어져 있을 수도 있다.<br/>

  **Let’s look at the evolution with probability equal to 0.4**  
  교차 확률이 0.4일 때의 진화 과정을 살펴보자.<br/>

  <img src="https://github.com/user-attachments/assets/c4199611-30c2-4221-8e78-bcdaddcf0f30" width="800" height="357"/> <br/>

  **The individuals we see that again populate is located near the best solution of first generation**  
  우리가 보는 개체들은 다시 한 번 첫 번째 세대에서의 최적 해 근처에 모여 있다.<br/>
  
  **There is no significant improvement over the non-crossover architecture.**  
  교차가 없는 구조에 비해 뚜렷한 개선은 없다.<br/>

  <img src="https://github.com/user-attachments/assets/9edd66c3-06cc-4beb-960f-8445cb104ece" width="400" height="366"/> <br/>

  **Architecture with crossover probability equal to 0.7 has more interesting evolution**  
  교차 확률이 0.7인 구조는 더 흥미로운 진화 과정을 보여준다.<br/>

  <img src="https://github.com/user-attachments/assets/990e73bd-a1e7-44a5-8da8-7dbc15b53dac" width="800" height="357"/> <br/>

  **Crossover probability defines the degree of population variability. The higher the crossover probability, the stronger the population’s craving for new solutions**  
  교차 확률은 집단의 다양성 정도를 결정한다. 교차 확률이 높을수록 집단은 새로운 해를 더 강하게 갈망하게 된다.<br/>
  
  **The danger of a higher number of crosses is the loss of useful accumulated hereditary factors.**  
  교차 횟수가 많을수록 생길 수 있는 위험은 유용하게 축적된 유전적 요소들이 사라질 수 있다는 점이다.<br/>

  <img src="https://github.com/user-attachments/assets/da8d7b78-0015-4c4f-b700-9735574acdb3" width="400" height="372"/> <br/>
<br/>
 <hr>

## p.37(Mutation probability)
 **If the crossover is an attempt to create a new solution based on two existing solutions, then mutation is a completely random deviation that does not necessarily add something useful to the individual but is necessary for the constant search for the best solutions**  
 교차가 두 개의 기존 해를 바탕으로 새로운 해를 만들기 위한 시도라면, 돌연변이는 개체에게 반드시 유용한 것을 더하지는 않지만, 최적의 해를 끊임없이 탐색하기 위해 필요한 완전히 무작위적인 변화이다.<br/>
 
 **The mutation probability is the probability with which an individual in a new population will be mutated**  
 돌연변이 확률은 새로운 집단의 개체가 돌연변이를 겪을 확률을 의미한다.<br/>

 <img src="https://github.com/user-attachments/assets/4b8e24fa-ab57-4c95-b510-3e4c8930f28a" width="400" height="381"/> <br/>

 **Let's study the variations of the evolution to find the maxima of some function f(x,y) for different values of mutation probability**  
이제 돌연변이 확률의 다양한 값에 따라 함수 f(x,y)의 최댓값을 찾기 위한 진화의 변화를 살펴보자.<br/>

 <img src="https://github.com/user-attachments/assets/76137d24-ac32-4a28-b30c-0b2edce835f0" width="400" height="328"/> <br/>

 - **two variable function heat map. red areas are most appropriate places for the population.**  
    두 변수 함수의 히트맵. 빨간 영역은 집단에게 가장 적합한 장소들이다.<br/>

 **We will evaluate three types of GAs -- without mutation, with 0.3 mutation probability, and with 1 mutation probability**  
 세 가지 유형의 유전 알고리즘을 평가해보자 — 돌연변이가 없는 경우, 돌연변이 확률이 0.3인 경우, 그리고 돌연변이 확률이 1인 경우이다.<br/>

 <img src="https://github.com/user-attachments/assets/ad954cc0-3b2e-4b9c-932a-0334932b7b1c" width="800" height="362"/> <br/>

 **After four generations almost all individuals are on the same line; we need just one to slightly move right**  
 네 세대가 지난 후 거의 모든 개체가 같은 선상에 있다; 단 하나만이라도 오른쪽으로 약간 이동하면 된다.<br/>
 
 **But what will cause at least one individual to move to the right?**  
 하지만 적어도 하나의 개체가 오른쪽으로 이동하게 만들 요인은 무엇일까?<br/>
 
 **All individuals have practically the same x-coordinate gene value.**  
 모든 개체는 사실상 동일한 x좌표 유전자 값을 가지고 있다.<br/>
 
 **After crossover, x-coordinate will practically not change**  
 교차가 일어난다 해도 x좌표는 사실상 변하지 않을 것이다.<br/>
 
 **But we have no mutations!**  
 하지만 우리는 돌연변이가 없다!<br/>
 
 **There is no way for any individual to move to the right occasionally, to get useful information, and pass it to other individuals**  
 어떤 개체라도 우연히 오른쪽으로 이동해 유용한 정보를 얻고 그것을 다른 개체들에게 전달할 방법이 없다.<br/>
 
 **As we assumed, a population that is very close to the best solution, cannot find it. The population has fixed one of its genes, and is unable to change it without the mutation**  
 우리가 가정했듯, 최적 해에 매우 가까운 집단이라도 그것을 찾지 못할 수 있다. 집단은 하나의 유전자를 고정해버렸고, 돌연변이 없이는 그것을 바꿀 수 없다.<br/>

 <img src="https://github.com/user-attachments/assets/432a32c5-26d7-4b0d-87cf-6e414609a565" width="400" height="370"/> <br/>

 **Let’s go next to a population with positive mutation probability equal to 0.3**  
 이제 돌연변이 확률이 0.3인 양의 값을 가진 집단으로 넘어가 보자.<br/>

 <img src="https://github.com/user-attachments/assets/fb290dd0-5fae-440c-8c46-5eeeebe1cb12" width="800" height="348"/> <br/>

 **Finally, we see that population with positive mutation probability has found the best solution to the problem**  
 마침내, 돌연변이 확률이 양수인 집단이 문제의 최적 해를 찾아냈다는 것을 확인할 수 있다.<br/>

 <img src="https://github.com/user-attachments/assets/72b755ab-d2d8-4d3f-9212-b55cbae30e8e" width="400" height="367"/> <br/>

 **But is a large number of mutations always a good thing?**  
 하지만 돌연변이의 수가 많다고 항상 좋은 것일까?<br/>

 <img src="https://github.com/user-attachments/assets/14544ed5-8fe2-4575-866a-e00060fcc4b3" width="800" height="345"/> <br/>
 <img src="https://github.com/user-attachments/assets/47926e5c-92ef-4db1-b71b-cae8aa2171bc" width="400" height="369"/> <br/>

 **The evolution with very high mutation probability looks like a random search**  
 돌연변이 확률이 매우 높은 진화는 무작위 탐색처럼 보인다.<br/>
 
 **Every individual which has any positive information can be mutated afterward, losing the genetic data it had obtained**  
 어떤 유용한 정보를 가진 개체도 이후에 돌연변이를 통해 자신이 얻은 유전 정보를 잃어버릴 수 있다.<br/>
 
 **Mutation probability defines the degree of population deviations**  
 돌연변이 확률은 집단의 변이 정도를 결정한다.<br/>
 
 **It is almost impossible to find any solution to complex problems without the mutation mechanism**  
 돌연변이 메커니즘 없이는 복잡한 문제에 대한 어떤 해도 찾는 것이 거의 불가능하다.<br/>
 
 **On the other hand, too many frequent mutations disrupt the forward evolutionary movement, and leads the solution of the problem to a random search**  
 반면에, 너무 잦은 돌연변이는 진화의 전진적 움직임을 방해하고, 문제 해결을 무작위 탐색으로 이끌게 된다.<br/>



 

















  

