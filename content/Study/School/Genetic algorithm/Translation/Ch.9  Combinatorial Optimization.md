---
created: 2025-04-25
updated: 2025-04-25
dg-publish: true
---

## p.1(Combinatorial Optimization – Binary Gene Encoding)
  **A combinatorial problem is a problem in which you need to find the best combination of some objects that gives the best result**  
  조합 문제란 어떤 객체들의 조합 중에서 최상의 결과를 주는 최적의 조합을 찾아야 하는 문제이다.<br/>
  
  **Combinatorial optimization problems are often complicated to be solved analytically**  
  조합 최적화 문제는 종종 해석적으로 풀기 어렵다.<br/>
  
  **Genetic algorithms are a very suitable method for solving combinatorial optimization problems**  
  유전 알고리즘은 조합 최적화 문제를 해결하는 데 매우 적합한 방법이다.<br/>
  
  **We will explore how GAs can solve problems without deep-diving into the specifics of the problem**  
  우리는 문제의 세부 사항을 깊이 파고들지 않고도 유전 알고리즘이 어떻게 문제를 해결할 수 있는지 살펴볼 것이다.<br/>
  
  **Let's consider the simplest example of a combinatorial optimization problem**  
  가장 간단한 조합 최적화 문제의 예를 살펴보자.<br/>

  **Suppose we have the following product list:**  
  다음과 같은 제품 목록이 있다고 가정해보자.<br/>
    - Chocolate (546 calories)  
    - Tomato (20 calories)  
    - Apple (52 calories)  
    - Cookies (502 calories)  
    - Bread (265 calories)  
    
  **And we need to choose the three lowest calorie items**  
  그리고 우리는 칼로리가 가장 낮은 세 가지 항목을 선택해야 한다.<br/>
  
  **The combination of these three products will be the solution to the combinatorial optimization problem**  
  이 세 가지 제품의 조합이 바로 조합 최적화 문제의 해가 된다.<br/>
  
  **Combinatorial problems are usually much more complicated than the one we gave in the example**  
  조합 문제는 일반적으로 우리가 예시로 든 문제보다 훨씬 더 복잡하다.<br/>
  
  **In this chapter, we will cover different combinatorial problems, the solution to which is a sequence of zeros or ones, and give intuition on how to solve them**  
  이 장에서는 해가 0과 1의 시퀀스로 표현되는 다양한 조합 문제들을 다루고, 이를 해결하는 직관을 제공할 것이다.<br/>
<br/>
  <hr>
  
## p.4(Structure)
  **Knapsack problem**  
  배낭 문제<br/>
  
  **Schedule problem**  
  일정 문제<br/>
  
  **Radar placement problem**  
  레이더 배치 문제<br/>
<br/>
  <hr>

## p.5(Objectives)
  **To give examples of combinatorial problems**  
  조합 문제의 예를 제시하기 위해서.<br/>
  
  **To understand how genetic algorithm solves them**  
  유전 알고리즘이 이러한 문제들을 어떻게 해결하는지 이해하기 위해서.<br/>
  
  **To define an architecture of genetic algorithm for combinatorial problems**  
  조합 문제를 위한 유전 알고리즘의 구조를 정의하기 위해서.<br/>
<br/>
  <hr>

