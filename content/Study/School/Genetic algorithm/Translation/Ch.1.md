---
created: 2025-03-28
updated: 2025-03-28
dg-publish: true
---

## p.2(Genetic Algorithm= GA)
  **evolution is one of the most perfect adaptation mechanisms**  
  진화는 가장 완벽한 적응 메커니즘 중 하나이.<br/>

  **It is a way to achieve extraordinary and complex solutions**  
  이는 비범하고 복잡한 해결책을 달성하는 방법이다.<br/>

  **Understanding the principles of evolution gave us a new approach called genetic algorithms**  
  진화의 원리를 이해함으로써 우리는 유전 알고리즘이라는 새로운 접근법을 얻었다.<br/>

  **We will now explore this rather beautiful, simple, and effective approach to problem-solving**  
  이제 우리는 문제 해결을 위한 이 아름답고, 단순하며, 효과적인 접근 방식을 살펴볼 것이다.<br/>  
<br/>
  ***

## p.3(topics)
  **Nature of genetic algorithm**
  유전 알고리즘의 본질(또는 특성)<br/>
  
  **Applicability of genetic algorithms**
  유전 알고리즘의 적용 가능성(또는 적용 범위)<br/>
  
  **Pros and cons of genetic algorithms**
  유전 알고리즘의 장점과 단점<br/>
  
  **Your first genetic algorithm**
  당신의 첫 번째 유전 알고리즘<br/>
<br/>
  ***

## p.4(Nature of genetic algorithm)
  **Complex computational problems that are very difficult to solve by classical methods can now be solved by AI **
  고전적인 방법으로는 풀기 매우 어려운 복잡한 계산 문제들을 이제는 인공지능으로 해결할 수 있다.<br/>
  
  **One of the most powerful techniques to solve such complex problems is genetic algorithms (GA), which is based on the principle of an evolutionary approach**
  이러한 복잡한 문제를 해결하는 가장 강력한 기법 중 하나는 진화적 접근 원리에 기반한 유전 알고리즘(GA)이다.<br/>
<br/>
  ***

## p.5(Nature of genetic algorithm)
  **In the late 60s, American researcher J. Holland proposed to find solutions to optimization problems using methods and evolution models of animal populations in nature.**
  1960년대 후반, 미국의 연구자 J. Holland는 자연 속 동물 개체군의 방법과 진화 모델을 이용하여 최적화 문제의 해를 찾을 것을 제안했다.<br/>
  
  **Since the evolution’s basic laws were investigated and described by genetics, the proposed approach was called genetic algorithms.**
  진화의 기본 법칙들이 유전학에 의해 연구되고 설명되었기 때문에, 제안된 이 접근법은 유전 알고리즘이라 불리게 되었다.<br/>
  
  **GA is a randomly directed search algorithm based on mechanisms of natural selection and natural genetics**
  유전 알고리즘(GA)은 자연 선택과 자연 유전의 메커니즘에 기반한 무작위 지향 탐색 알고리즘이다.<br/>
  
  **It implements the principle of survival of the fittest, forming and changing the search algorithm based on evolutionary modeling.**
  유전 알고리즘은 '적자생존'의 원칙을 구현하며, 진화적 모델링을 기반으로 탐색 알고리즘을 구성하고 변화시킨다.<br/>
<br/>
  ***

## p.6(❖ Nature of genetic algorithm)
  **The basic steps in natural evolution**
  자연 진화의 기본 단계들<br/>
  - **Selection**
     선택<br/>
     
    - **According to Charles natural selection laws were formulated in the book On the Origin of Species**
      찰스 다윈에 따르면 자연 선택의 법칙은 『종의 기원』이라는 책에서 정립되었다.<br/>
      
    - **The central postulate is that individuals who can better solve problems, survive and reproduce more**
      중심 가설은 문제를 더 잘 해결할 수 있는 개체가 더 많이 살아남고 번식한다는 것이다.<br/>
      
    - **In GAs, each individual is a solution to some problem**
      유전 알고리즘(GA)에서 각 개체는 어떤 문제에 대한 하나의 해이다.<br/>
      
    - **According to this principle, individuals who solve the problem better have a greater chance of surviving and leaving offsprings**
      이 원리에 따르면, 문제를 더 잘 해결하는 개체는 생존하고 자손을 남길 가능성이 더 크다.<br/>
<br/>
  ***

