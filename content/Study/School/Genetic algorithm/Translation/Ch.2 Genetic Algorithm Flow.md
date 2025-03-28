---
created: 2025-03-28
updated: 2025-03-28
dg-publish: true
---

## p.1(evolution)
  **The modern understanding of evolution is based on the Darwin theory and genetics.**
  현대의 진화에 대한 이해는 다윈의 이론과 유전학에 기반하고 있다.<br/>
  
  **The mechanism of natural selection is known as the process of ensuring the stability and adaptation of species**
  자연 선택의 메커니즘은 종의 안정성과 적응을 보장하는 과정으로 알려져 있다.<br/>
  
  **Strong and viable individuals survive, leaving offspring, to whom their characteristics are passed on**
  강하고 생존력 있는 개체들이 살아남아 자손을 남기며, 그 특성은 자손에게 전달된다.<br/>
  
  **Weak individuals, on the contrary, perish without participating in reproduction.**
  반대로, 약한 개체들은 번식에 참여하지 못한 채 사라진다.<br/>
<br/>
  ***

## p.2(topics)
  **Individual**
  개체군<br/>
  
  **Fitness function**
  적합도 함수<br/>
  
  **Population**
  개체군<br/>
  
  **Selection**
  선택<br/>
  
  **Crossover**
  교차<br/>
  
  **Mutation**
  돌연변이<br/>
  
  **Genetic algorithm flow**
  유전알고리즘 흐름<br/>
<br/>
  ***

## p.3(Individual)
  **An individual is an object that represents a solution to a problem.**
  개체는 문제에 대한 해를 나타내는 객체이다.<br/>
  
  **The response parameters are determined by the genes that are contained in the individual.**
  반응 파라미터는 개체 안에 포함된 유전자들에 의해 결정된다.<br/>

  **Usually, there are two ways to create individuals**
  일반적으로 개체를 생성하는 방법에는 두 가지가 있다.<br/>
  
  - **Random generation of an individual**
    개체의 무작위 생성<br/>.
    
  - **Creating an individual with a specified set of genes**
    지정된 유전자 집합으로 개체 생성<br/>.
<br/>
  ***

## p.4( Fitness function)
  **The fitness function is equivalent to the natural concept of the fitness of a living organism**
  적합도 함수는 살아있는 유기체의 적합도라는 자연적 개념과 동일하다.<br/>
  
  **This function characterizes how well an individual is adapted to the environment.**
  이 함수는 개체가 환경에 얼마나 잘 적응했는지를 특징짓는다.<br/>
  
  **Depending on the problem to be solved, the best individual is considered to be the one whose objective function is maxima or minima.**
  해결해야 할 문제에 따라, 최적의 개체는 목표 함수가 최대값 또는 최소값인 개체로 간주된다.<br/>

  **For our problem of finding the maxima of $sin (x) - 0.5 |x|$, the best individual will be the one with the maxima fitness function**
  $sin(x)−0.5∣x∣$의 최대값을 찾는 문제에서, 최적의 개체는 최대값을 갖는 적합도 함수를 가진 개체가 될 것이다.<br/>
<br/>
  ***

## p.5(Population)
  **A population is just a set of individuals.**
  개체군은 단지 개체들의 집합이다.<br/>
  
  **When we say that we are creating a random population, it means that we are simply creating a certain number of random individuals**
  우리가 무작위 개체군을 만든다고 말할 때, 그것은 단지 일정 수의 무작위 개체를 생성하는 것을 의미한다.<br/>
  
  **For each population, the following characteristics can be obtained**
  각 개체군에 대해 다음과 같은 특성을 얻을 수 있다:<br/>
  - **Best individual**: The best individual is the individual that has the maximum fitness function value.
    **최고의 개체**: 최고의 개체는 최대 적합도 함수 값을 가진 개체이다.<br/>
    
  - **Best fitness**: The best fitness is the value fitness function that the best individual has.
    **최고 적합도**: 최고 적합도는 최고의 개체가 가진 적합도 함수 값이다.<br/>
  - **Average fitness**: The average fitness value is the average fitness function value for all individuals in the population
    **평균 적합도**: 평균 적합도 값은 개체군에 있는 모든 개체들의 적합도 함수 값의 평균이다.<br/>