## p.6(Knapsack problem)
  **The knapsack problem is a classic combinatorial optimization problem**  
  배낭 문제는 고전적인 조합 최적화 문제이다.<br/>
  
  **The challenge is as follows**  
  문제는 다음과 같다.<br/>
    - we have a knapsack with a capacity of 15kg, and  
      우리는 15kg 용량의 배낭을 가지고 있고,<br/>
    - we have many different items with different weights and costs  
      서로 다른 무게와 가격을 가진 다양한 항목들이 있다.<br/>
      
  **We have to select such things in a knapsack so that their price is maximum and, at the same time, does not exceed the capacity of the knapsack**  
  배낭에 담을 항목들을 선택하되, 가격이 최대가 되면서 동시에 배낭의 용량을 초과하지 않도록 해야 한다.<br/>
  
  **For knapsack problem, the individual has the following binary gene set encoding:**  
  배낭 문제에서 개체는 다음과 같은 이진 유전자 집합 인코딩을 가진다.<br/>
  
  **1 - include item, 0 - exclude item**  
  1 - 항목 포함, 0 - 항목 제외<br/>
    <img src="https://github.com/user-attachments/assets/f039cf98-6124-46a2-9fe1-c9e37a5a31a6" width="500" height="258"/>
  <br/>

  **Each individual represents a specific combination of things that should be put in a backpack**  
  각 개체는 배낭에 넣어야 할 특정 항목 조합을 나타낸다.<br/>
  
  **Fitness function is the total value of all items that are included in the combination**  
  적합도 함수는 조합에 포함된 모든 항목들의 총 가치를 의미한다.<br/>
    <img src="https://github.com/user-attachments/assets/a827a2c7-9f47-480e-9d9c-63725bb33774" width="500" height="191"/>

  **Let’s design an architecture, and test GA solving knapsack problem**  
  유전 알고리즘 구조를 설계하고, 배낭 문제를 해결하는 것을 시험해보자.<br/>
    <img src="https://github.com/user-attachments/assets/fdde9c53-1e49-493b-bd72-e1e997484be1" width="325" height="400"/>
    <img src="https://github.com/user-attachments/assets/be7648cb-2ee3-4fa5-93e6-1194e8d2dc3f" width="450" height="335"/>
    - Solving Knapsack Problem Evolution Progress
      배낭 문제 해결의 진화 진행 상황.<br/>

  **Well, not bad, but there is one more improvement in our algorithm.**  
  괜찮지만, 우리의 알고리즘에는 한 가지 더 개선할 점이 있다.<br/>
  
  **As you can see, any individual who is close to maximum capacity can be destroyed very easily**  
  보다시피, 최대 용량에 가까운 어떤 개체든 매우 쉽게 파괴될 수 있다.<br/>
  
  **The addition of any inappropriate item can set fitness function to zero**  
  부적절한 항목 하나가 추가되면 적합도 함수가 0이 되어버릴 수 있다.<br/>
  
  **To check this hypothesis, we will take the best individual from the previous example, and make 1000 mutations on it, and then will check how many mutations have killed the best individual**  
  이 가설을 확인하기 위해, 우리는 이전 예제에서 가장 좋은 개체를 선택하고 그것에 대해 1000번의 돌연변이를 수행한 뒤, 얼마나 많은 돌연변이가 그 최적 개체를 파괴했는지를 확인할 것이다.<br/>
    <img src="https://github.com/user-attachments/assets/8778f864-33af-48a8-b53b-e116a431229c" width="450" height="321"/>
      - Results of Bit Flip Mutation of Best Individual
        최적 개체에 대한 비트 플립 돌연변이의 결과.<br/>

  **Only 5% of mutations keep the best individual alive**  
  돌연변이 중 오직 5%만이 최적 개체를 살아남게 한다.<br/>
  
  **The rest of the mutations kill the individual, thereby excluding it from the population, and thereby erasing all the useful information that this individual carried**  
  나머지 돌연변이들은 그 개체를 파괴하여 개체군에서 제외시키고, 그 개체가 가지고 있던 모든 유용한 정보를 지워버린다.<br/>
  
  **It is not difficult to conclude that a similar situation occurs with crossover**  
  비슷한 상황이 교차 연산에서도 발생한다는 결론을 내리는 것은 어렵지 않다.<br/>
  
  **Any crossing is capable of producing non-viable offspring**  
  어떤 교차 연산도 생존 불가능한 자손을 만들어낼 수 있다.<br/>
  
  **NOTE: The feature of fast destructibility of individuals is natural in all discrete optimization problems. It is obvious that a change in one value of one gene can completely change the value of a fitness function**  
  주의: 개체가 빠르게 파괴되는 특성은 모든 이산 최적화 문제에서 자연스러운 현상이다. 하나의 유전자 값이 변경되면 적합도 함수의 값이 완전히 바뀔 수 있다는 것은 명백하다.<br/>

  **Let’s change our GA architecture:**  
  우리의 유전 알고리즘 구조를 변경해보자.<br/>
    - From one-point crossover to fitness driven one-point crossover  
      단일 지점 교차에서 적합도 기반 단일 지점 교차로 변경하자.<br/>
    - From bit flip mutation to fitness driven bit flip mutation  
      비트 플립 돌연변이에서 적합도 기반 비트 플립 돌연변이로 변경하자.<br/>

  **What we did was to protect individuals from unsuccessful crossings and mutations**  
  우리가 한 것은 개체들을 실패한 교차와 돌연변이로부터 보호하는 것이었다.<br/>

  **Let's see the performance of our algorithm after the changes made**  
  구조 변경 후 우리의 알고리즘 성능을 살펴보자.<br/>
    <img src="https://github.com/user-attachments/assets/a959ed9e-2002-4a93-b07c-0f4f96b6167d" width="450" height="333"/>
  <br/>
  
  **As we can see, this architecture converges to the solution faster, and the fitness function of the solution is higher than that of the previous architecture**  
  보다시피, 이 구조는 더 빠르게 해에 수렴하며, 해의 적합도 함수 값도 이전 구조보다 더 높다.<br/>
  
  **But of course, we understand that one architecture test cannot be a reliable proof for one architecture being better than another**  
  하지만 물론, 하나의 아키텍처 테스트만으로 어떤 구조가 다른 구조보다 더 낫다고 신뢰할 수 있는 증거가 되지는 않는다.<br/>
  
  **Compare two different architectures using the Monte-Carlo simulation method**  
  몬테카를로 시뮬레이션 기법을 사용하여 두 가지 다른 구조를 비교하라.<br/>
    <img src="https://github.com/user-attachments/assets/dfdc0ffa-83f5-422f-a77f-2ef6fe566b1a" width="450" height="333"/>
  <br/>

  **As we expected, the improved version of the GA gives a 25% better fitness result for the same number of individuals**  
  예상했던 대로, 개선된 버전의 유전 알고리즘은 같은 개체 수 조건에서 25% 더 높은 적합도 결과를 제공한다.<br/>
  
  **The knapsack problem can be easily extended for more sophisticated problems and conditions**  
  배낭 문제는 더 복잡한 문제와 조건으로 쉽게 확장할 수 있다.<br/>
  
  **For example, if we need to compose the most nutritious diet for a certain amount of money, and diet should include a certain amount of proteins, fats and carbohydrates, then we will have three more boundary conditions in addition to the condition for the cost of products, which is similar to the capacity condition in the knapsack problem**  
  예를 들어, 일정 금액 안에서 가장 영양가 높은 식단을 구성해야 하고, 그 식단에 단백질, 지방, 탄수화물이 각각 일정량 포함되어야 한다면, 이는 제품 가격에 대한 조건(배낭 문제의 용량 조건과 유사) 외에 세 가지 경계 조건이 추가되는 것이다.<br/>
