---
created: 2025-03-18
updated: 2025-03-21
dg-publish: true
craft: true
---

## p.1(Mutation)
  **Amutation is a random change in genes with the aim of improving an individual's ability to survive.**  
  돌연변이는 개체의 생존 능력을 향상시키기 위한 목적을 가진 유전자의 무작위 변화이다.<br/>

  **A mutation has no direction; it is a simple attempt at introducing a new feature that will give the future individual additional advantages.**  
  돌연변이는 방향이 없으며, 미래의 개체에 추가적인 이점을 줄 새로운 특성을 도입하려는 단순한 시도이다.<br/>

  **If you look at the history of evolution, it might seem that all mutations of species were strictly directed, and were extremely successful.**  
  진화의 역사를 보면, 모든 종의 돌연변이가 엄격하게 방향 지어졌고, 극히 성공적이었다고 생각할 수도 있다.<br/>

  **But this is not right.**  
  하지만 이는 옳지 않다.<br/>

  **An unsuccessful mutation makes an individual less viable due to which it cannot leave offspring, and therefore pass on its genes.**
  성공하지 못한 돌연변이는 개체를 덜 생존 가능하게 만들어 자손을 남길 수 없게 되며, 따라서 유전자를 전달할 수 없다.<br/>

  **Consequently, individuals and species with unsuccessful mutations do not exist for a long time, which means they do not leave a significant trace in the evolutionary chain.**
  결과적으로, 실패한 돌연변이를 가진 개체와 종은 오래 존재하지 않으며, 이는 진화 사슬에 중요한 흔적을 남기지 않음을 의미한다.<br/>
  
  **The mechanism of mutations is the driving force of evolution; it helps species to improve, as well as to adapt to environmental conditions**
  돌연변이의 메커니즘은 진화의 원동력이며, 종이 개선되고 환경 조건에 적응하는 데 도움을 준다.<br/>
<br/>
  ***

## p.3(Mutation method)
  **Random deviation mutation**
  무작위 편차 돌연변이<br/>
  
  **Exchange mutation**
  교환 돌연변이<br/>
  
  **Shift mutation**
  이동 돌연변이<br/>
  
  **Bit flip mutation**
  비트 반전 돌연변이<br/>
  
  **Inversion mutation**
  반전 돌연변이<br/>
  
  **Shuffle mutation**
  셔플 돌연변이<br/>
  
  **Fitness driven mutation**
  적합도 기반 돌연변이<br/>
<br/>
  ***

