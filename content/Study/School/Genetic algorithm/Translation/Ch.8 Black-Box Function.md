---
created: 2025-04-13
updated: 2025-04-13
dg-publish: true
---

## p.1(Black-Box Function)
  **The most common task is to find the parameters at which a particular function reaches its maxima values**  
  가장 일반적인 과제는 특정 함수가 최대값에 도달하는 파라미터를 찾는 것이다.<br/>
  
  **Often these functions have a very complex analytical form, and sometimes nothing is known at all about the function itself, and it is represented as a black-box**  
  종종 이러한 함수는 매우 복잡한 해석적 형태를 가지며, 때때로 함수 자체에 대해 아무것도 알려져 있지 않고 블랙박스로 표현된다.<br/>
  
  **In this chapter, we will study the methods that help in finding values at which a certain function takes its maxima value.**  
  이 장에서는 특정 함수가 최대값을 갖는 지점을 찾는 데 도움이 되는 방법들을 살펴볼 것이다.<br/>
<br/>
  <hr>

## p.2(Structure)
  **What is black-box function**  
  블랙박스 함수란 무엇인가.<br/>
  
  **Gene encodings**  
  유전자 인코딩.<br/>
  
  **Genetic algorithm architecture**  
  유전 알고리즘 구조.<br/>
<br/>
  <hr>

## p.3(Objectives)
  **Get the understanding about what the black-box function is**  
  블랙박스 함수가 무엇인지에 대한 이해를 얻어라.<br/>
  
  **Explore ways to create individuals for various optimizable functions**  
  다양한 최적화 가능한 함수들을 위해 개체를 생성하는 방법들을 탐색하라.<br/>
  
  **Examine the most suitable genetic algorithm architectures for searching maxima of a black-box function**  
  블랙박스 함수의 최대값을 탐색하기에 가장 적합한 유전 알고리즘 구조들을 살펴보아라.<br/>
<br/>
  <hr>

## p.4(What is Black-box function?)
  **We often do not need to spend time on the long-term analytical, and mathematical study of a function**  
  우리는 종종 함수에 대한 장기적인 해석적, 수학적 연구에 시간을 들일 필요가 없다.<br/>
  
  **This study can take weeks, months, or even years**  
  이러한 연구는 몇 주, 몇 달, 심지어 몇 년이 걸릴 수도 있다.<br/>
  
  **We just need to find the parameters at which the value of the function is maxima**  
  우리는 단지 함수의 값이 최대가 되는 파라미터를 찾기만 하면 된다.<br/>
  
  **In this case, we can consider the function as some kind of black box that has some input parameters, and one output value**  
  이 경우 우리는 그 함수를 입력 파라미터와 하나의 출력 값을 가진 일종의 블랙박스로 간주할 수 있다.<br/>
  
  **We will call any function of several variables $f(x₁, x₂, …, xₙ)$ of unknown nature as a black box function**  
  우리는 여러 변수 $f(x₁, x₂, …, xₙ)$를 갖고 본질이 알려지지 않은 어떤 함수든 블랙박스 함수라고 부를 것이다.<br/>
  
  **As we mentioned earlier, there is a rich mathematical toolset for finding the maxima for classical differentiable functions**  
  앞서 언급했듯이, 고전적인 미분 가능한 함수의 최대값을 찾기 위한 풍부한 수학적 도구들이 존재한다.<br/>
  
  **It can be much more efficient than the use of genetic algorithms**  
  그것은 유전 알고리즘을 사용하는 것보다 훨씬 더 효율적일 수 있다.<br/>
  
  **There are some exceptions for complicated functions with boundary conditions in the form of differential equations; for finding the extrema of these functions, the use of genetic algorithms is reasonable**  
  경계 조건이 있는 복잡한 함수들(미분방정식 형태)의 경우에는 예외가 있으며, 이러한 함수들의 극값을 찾는 데에는 유전 알고리즘을 사용하는 것이 합리적이다.<br/>

  **Before finding the maxima of a function, it is sometimes necessary to make certain transformations**  
  함수의 최대값을 찾기 전에, 때때로 특정한 변환을 수행할 필요가 있다.<br/>

  **We always mention the search of the maxima of function f, but what if we need to find the minima of a function f?**  
  우리는 항상 함수 f의 최대값을 찾는 것에 대해 언급하지만, 만약 함수 f의 최소값을 찾아야 한다면 어떻게 해야 할까?<br/>
  
  **In this case, we are simply looking for the maxima of the function -f**  
  이 경우 우리는 단순히 함수 -f의 최대값을 찾는 것이다.<br/>
  
  **Hereinafter, we will consider only the search for the maxima**  
  이후로는 최대값을 찾는 경우만을 고려할 것이다.<br/>

  **Another detail worth mentioning is that you should always limit the range of values of an individual's genes in advance**  
  또 하나 언급할 가치가 있는 세부 사항은, 개체의 유전자 값의 범위는 항상 사전에 제한해야 한다는 것이다.<br/>
  
  **There should not be a situation where an individual's gene can take values in a range: $(-∞, +∞), (-∞, a] or [a, +∞)$**  
  개체의 유전자가 (-∞, +∞), (-∞, a], [a, +∞)와 같은 범위의 값을 가질 수 있는 상황은 없어야 한다.<br/>
  
  **This is done in order to limit the search range initially, and not allow the population to go beyond certain limits that do not need to be investigated a priori.**  
  이것은 탐색 범위를 초기에 제한하고, 사전에 조사할 필요가 없는 특정 한계를 넘어서는 것을 개체군이 허용하지 않도록 하기 위해 수행된다.<br/>
  
  **In order to not inject these restrictions on the operations of crossover and mutation, you can add range restrictions when initializing an individual:**  
  교차 및 돌연변이 연산에 이러한 제약을 주입하지 않기 위해, 개체를 초기화할 때 범위 제한을 추가할 수 있다.<br/>