<br/>
  <hr>

## p.19(Schedule problem)
  **Another combinatorial optimization problem that we will study is the schedule problem**  
  우리가 공부할 또 다른 조합 최적화 문제는 일정(schedule) 문제이다.<br/>

  **In this task, there is a certain number of workers and requirements for their work schedule; it is necessary to select a work schedule that will satisfy all the requirements**  
  이 과제에서는 일정 수의 작업자들과 그들의 근무 일정에 대한 요구사항들이 주어지며, 이 모든 요구사항을 만족시키는 근무 일정을 선택해야 한다.<br/>
  
  **Here is an example of a schedule with the following inputs** 
  다음은 다음과 같은 입력값을 가진 일정의 예시이다.<br/>
    - 7 working days  
      7일간의 근무일<br/>
    - 4 workers  
      4명의 작업자<br/>
    - A worker cannot work for more than two days in a row
      작업자는 연속으로 이틀 이상 근무할 수 없다.<br/>
    - One worker only works on Sundays
      한 작업자는 일요일에만 근무한다.<br/>
      <img src="https://github.com/user-attachments/assets/4495dbc7-5b41-4a54-b6f6-850fb8335b1b" width="500" height="209"/>
  <br/>

  **This schedule is not difficult to construct**  
  이 일정은 구성하기 어렵지 않다.<br/>
  
  **But let's look at more complex conditions:**  
  하지만 더 복잡한 조건들을 살펴보자.<br/>
    - 7 working days and 3 shifts per day – morning, midday, and evening shift  
      7일간의 근무일과 하루에 3개의 근무조 – 오전, 중간, 그리고 저녁 근무조.<br/>
    - 5 workers  
      5명의 작업자.<br/>
    - In the morning, there should be at least 1, and maximum 4 workers  
      오전 근무조에는 최소 1명, 최대 4명의 작업자가 있어야 한다.<br/>
    - In the midday, there should be at least 2, and maximum 5 workers  
      중간 근무조에는 최소 2명, 최대 5명의 작업자가 있어야 한다.<br/>
    - In the evening, there must be at least 1, and maximum 2 workers  
      저녁 근무조에는 최소 1명, 최대 2명의 작업자가 있어야 한다.<br/>
    - After the morning and afternoon shifts, the worker must rest for at least one shift, that is, one cannot work in a row, morning and afternoon, or day and evening  
      작업자는 오전 근무 또는 오후 근무 후에는 최소 한 번의 근무조 동안 휴식을 취해야 하며, 즉 연속으로 오전과 오후, 또는 오후와 저녁 근무를 할 수 없다.<br/>
    - After the evening shift, the worker must rest for a day, that is, not work on any of the next day’s shifts  
      저녁 근무 후에는 작업자가 하루 동안 휴식을 취해야 하며, 즉 다음 날의 어떤 근무조에도 근무할 수 없다.<br/>

  **Well, this problem is no longer so easy to solve**  
  이제 이 문제는 그렇게 쉽게 해결할 수 있는 문제가 아니다.<br/>
  
  **There are more than 2100 different schedule variations, and it is clear that we cannot solve this problem by brute force**  
  2100개 이상의 서로 다른 일정 조합이 있으며, 이 문제를 무차별 대입법으로 해결할 수는 없다는 것이 분명하다.<br/>

  **The binary construction of day shifts for an employee**  
  직원의 하루 근무조를 이진 구조로 표현하기.<br/>
    <img src="https://github.com/user-attachments/assets/43524af7-e785-4ca1-a276-5a9c8dc83ebb" width="500" height="209"/><br/>
  <br/>

  **So, the whole schedule for one worker can be represented in such a way**  
  따라서 한 작업자의 전체 근무 일정은 이러한 방식으로 표현할 수 있다.<br/>
    - 1,0,0  0,0,1  1,1,0  0,0,0  0,1,0  1,0,0  1,0,0<br/>
    <img src="https://github.com/user-attachments/assets/566408b6-ce22-4560-acb2-356832a100c4" width="281" height="500"/>
  <br/>

  **And the whole schedule for all workers can be represented**  
  그리고 모든 작업자의 전체 근무 일정은 표현될 수 있다.<br/>
  
  **So, we see that the schedule can be represented as a sequence of 105 ones and zeros**  
  따라서 우리는 이 근무 일정이 105개의 1과 0의 시퀀스로 표현될 수 있음을 알 수 있다.<br/>
    <img src="https://github.com/user-attachments/assets/799778bb-af10-4d79-9b65-0f8b2912d964" width="500" height="209"/>
  <br/>
    <img src="https://github.com/user-attachments/assets/1b246505-c7d6-471b-bf2e-dad1ed6fa222" width="500" height="209"/>
  <br/>

  **And so, we have determined the binary structure of the working schedule, and implemented the genotype of the individual population**  
  이와 같이 우리는 근무 일정의 이진 구조를 정의하고, 개체 집단의 유전자형을 구현하였다.<br/>
  
  **But now the questions arise**  
  하지만 이제 몇 가지 의문이 생긴다.<br/>
    - What will be the fitness function for the individual?  
      개체의 적합도 함수는 무엇이 될 것인가?<br/>
    - How to compare two individuals and understand that one of them is better than the other?  
      두 개체를 어떻게 비교하고, 그중 하나가 다른 하나보다 더 낫다고 판단할 수 있을까?<br/>

  **To solve this problem, we will take the following approach**  
  이 문제를 해결하기 위해, 우리는 다음과 같은 접근 방식을 취할 것이다.<br/>
    - We will calculate the penalty points for each graph  
      우리는 각 그래프에 대한 페널티 점수를 계산할 것이다.<br/>
    - The more violations and deviations from the rules that the schedule contains, the more penalty points it will be awarded  
      일정에 규칙 위반과 편차가 많을수록, 더 많은 페널티 점수가 부여될 것이다.<br/>
    - According to this logic, an individual with a fitness function equal to 0 will be the solution to our problem  
      이 논리에 따르면, 적합도 함수 값이 0인 개체가 우리 문제의 해(solution)가 될 것이다.<br/>
      
  **NOTE: Obviously, the schedule problem contains quite a lot of solutions. Only one representative of this set has to be found**  
  주의: 분명히, 일정 문제에는 상당히 많은 해가 존재한다. 이 집합의 대표적인 하나만 찾으면 된다.<br/>
  
  **A schematic of an evolutionary search might look like as shown in the following figure**  
  진화적 탐색의 개요는 다음 그림과 같이 보일 수 있다.<br/>
    <img src="https://github.com/user-attachments/assets/566408b6-ce22-4560-acb2-356832a100c4" width="450" height="241"/>
  <br/>

  **First condition**  
  첫번째 조건
    - minimum and maximum presence  
      최소 및 최대 참석.<br/>
    - We have to impose minimum and maximum shift attendance conditions  
    우리는 최소 및 최대 근무조 참석 조건을 부여해야 한다.<br/>
    - If we have a maximum of two employees in the evening, and the schedule indicates 4, then the schedule receives two penalty points
      저녁 근무조에 최대 2명의 직원이 배치되어야 하는데, 일정에 4명이 배치되었다면, 그 일정은 두 개의 페널티 점수를 받는다.<br/>
    - And we will add the condition that the absence of anyone on the shift is completely unacceptable, and we will immediately add 100 penalty points in case of such an event,  
      그리고 근무조에 아무도 배치되지 않는 것은 완전히 용납할 수 없다는 조건을 추가하고, 이런 일이 발생하면 즉시 100개의 페널티 점수를 추가한다.<br/>

  **Second condition**
  두번째 조건
    - rest after shifts  
      교대 근무 후 휴식.<br/>
    - Each employee should rest for the allotted time after the shift  
      각 직원은 근무조 후 정해진 시간만큼 휴식을 취해야 한다.<br/>
    - If the employee left the shift without resting for the allotted time, then one penalty point is charged,  
      직원이 정해진 시간만큼 휴식을 취하지 않고 근무조를 떠나면, 하나의 페널티 점수가 부과된다.<br/>
      
  **Let us assume that violation of labor standards is much worse than incomplete staffing of a shift**  
  노동 기준 위반이 근무조의 직원 배치가 불완전한 것보다 훨씬 더 심각하다고 가정하자.<br/>
  
  **Penalty points that an individual received for the lack of an individual are much more significant than penalty points for the rules of attendance shift**  
  개체가 개별 직원 부족으로 받은 페널티 점수는 근무조 참석 규칙 위반으로 받은 페널티 점수보다 훨씬 더 중요하다.<br/>
  
  **Then: fitness function = - (5 × rest penalty + presence penalty)**  
  그러면: 적합도 함수 = - (5 × 휴식 페널티 + 참석 페널티)<br/>
  
  **As we have already noticed, the schedule problem differs from others such that we can definitely understand that we have found the best solution**  
  우리가 이미 알아차린 것처럼, 일정 문제는 다른 문제들과 달리 우리가 최적의 해를 찾았다는 것을 확실히 알 수 있다는 점에서 다르다.<br/>
  
  **In the problems that we studied before, the probability of finding a better solution remained for each generation**  
  우리가 이전에 공부한 문제들에서는, 각 세대마다 더 나은 해를 찾을 확률이 남아 있었다.<br/>
  
  **But here, in the case of finding an individual with a fitness function equal to 0, we can immediately stop the search**  
  하지만 여기에서는 적합도 함수 값이 0인 개체를 찾으면 즉시 탐색을 멈출 수 있다.<br/>
  
  **so we will add this stop condition to the architecture of our algorithm.**  
  그래서 우리는 이 종료 조건을 알고리즘 구조에 추가할 것이다.<br/>
    <img src="https://github.com/user-attachments/assets/74ab60d8-2c5f-495f-bd70-98bd4b916d72" width="400" height="360"/>
  <br/>
    <img src="https://github.com/user-attachments/assets/03134ff0-2790-4ead-bdb3-442ff6a4a343" width="800" height="339"/>
  <br/>
    <img src="https://github.com/user-attachments/assets/03134ff0-2790-4ead-bdb3-442ff6a4a343" width="450" height="331"/>
  <br/>

  **As you can see in the preceding figure at the beginning, the algorithm converges quite quickly, but it spends quite a lot of time to overcome the last step**  
  앞선 그림에서 볼 수 있듯이, 알고리즘은 처음에는 꽤 빠르게 수렴하지만, 마지막 단계를 넘는 데에는 꽤 많은 시간이 소요된다.<br/>
  
  **Congratulations! We have built a general mechanism for solving a very complex problem**  
  축하합니다! 우리는 매우 복잡한 문제를 해결하기 위한 일반적인 메커니즘을 구축했습니다.<br/>
  
  **As you can see from the implementation, we can choose any number of employees, the duration of the work cycle, rest restrictions, and so on**  
  구현을 통해 알 수 있듯이, 우리는 직원 수, 작업 주기의 지속 시간, 휴식 제한 사항 등을 자유롭게 선택할 수 있다.<br/>
  
  **We can also add different conditions, such as different shift wages for workers, and minimize costs when drawing up a work schedule**  
  우리는 또한 직원에 대한 다른 근무조 임금을 설정하거나, 근무 일정을 작성할 때 비용을 최소화하는 등의 다양한 조건을 추가할 수 있다.<br/>

## p.38(Radar placement problem)




  