## p.4(Random deviation mutation)
  **Random deviation mutation is mainly applied to a real set of genes.**
  무작위 편차 돌연변이는 주로 실수 유전자 집합에 적용된다.<br/>
  
  **A random variable is added to the gene with a certain probability, usually with an average of 0**
  무작위 변수가 일정 확률로 유전자에 추가되며, 보통 평균값은 0이다.<br/>
  
  ![image](https://github.com/user-attachments/assets/e4051dc5-43ca-4a5f-b285-209b6de76f39)
<br/>
  ***

## p.5(Exchange mutation)
  **Mutation exchange is mainly applied to a binary or ordered set of genes.**
  교환 돌연변이는 주로 이진 또는 순서가 있는 유전자 집합에 적용된다.<br/>
  
  **A pair of genes are exchanged from randomly selected positions.**
  무작위로 선택된 위치에서 유전자 쌍을 교환한다.<br/>
  
  ![image](https://github.com/user-attachments/assets/42f71323-d10d-49dd-961f-540aaa9871e8)
<br/>
  ***

## p.6(Shift mutation)
  **Shift Mutation is moving a gene from a randomly selected position by a random number of positions to the left or right.**
  이동 돌연변이는 무작위로 선택된 위치에서 유전자를 무작위로 왼쪽 또는 오른쪽으로 일정 수의 위치만큼 이동시키는 것이다.<br/>
  
  **The content of all intermediate genes is shifted by one position.**
  모든 중간 유전자의 내용은 한 위치씩 이동된다.<br/>

  **This mutation method is applied to a binary or ordered set of genes.**
  이 돌연변이 방법은 이진 또는 순서가 있는 유전자 집합에 적용된다.<br/>

  ![image](https://github.com/user-attachments/assets/304f0f93-a7c2-41de-bca6-fdd938b7c55d)
<br/>

  **There are three different approaches of shift mutation implementation**
  이동 돌연변이 구현에는 세 가지 다른 접근 방식이 있다.<br/>
  
  - **Bounded shifting: This approach allows to shift gene without crossing gene list borders, that is, last element cannot shift to first, and vice versa.**
  경계 이동: 이 접근법은 유전자가 유전자 목록의 경계를 넘지 않도록 이동을 허용한다. 즉, 마지막 요소는 첫 번째로 이동할 수 없고, 그 반대도 마찬가지이다.<br/>
  
    - **In list [1,2,3,4,5] we can pick gene 3, and put it to position with index 0, and get the result [3,1,2,4,5].**
      리스트 [1,2,3,4,5]에서 유전자 3을 선택하여 인덱스 0의 위치로 이동시키면 결과는 [3,1,2,4,5]가 된다.<br/>
    
  - **Unbounded shifting: This approach allows to shift gene with crossing gene list borders.**
  비경계 이동: 이 접근법은 유전자가 유전자 목록의 경계를 넘어 이동할 수 있도록 허용한다.<br/>
  
    - **For example, in list [1,2,3,4,5], we can pick gene 3 and put it to position with index 0 and get the result [3,2,4,5,1].**
      예를 들어, 리스트 [1,2,3,4,5]에서 유전자 3을 선택하여 인덱스 0의 위치로 이동시키면 결과는 [3,2,4,5,1]이 된다.<br/>
<br/>
  ***

## p.8(Bit flip mutation)
  **This type of mutation is applied to the binary gene set.**
  이 유형의 돌연변이는 이진 유전자 집합에 적용된다.<br/>
  
  **Random gene is selected, and bit flipping is provoked, from 1 to 0 or from0 to 1.**
  무작위 유전자가 선택되어 비트 반전이 일어나며, 1에서 0으로 또는 0에서 1로 바뀐다.<br/>

  ![image](https://github.com/user-attachments/assets/cb7b37ff-aa32-4b61-9fd6-5e109345fe2f)
<br/>
  ***

## p.9(Inversion mutation)
  **Inversion mutation picks a random subrange and changes the order of the values in it**
  반전 돌연변이는 무작위 하위 범위를 선택하고 그 범위 내의 값들의 순서를 변경한다.<br/>
  
  **This mutation method is applied to a binary or ordered set of genes.**
  이 돌연변이 방법은 이진 또는 순서가 있는 유전자 집합에 적용된다.<br/>
  
  ![image](https://github.com/user-attachments/assets/eb3ca353-e6b2-4843-a844-5e5cddba2899)
<br/>

  **There are two different approaches of implementation of inversion mutation, which are as follows**
  반전 돌연변이 구현에는 두 가지 다른 접근 방식이 있으며, 다음과 같다:<br/>
  
  - **Unbounded subrange: This approach allows to select through the end subrange, in the list [1,2,3,4,5]; we can pick subrange with indices [3:1] as [4,5,1,2] and get the result [5,4,3,2,1].**
  비경계 하위 범위: 이 접근법은 하위 범위를 끝까지 선택할 수 있도록 허용한다. 예를 들어, 리스트 [1,2,3,4,5]에서 인덱스 [3:1]의 하위 범위 [4,5,1,2]를 선택하면 결과는 [5,4,3,2,1]이 된다.<br/>
  
  - **Bounded subrange: This approach doesn’t allow to go through the end, which means that the first index of a subrange is always lower than the last index of subrange.**
  경계 하위 범위: 이 접근법은 끝을 넘지 않도록 허용하며, 즉 하위 범위의 첫 번째 인덱스는 항상 마지막 인덱스보다 낮아야 한다.<br/>

## p.11(Shuffle mutation)
  **Shuffle mutation, like inversion mutation, picks a random subrange, but instead of changing the order of the values in it, it just shuffles the values.**
  셔플 돌연변이는 반전 돌연변이처럼 무작위 하위 범위를 선택하지만, 그 안의 값들의 순서를 변경하는 대신 단순히 값을 섞는다.<br/>
  
  **This mutation method is applied to a binary or ordered set of genes.**
  이 돌연변이 방법은 이진 또는 순서가 있는 유전자 집합에 적용된다.<br/>
  
  ![image](https://github.com/user-attachments/assets/78b709c9-0db8-49bf-89df-baae06cdd070)
<br/>
  ***

## p.12(Fitness driven mutation)
  **Fitness driven mutation, like the fitness driven crossover, is an approach that is trying to obtain only positive changes.**
  적합도 기반 돌연변이, 적합도 기반 교차와 마찬가지로, 오직 긍정적인 변화를 얻으려고 하는 접근법이다.<br/>
  
  **We run several mutations and pick the best one; if all mutations are worse than the original individual, then we leave the original without a mutation.**
  여러 번의 돌연변이를 실행하고 그 중 가장 좋은 것을 선택한다; 만약 모든 돌연변이가 원본 개체보다 더 나쁘다면, 원본은 돌연변이 없이 그대로 둔다.<br/>
  
  ![image](https://github.com/user-attachments/assets/867df55a-10e1-4da3-ab9f-f65a0cca5d69)
<br/>
  
  **NOTE: You have to make only a finite number of mutation tries. It is unacceptable to make an infinite loop trying to find any positive mutation.**
  참고: 돌연변이 시도는 유한한 횟수만 해야 한다. 긍정적인 돌연변이를 찾기 위해 무한 루프를 만드는 것은 용납되지 않는다.<br/>
  
  **Because there can be a situation when you’re trying to mutate the best individual, and each mutation makes it worse than it is now.**
  최고의 개체를 돌연변이시키려고 할 때, 각 돌연변이가 현재보다 더 나쁘게 만들 수 있는 상황이 있을 수 있기 때문이다.<br/>
  
  **Thus, your genetic algorithm will get stuck, trying to improve something that is already perfect.**
  따라서, 유전 알고리즘은 이미 완벽한 것을 개선하려고 시도하면서 멈추게 될 수 있다.<br/>
  
  **Following are the two different approaches of implementation of fitness driven mutation:**
  다음은 적합도 기반 돌연변이 구현의 두 가지 다른 접근 방식이다:<br/>

  - **Pick first positive: This approach generates mutations one by one, and stops when first positive mutation is found. This approach is better in terms of the algorithm speed.**
    첫 번째 긍정적인 돌연변이 선택: 이 접근법은 돌연변이를 하나씩 생성하고 첫 번째 긍정적인 돌연변이가 발견되면 멈춘다. 이 접근법은 알고리즘 속도 측면에서 더 효율적이다.<br/>
  
  - **Pick best positive: This approach generates all mutations, then picks the best one. This approach can improve population better but is worse in terms of the algorithm speed.**
    최고의 긍정적인 돌연변이 선택: 이 접근법은 모든 돌연변이를 생성한 후, 그 중 가장 좋은 것을 선택한다. 이 접근법은 개체군을 더 잘 개선할 수 있지만, 알고리즘 속도 측면에서는 더 나쁘다.<br/>
<br/>
  ***

## p.15(Mutation)
  **Just as in nature, in computational problems, the mutation is usually more important than crossing.**
  자연에서처럼, 계산 문제에서 돌연변이는 보통 교차보다 더 중요하다.<br/>
  
  **Yes, it is possible to construct successive GA algorithm architecture without crossing, but with a mutation.**
  교차 없이 돌연변이만 있는 연속적인 유전 알고리즘 아키텍처를 구성하는 것이 가능하다.<br/>
  
  **But architecture without mutation is impossible in principle.**
  하지만 돌연변이가 없는 아키텍처는 원칙적으로 불가능하다.<br/>
  
  **In the wild, some species reproduce themselves by simple cloning with mutation, and this approach ensures their development and survival.**
  자연에서 일부 종은 간단한 복제와 돌연변이를 통해 스스로 번식하며, 이 접근법은 그들의 발전과 생존을 보장한다.<br/>
<br/>
  ***

## p.16(Key terms)
  **Random deviation mutation: Addition of random variable to gene.**
  무작위 편차 돌연변이: 유전자에 무작위 변수를 추가하는 것.<br/>
  
  **Exchange mutation: Two genes are randomly selected, and their**
  교환 돌연변이: 두 개의 유전자가 무작위로 선택되고, 그들의 유전자가 교환된다.<br/>
  
  **values are exchanged.**
  값이 교환된다.<br/>
  
  **Shift mutation: Shifting random gene left or right.**
  이동 돌연변이: 무작위 유전자를 왼쪽이나 오른쪽으로 이동시키는 것.<br/>
  
  **Bit flip mutation: Changing the gene bit.**
  비트 반전 돌연변이: 유전자 비트를 변경하는 것.<br/>
  
  **Inversion mutation: Changing gene subrange order.**
  반전 돌연변이: 유전자 하위 범위의 순서를 변경하는 것.<br/>
  
  **Shuffle mutation: Shuffling gene values in gene subrange.**
  셔플 돌연변이: 유전자 하위 범위에서 유전자 값을 섞는 것.<br/>
<br/>