## p.7(Nature of genetic algorithm)
  **The basic steps in natural evolution**
  자연 진화의 기본 단계들<br/>
  
  - **Crossover**
    교차<br/>
    
    - **This means that the offspring chromosome is made up of parts that are derived from the parents’ chromosomes**
      이는 자손 염색체가 부모 염색체로부터 유래된 부분들로 구성된다는 것을 의미한다.<br/>
      
    - **This principle was discovered in 1865 by G**
      이 원리는 1865년에 멘델(Gregor Mendel)에 의해 발견되었다.<br/>
<br/>
  ***

## p.8(Nature of genetic algorithm)
  **The basic steps in natural evolution**
  자연 진화의 기본 단계들<br/>

  - **Mutation**
    돌연변이<br/>
    
    - **In 1900, H. de Vries discovered the principle of random change**
      1900년, H. 드 프리스(H. de Vries)는 무작위 변화의 원리를 발견하였다.<br/>
      
    - **Initially, this term was used to describe significant changes in descendants’ properties that were not present in their parents**
      처음에는 이 용어가 부모에게는 존재하지 않았던 자손의 특성에서 나타나는 중요한 변화들을 설명하는 데 사용되었다.<br/>
     
    - **By analogy, genetic algorithms use a similar mechanism to change offspring’s properties, thereby increasing individuals’ diversity in a population**
      이와 유사하게, 유전 알고리즘은 자손의 특성을 변화시키는 유사한 메커니즘을 사용하여 개체군 내 개체들의 다양성을 증가시킨다.<br/>

## p.9(Nature of genetic algorithm)
  **Genetic algorithms have the following characteristics**
  유전 알고리즘은 다음과 같은 특성을 가진다.<br/>
  
  - **Easy to implement**
    구현이 간단하다.<br/>
    
  - **Used for a wide range of tasks**
    다양한 작업에 활용된다.<br/>
    
  - **They do not require any additional information about the nature of the problem**
    유전 알고리즘은 문제의 본질에 대한 추가적인 정보를 필요로 하지 않는다.<br/>

  - **Easy and convenient to parallelize**
    병렬 처리하기 쉽고 편리하다.<br/>
<br/>
  ***

## p.10(Applicability of genetic algorithms)
  **As a solution, the GA tries to find the extremum of some function that characterizes the quality of the solution to the problem**
  해결책으로서 유전 알고리즘은 문제에 대한 해의 품질을 나타내는 어떤 함수의 극값을 찾으려고 시도한다.<br/>
  
  **Generally, the GA does not guarantee that the solution found is the best of all that’s possible**
  일반적으로 유전 알고리즘은 찾아낸 해가 가능한 모든 해 중에서 최선이라는 것을 보장하지는 않는다.<br/>
  
  **Usually, this is not required, but it is only important that the found solution satisfies the meaning of the problem being solved**
  보통 이는 요구되지 않으며, 중요한 것은 찾아낸 해가 해결하려는 문제의 의미를 만족시키는 것이다.<br/>
<br/>
  ***

## p.11(Applicability of genetic algorithm)
  **The areas of application of Gas**
  유전 알고리즘(GA)의 적용 분야들<br/>
  
  - **Search for extremum of various functions**
    다양한 함수의 극값 탐색<br/>
    
  - **Finding the shortest paths (traveling salesman problem)**
    최단 경로 찾기 (외판원 문제)<br/>
    
  - **Combinatorial optimization**
    조합 최적화<br/>
    
  - **Tasks of placement and scheduling**
    배치 및 스케줄링 작업<br/>
    
  - **Automatic programming tasks**
    자동 프로그래밍 작업<br/>
    
  - **AI tasks (choosing the structure and parameters of artificial neural networks)**
    인공지능 작업 (인공신경망의 구조와 파라미터 선택)<br/>
    
  - **In real time scenarios, GAs are used to develop AI systems, like designing tasks for aircraft routes at airports, finding the optimal behavior of robots, problems of constructing investment portfolios, and so on**
    실시간 시나리오에서는, 유전 알고리즘이 AI 시스템 개발에 사용되며, 예를 들어 공항의 항공기 경로 설계, 로봇의 최적 행동 결정, 투자 포트폴리오 구성 문제 등에 활용된다.<br/>
<br/>
  ***