<br/>
  <hr>

## p.8(Gene encodings)
  **Real encoding**  
  실수 인코딩.<br/>
  - **The simplest and most convenient way is when a gene is a real valued limited value**  
    가장 단순하고 편리한 방법은 유전자가 제한된 실수 값을 갖는 경우이다.<br/>
  
  - **These genes are convenient in that we can apply convenient methods of crossover, and mutation without modification**  
    이러한 유전자는 수정 없이도 편리한 교차 및 돌연변이 방법을 적용할 수 있다는 점에서 편리하다.<br/>

  - **These genes are the parameters for solving the problem, represented by the float type**  
    이러한 유전자들은 문제를 해결하기 위한 파라미터이며, float 타입으로 표현된다.<br/>
    
  **Discrete encoding**  
  이산 인코딩.<br/>
  
  - **Discrete encoding is used to represent finite linearly ordered sets**
    이산 인코딩은 유한한 선형 순서 집합을 표현하는 데 사용된다.<br/>
    
  - **For example: [-10, -9, -8, …, 10] or [0, 2, 4, …, 100]**
    예를 들어: [-10, -9, -8, …, 10] 또는 [0, 2, 4, …, 100].<br/>
    
  - **This type of set is used in many functions**
    이러한 유형의 집합은 많은 함수들에서 사용된다.<br/>

  - **For example, if we consider a function f(age, word_count) that returns the number of likes on Facebook made by the user aged “age”, and word_count is the number of words in a post that received a like**
    예를 들어, f(age, word_count)라는 함수가 사용자의 나이 "age"와, 좋아요를 받은 게시물의 단어 수 "word_count"를 입력으로 받아 Facebook에서 받은 좋아요 수를 반환한다고 가정해보자.<br/>
    
  - **For discrete encoded genes, we can use standard crossover and mutation operations with the selection of the most appropriate element in the set**
    이산 인코딩된 유전자에 대해서는, 집합 내에서 가장 적절한 요소를 선택하여 표준 교차 및 돌연변이 연산을 사용할 수 있다.<br/>
    
  - **It should be understood that with discrete gene encoding, the mutation mechanism works in gaps, and not smoothly, as in the case of realgene encoding**
    이산 유전자 인코딩의 경우, 돌연변이 메커니즘은 실수형 유전자 인코딩처럼 부드럽게 작동하는 것이 아니라, 불연속적인 간격으로 작동한다는 점을 이해해야 한다.<br/>
    
  - **This feature can eliminate the mutation at all**
    이러한 특성은 돌연변이를 완전히 제거해버릴 수도 있다.<br/>
    
  - **This is rather a common mistake in GA design.**
    이것은 유전 알고리즘 설계에서 꽤 흔한 실수이다.<br/>
    
  - **As we see, discrete individual is not mutated, because any random deviation cannot make any discrete shift of gene.**  
    보는 바와 같이, 이산 개체는 돌연변이되지 않는다. 왜냐하면 어떤 무작위 편차도 유전자의 이산적인 변화를 일으킬 수 없기 때문이다.<br/>
    <img src="https://github.com/user-attachments/assets/24ba6186-1896-4192-95fd-9c7108f069f3" width="500" height="233"/>

  **Enumeration encoding**  
  열거 인코딩.<br/>
  
  - **In some cases, a function can take input parameters that can be considered as enumeration**
    일부 경우에는 함수가 입력 파라미터로 열거형으로 간주할 수 있는 값을 받을 수 있다.<br/>
  
  - **For enumerated genes encoding we can use only uniform crossover, which changes values in parent genes**
    열거형 유전자 인코딩의 경우, 부모 유전자의 값을 변경하는 균등 교차만 사용할 수 있다.<br/>
    
  - **As a mutation, the function of a random choice of the value in the enumeration set can be used**  
    돌연변이로는 열거 집합 내의 값을 무작위로 선택하는 함수가 사용될 수 있다.<br/>