<br/>
  ***

## p.6(Selection)
  **Selection is necessary to select more adapted individuals for crossing.**
  선택은 교차를 위해 더 잘 적응된 개체들을 선택하는 데 필요하다.<br/>
  
  **NOTE: Selection is the first genetic operation to be performed on a population. As a result of selection, the individuals that are selected will participate in the process of generating a new population.**
  참고: 선택은 개체군에 대해 수행되는 첫 번째 유전 연산이다. 선택의 결과로 선택된 개체들은 새로운 개체군을 생성하는 과정에 참여하게 된다.<br/>
  
  **Selection itself does not generate the new population; it is only responsible for selecting individuals that can leave the offspring.**
  선택 자체는 새로운 개체군을 생성하지 않는다; 그것은 오직 자손을 남길 수 있는 개체들을 선택하는 역할만 한다.<br/>
  
  **As an example, consider tournament selection, where one must choose three different random individuals from the population, and from these three, they choose the best one.**
  예를 들어, 토너먼트 선택을 고려해보자. 여기서 개체군에서 세 개의 서로 다른 무작위 개체를 선택한 후, 이들 중에서 가장 좋은 개체를 선택한다.<br/>
<br/>
  ***

## p.7(Crossover)
  **Crossover is the process of generating new offspring**
  교차는 새로운 자손을 생성하는 과정이다.<br/>
  
  **The main purpose of crossover is the exchange of genetic information, and to transfer the accumulated experience to the offspring.**
  교차의 주요 목적은 유전 정보를 교환하고, 축적된 경험을 자손에게 전달하는 것이다.<br/>
  
  **The child should not be very different from the parents.**
  자손은 부모와 너무 다르지 않아야 한다.<br/>
<br/>
  ***

## p.8(Mutation)
  **Mutation is a random change that an individual's genes undergo.**
  돌연변이는 개체의 유전자가 겪는 무작위 변화이다.<br/>
  
  **Mutation is the factor that drives the development of evolution.**
  돌연변이는 진화의 발전을 이끄는 요인이다.<br/>
  
  **Each child contains something that neither of his parents has.**
  각 자손은 그의 부모 중 누구도 가지지 않은 것을 포함하고 있다.<br/>
  
  **Mutation is the most important factor in evolution, which allows you to find new solutions.**
  돌연변이는 진화에서 가장 중요한 요인으로, 새로운 해를 찾을 수 있게 해준다.<br/>
  
  **If the trees begin to grow taller, then a child of a horse, whose neck is slightly longer than its parents, will be able to find food for itself more easily, which means it will be more adapted to life and will be able to pass on this feature to its offspring. This is exactly how, by accumulating positive mutations from generation to generation, a horse can evolve into a giraffe.**
  만약 나무들이 더 자라기 시작하면, 목이 부모보다 조금 더 긴 말의 자손은 스스로 음식을 더 쉽게 찾을 수 있게 되어, 이는 생명에 더 잘 적응하게 되고 이 특성을 자손에게 전달할 수 있게 된다. 바로 이런 방식으로, 세대를 거쳐 긍정적인 돌연변이가 축적되면서 말은 기린으로 진화할 수 있다.<br/>
<br/>
  ***

## p.9(Genetic Algorithm Flow)
  ![image](https://github.com/user-attachments/assets/106948a9-6ca6-4a43-8cba-11cd6c5d21b8)
<br/>
  ***
  
## p.10(conditions for stopping)
  **There are various conditions for stopping the GA, for example**
  유전 알고리즘을 종료하기 위한 다양한 조건이 있다, 예를 들어:<br/>
  
  - **Finding an acceptable solution**
    수용 가능한 해를 찾는 것<br/>
    
  - **Reaching a certain number of generations**
    특정 세대 수에 도달하는 것<br/>