## p.12(Pros and cons of genetic algorithms)
  **The pros of genetic algorithms**
  유전 알고리즘의 장점<br/>
  
  - **A wide range of tasks to be solved**: GA is successfully applied in the following areas – combinatorial optimization, finance (portfolio optimization), machine learning (feature extraction, neural network hyper-parameter optimization), code-breaking, game theory, natural sciences, and so on.
    **해결 가능한 작업의 범위가 넓다**: 유전 알고리즘은 조합 최적화, 금융(포트폴리오 최적화), 머신러닝(특징 추출, 신경망 하이퍼파라미터 최적화), 암호 해독, 게임 이론, 자연 과학 등 다양한 분야에 성공적으로 적용된다.<br/>
 
  - **Ease of implementation**: The algorithm implies the presence of steps – natural selection, crossing, and mutation. This conceptual simplicity makes this method available to a wide range of developers
    **구현이 용이하다**: 이 알고리즘은 자연 선택, 교차, 돌연변이 등의 단계를 포함하며, 이러한 개념적 단순성은 이 방법을 다양한 개발자들이 사용할 수 있도록 만든다.<br/>
    
  - **Resistance to dynamic changes in problem conditions**: The GA is able to retrain if the conditions of the problem change when searching for a solution
    문제 조건의 동적 변화에 대한 저항성: 유전 알고리즘은 문제를 해결하는 과정에서 조건이 변경되더라도 다시 학습할 수 있는 능력을 가진다.<br/>
<br/>
  ***
  
## p.13(Pros and cons of genetic algorithms)
  - **The ability for self-adaptation**: GAs are able, after a certain period of evolution, to adapt to the conditions of the problem being solved
    **자기 적응 능력**: 유전 알고리즘은 일정한 진화 과정을 거친 후, 해결하고 있는 문제의 조건에 적응할 수 있는 능력을 가진다.<br/>

  - **Ease of scaling**: Can easily be used on big data where the data is spread over the distributed systems. GAs, as a highly parallel process, can be easily parallelized, which makes it possible to proportionally accelerate the finding of a solution with an increase in computing power.
    **확장 용이성**: 유전 알고리즘은 데이터가 분산 시스템에 퍼져 있는 빅데이터 환경에서도 쉽게 사용할 수 있다. GA는 높은 수준의 병렬 처리가 가능한 프로세스이기 때문에, 쉽게 병렬화할 수 있으며, 이는 컴퓨팅 성능이 증가함에 따라 해를 찾는 속도를 비례적으로 향상시킬 수 있게 한다.<br/>

  - **Solving problems for which there is no solution experience**: One of the biggest advantages of GAs is their ability to investigate problems for which there is no relevant solution experience. It should be noted that expert assessments are often used to solve difficult-to-formalize problems, but they sometimes give less acceptable solutions than automated methods
    **해결 경험이 없는 문제 해결**: 유전 알고리즘의 가장 큰 장점 중 하나는, 기존에 해결 경험이 없는 문제들을 탐색할 수 있는 능력이다. 형식화하기 어려운 문제들을 해결하기 위해 전문가의 판단이 종종 사용되지만, 때로는 자동화된 방법보다 덜 만족스러운 해를 제공할 수 있다는 점을 주목할 필요가 있다.<br/>
<br/>
  ***

## p.14(Pros and cons of genetic algorithms)
  **The cons of genetic algorithms**
  유전 알고리즘의 단점<br/>

  - **The complexity of representing an individual in a population and determining the fitness function**
    개체군 내 개체를 표현하고 적합도 함수를 정의하는 데에 복잡성이 존재한다.<br/>
    
  - **For real problems, it is initially not-at-all obvious in what form it is necessary to present a set of individual genes for a successful solution to the problem, and also determine the assessment of the quality of a particular individual.**
    실제 문제에서는, 문제를 성공적으로 해결하기 위해 개별 유전자의 집합을 어떤 형태로 표현해야 하는지가 처음부터 전혀 명확하지 않으며, 또한 특정 개체의 품질을 어떻게 평가할지도 결정해야 한다.<br/>
    
  - **The choice of parameters of the architecture of the GA**
    유전 알고리즘의 아키텍처에서 사용할 파라미터들을 선택해야 한다.<br/>
    
  - **There are no effective criteria for the termination of the algorithm**
    알고리즘을 종료하기 위한 효과적인 기준이 존재하지 않는다.<br/>
<br/>
  ***

## p.15(Pros and cons of genetic algorithms)
  - **Not effective for finding an extremum for smooth functions with one extremum.**
    하나의 극값만 가지는 매끄러운 함수에서 극값을 찾는 데에는 유전 알고리즘이 비효율적이다.<br/>
    
  - **They require large enough computing resources.**
    유전 알고리즘은 충분히 큰 계산 자원을 필요로 한다.<br/>
    
  - **When solving problems, there are cases of premature convergence, and therefore, generally, they do not guarantee in finding the global extremum**
    문제를 해결하는 과정에서 조기 수렴이 발생하는 경우가 있으며, 따라서 일반적으로 전역 극값을 찾는 것을 보장하지는 않는다.<br/>
<br/>

















    