<br/>
  <hr>

## p.13(Genetic algorithm architecture)
  **Let's build the GA architecture that uses the previously discussed approaches**  
  앞서 논의한 접근 방식들을 사용하는 유전 알고리즘 구조를 구축해보자.<br/>
  
  **Since we have different types of genes in an individual, we need to determine the crossover and mutation for each gene separately**  
  개체 내에 서로 다른 유형의 유전자가 있기 때문에, 각 유전자에 대해 교차 및 돌연변이 연산을 별도로 결정할 필요가 있다.<br/>
  
  **We will use crossover based on blend crossover, and mutation based on random deviation**  
  개체 내에 서로 다른 유형의 유전자가 있기 때문에, 각 유전자에 대해 교차 및 돌연변이 연산을 별도로 결정할 필요가 있다.<br/>
<br/>
  <hr>

## p.14(Conclusion)
  **We have studied a very important aspect of the application of genetic algorithms**  
  우리는 유전 알고리즘 적용의 매우 중요한 측면을 살펴보았다.<br/>
  
  **Finding the maxima of complex and difficult to analyze functions is a very common task**  
  복잡하고 분석하기 어려운 함수의 최대값을 찾는 것은 매우 흔한 작업이다.<br/>
  
  **Of course, it should be kept in mind that genetic algorithms do not guarantee finding the global maxima, but nevertheless, they can be very useful when it is necessary to find any maxima in the foreseeable time**  
  물론 유전 알고리즘이 전역 최대값을 찾아준다는 보장은 없지만, 예측 가능한 시간 안에 어떤 최대값이라도 찾아야 할 필요가 있을 때 매우 유용할 수 있다는 점을 염두에 두어야 한다.<br/>
  
  **Such tasks are often encountered in the design of real-time systems.**  
  이러한 과제는 실시간 시스템 설계에서 자주 마주친다.<br/>
  
  **When the system may face the task of optimizing a completely unfamiliar function, it is necessary to find its maxima quickly**  
  시스템이 전혀 낯선 함수를 최적화해야 하는 상황에 직면할 수 있을 때, 그 함수의 최대값을 신속하게 찾아야 한다.<br/>
<br/>
