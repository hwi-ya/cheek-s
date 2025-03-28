![image](https://github.com/user-attachments/assets/4bb35cc7-29d9-456b-8ed2-2beb505a939e)---
created: 2025-03-28
updated: 2025-03-28
dg-publish: true
---

## p.1(Crossover)
  **Crossover is the process of forming new individuals from existing individuals while maintaining traits.**<br>
  교차는 기존 개체들로부터 특성을 유지하면서 새로운 개체를 형성하는 과정이다.<br/>
  
  **The main purpose of crossing is the exchange of experience.**<br>
  교차의 주요 목적은 경험을 교환하는 것이다.<br/>
  
  **This approach greatly speeds up finding an acceptable solution.**<br>
  이 접근법은 수용 가능한 해를 찾는 속도를 크게 향상시킨다.<br/>
  
  **Crossover is the next logical action that occurs after selection.**<br>
  교차는 선택 후에 발생하는 다음 논리적인 행동이다.<br/>
<br/>
  ***

## p.2(crossover methods)
  **One-point crossover**<br>
  일점 교차<br/>
  
  **N-point crossover**<br>
  N-점 교차<br/>
  
  **Uniform crossover**<br>
  균일 교차<br/>
  
  **Linear combination crossover**<br>
  선형 결합 교차<br/>
  
  **Blend crossover**<br>
  블렌드 교차<br/>
  
  **Order crossover**<br>
  순서 교차<br/>
  
  **Fitness driven crossover**<br>
  적합도 기반 교차<br/>
<br/>
  ***

## p.3(One-point crossover)
  **a point in a gene sequence is randomly selected by dividing the gene sequence into two parts**<br>
  유전자 서열을 두 부분으로 나누어 유전자 서열에서 한 점을 무작위로 선택한다.<br/>
  
  **New individuals are created by crossing these two parts**<br>
  새로운 개체는 이 두 부분을 교차시켜 생성된다.<br/>

  ![image](https://github.com/user-attachments/assets/a2bd0f46-aefc-41cf-bc11-4540802a8d29)
<br/>
  
  **One-point crossover can be applied to ordered gene and binary bin sets.**<br>
  일점 교차는 순서가 있는 유전자와 이진 집합에 적용될 수 있다.<br/>
  
  **If the gene sequence consists of one element, then a simple exchange of genes between the parents happens, and each of the children is a clone of one of the parents**<br>
  유전자 서열이 하나의 요소로 구성되어 있으면, 부모 간에 유전자가 단순히 교환되고, 각 자식은 부모 중 하나의 클론이 된다.<br/>

  ![image](https://github.com/user-attachments/assets/83248f79-5974-49a4-8e79-8cec75785b5e)
<br/>
 
  **If the gene sequence consists of two elements, then the genes are exchanged in a crisscross way**<br>
  유전자 서열이 두 개의 요소로 구성되어 있으면, 유전자는 교차 방식으로 교환된다.<br/>

  ![image](https://github.com/user-attachments/assets/0886846e-3fcd-40a4-aae4-b4224f72fddf)
<br/>
  ***

## p.6(N-point crossover)
  **N-point crossover is a logical continuation of one-point crossover, but instead of choosing only one point in a gene sequence, N points are selected, and genes are being exchanged in a crisscross way**<br>
  N-점 교차는 일점 교차의 논리적인 연장선으로, 유전자 서열에서 하나의 점만 선택하는 대신 N개의 점을 선택하고, 유전자는 교차 방식으로 교환된다.<br/>

  ![image](https://github.com/user-attachments/assets/bb7e53dc-e640-45c6-943f-487acd393e07)
<br/>
  ***

## p.7(Uniform crossover)
  **Uniform crossover randomly selects some points in the parent’s gene chain, and swaps the genes at these points.**<br>
  균일 교차는 부모의 유전자 체인에서 일부 점을 무작위로 선택하고, 이 지점들의 유전자를 교환한다.<br/>

  ![image](https://github.com/user-attachments/assets/ad134f76-976f-4abb-8a03-35f5be44b3a5)
<br/>
  ***

## p.8(Linear combination crossover)
  **Linear combination crossover is the example of a crossover without any randomness.**<br>
  선형 결합 교차는 무작위성 없이 이루어지는 교차의 예이다.<br/>
  
  **Child genes is a simple linear combination of parent genes**
  자식의 유전자는 부모 유전자의 간단한 선형 결합이다<br/>
  
  - **$(x1 + α|x2 - x1|, x2 – α|x2 - x1|)$, where $α$ is the parameter of linear combination in range $[0, 1]$.**<br>
    $(x1+α∣x2−x1∣,x2−α∣x2−x1∣)$, 여기서 $α$는 선형 결합의 파라미터로 범위는 $[0,1]$이다.<br/>

  **NOTE: If α equals 0 or 1, then children are the same as parents**<br>
  참고: $α$가 0 또는 1이면, 자식은 부모와 동일하다.<br/>
  
  **If α equals 0.5, then we have twins in offspring (both children are the same).**<br>
  만약 $α$가 0.5이면, 자식들은 쌍둥이가 된다(두 자식이 동일하다).<br/>

  **If we want only new individuals to be created, then we can restrict α to this range (0, 0.5)**<br>
  새로운 개체만 생성되기를 원한다면, $α$를 이 범위$(0, 0.5)$로 제한할 수 있다.<br/>

  ![image](https://github.com/user-attachments/assets/522a6a1b-29b1-4a3f-afd6-6f7aa3a4a54b)
<br/>
  ***

## p.10(Blend crossover)
  **Blend crossover method chooses random genes in the range defined by parent genes**<br>
  블렌드 교차 방법은 부모 유전자에 의해 정의된 범위에서 무작위로 유전자를 선택한다.<br/>
  
  **The range for children genes is defined as follows**<br>
  자식 유전자의 범위는 다음과 같이 정의된다:<br/>
  
  - **$[x1 - α(x2 - x1), x2 + α(x2 - x1)]$, where $α$ is the parameter that expands the parent genes range**<br>
    $[x1−α(x2−x1),x2+α(x2−x1)]$, 여기서 $α$는 부모 유전자의 범위를 확장하는 파라미터이다.<br/>

  ![image](https://github.com/user-attachments/assets/0980b28e-b3a1-40a8-8958-7285a5449081) <br>
  ![image](https://github.com/user-attachments/assets/ba18a657-c6f2-4445-a9f6-e9c2b36eccb7)
<br/>
  ***

## p.13(Order crossover)
  **Order crossover is used for ordered genes; the main principle in this approach is to preserve the order of parent genes**<br>
  순서 교차는 순서가 있는 유전자에 사용되며, 이 접근법의 주요 원리는 부모 유전자의 순서를 유지하는 것이다.<br/>
  
  **We will show how this method works with an example:**<br>
  이 방법이 어떻게 작동하는지 예를 들어 보여드리겠습니다:<br/>
  
  - **Say, we have two individuals with ordered genes**<br>
    두 개의 순서가 있는 유전자를 가진 개체가 있다고 가정해봅시다:<br/>
    
    - **Parent 1: (1, 7, 4, 5, 9, 2, 8, 3, 6)**<br>
    - **Parent 2: (3, 1, 5, 4, 9, 8, 6, 2, 7)**
  <br/>
  ![image](https://github.com/user-attachments/assets/b20edc77-d53f-4146-8f72-1cbeec8f3850) <br>
  ![image](https://github.com/user-attachments/assets/91948925-315e-4eab-bb58-7be98a8778a2) <br>
  ![image](https://github.com/user-attachments/assets/f5e4816a-7d81-48bf-8963-b3ad1bdf1740) <br>
  ![image](https://github.com/user-attachments/assets/f2527f5b-a172-497b-83fb-fc4177e4e096)
<br/>
  ***

## p.19(Fitness driven crossover)
  **Fitness driven crossover is an approach that compares the child to the parent and selects the best one**<br>
  적합도 기반 교차는 자식과 부모를 비교하고 가장 좋은 개체를 선택하는 접근법이다.<br/>
  
  **The main principle of this approach is that children should be better than their parents or not at all.**<br>
  이 접근법의 주요 원리는 자식이 부모보다 나아야 한다는 것이며, 그렇지 않으면 자식은 선택되지 않는다는 것이다.<br/>
  
  **In some tasks, the crossing operation is very unpredictable, and carries a high risk of destroying the accumulated positive experience.**<br>
  일부 작업에서는 교차 연산이 매우 예측 불가능하며, 축적된 긍정적인 경험을 파괴할 위험이 크다.<br/>
  
  **Then, as soon as the individuals appear to begin to adapt well to the environment, their genotype can be destroyed after crossing, and as a result, their unique genetic adaptation will be destroyed.**<br>
  그 후, 개체들이 환경에 잘 적응하기 시작하면, 교차 후 그들의 유전자형이 파괴될 수 있으며, 그 결과 고유한 유전적 적응이 파괴될 수 있다.<br/>

  ![image](https://github.com/user-attachments/assets/2d032051-9ddf-4ce5-90e4-f4e84b71f745)
<br/>
  
  **NOTE: You can notice that fitness driven crossover shares the same principle as elite selection which we covered in Chapter 3:**<br>
  참고: 적합도 기반 교차는 우리가 3장에서 다룬 엘리트 선택과 동일한 원리를 공유한다는 것을 알 수 있다.<br/>
  
  **Selection – not to lose valuable individuals.**<br>
  선택 – 가치 있는 개체를 잃지 않기 위해서.<br/>
  
  **And a reasonable question could be: Why not always do this?**<br>
  그리고 합리적인 질문은 이렇게 될 수 있다: 왜 항상 이렇게 하지 않는가?<br/>

  **Why don’t we protect the best ones all the time?**<br>
  왜 항상 최고의 개체들을 보호하지 않는가?<br/>
  
  **Sometimes it makes sense, but evolution is very tricky and unpredictable thing; sometimes it can make one step back and two steps forward.**<br>
  때로는 그럴 때도 있지만, 진화는 매우 교활하고 예측할 수 없는 것이며, 때로는 한 걸음 뒤로 가고 두 걸음 앞으로 나아갈 수 있다.<br/>
  
  **Tiny mammals from the Jurassic period lived on the brink of survival, but after millions of years, this species led to the appearance of human.**<br>
  쥐라기 시대의 작은 포유류들은 생존의 위태로운 지경에 있었지만, 수백만 년이 지난 후, 이 종은 인간의 등장으로 이어졌다.<br/>
<br/>
  ***

## p.22(Key terms)
  **One Point crossover: Exchange of gene “tails”.**<br>
  일점 교차: 유전자 "꼬리" 교환<br/>

  **N-Point crossover: Crisscross gene exchange.**<br>
  N-점 교차: 교차 방식으로 유전자 교환<br/>
  
  **Uniform crossover: Random gene swap**<br>
  균일 교차: 무작위 유전자 교환<br/>.
  
  **Blending crossover: Random gene in range determined by parent genes.**<br>
  블렌딩 교차: 부모 유전자에 의해 결정된 범위 내에서 무작위 유전자 교환<br/>
  
  **Order crossover: Preserving parent genes order.**<br>
  순서 교차: 부모 유전자의 순서 유지<br/>
  
  **Fitness driven crossover: Choosing best between children and parents**<br>
  적합도 기반 교차: 자식과 부모 중 가장 좋은 개체 선택<br/>
<br/>
  
