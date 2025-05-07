---
created: 2025-05-07
updated: 2025-05-07
dg-publish: true
---

## p.1(Other Common Problems)
  **Structure**  
  구조.<br/>
  - System of equations  
    연립방정식.<br/>
  - Graph coloring problem  
    그래프 색칠 문제.<br/>
    
  **Objective**  
  목적.<br/>
  - To get familiar with other types of problems  
    다른 유형의 문제에 익숙해지기 위해.<br/>
<br/>
  <hr>

## p.2(System of equations)
  **In real life, problems often arise that lead to the appearance of a system of equations**  
  실생활에서는 연립방정식이 나타나는 문제가 자주 발생한다.<br/>
  
  **Moreover, this equation system can be very complicated, and sometimes, it cannot even be analytically solvable**  
  게다가 이 연립방정식은 매우 복잡할 수 있으며, 때로는 해석적으로 풀 수 없기도 하다.<br/>
  
  **Methods of finding solutions based on genetic algorithms are very well suited for such problems.**  
  이러한 문제에는 유전 알고리즘 기반의 해법 탐색 방법이 매우 적합하다.<br/>

  **Let us have a system of equations:**  
  연립방정식을 살펴보자.<br/>

  $$
  \begin{cases}
  f(x, y, z) = 0 \\
  g(x, y, z) = 0 \\
  w(x, y, z) = 0
  \end{cases}
  $$

  **As we remember, (x, y, z) satisfies the system of equations, if and only if (x, y, z) satisfies the equation:**  
  기억하듯이, (x, y, z)가 연립방정식을 만족하는 것은 오직 (x, y, z)가 다음 방정식을 만족할 때이다.<br/>

  $$
  \lvert f(x,y,z)\rvert + \lvert g(x,y,z)\rvert + \lvert w(x,y,z)\rvert = 0
  $$

  **Therefore, all we need to do is find the points at which the function:**  
  따라서 우리가 해야 할 일은 다음 함수가 영점을 갖는 지점을 찾는 것이다.<br/>

  $$
  f(x, y, z) = \lvert f(x,y,z)\rvert + \lvert g(x,y,z)\rvert + \lvert w(x,y,z)\rvert = 0
  $$

  **or find the minimum of this function**  
  또는 이 함수의 최솟값을 찾는 것이다.<br/>

  **Let’s try to solve the following system of equations in integers:**  
  다음 연립방정식을 정수 해로 풀어보자.<br/>
  
  $$
  \begin{cases}
  (xy + 2)x^2 + (x + y)^{\lvert z - 2\rvert^3 + 2} + xyz = 0 \\
  x\,(yz + 10) - \lvert z - 3\rvert! + y^{\lvert x\rvert} + 11z = 0 \\
  (x + 7y)^{\lvert z + x\rvert} - (z + 16)^2 - 151 = 0
  \end{cases}
  $$
<br/>
  <hr>
  
## p.5(Graph coloring problem)
  **As we remember, the graph is some structure with vertices and edges connecting them**  
  기억하듯이, 그래프는 정점들과 이들을 연결하는 간선들로 이루어진 구조이다.<br/>

  <img src="https://github.com/user-attachments/assets/425e5df6-bf1c-49b9-8569-c2c36fe6c3f9" width="280" height="300"/> <br/>

  **A large number of problems from game theory, chemistry, biology, and social networks analysis are formulated as graph theory problems**
  게임 이론, 화학, 생물학, 소셜 네트워크 분석 분야의 많은 문제가 그래프 이론 문제로 공식화된다.<br/>
  
  **One of the important subclasses of graph theory problems is the graph coloring problem**  
  그래프 이론 문제의 중요한 하위 범주 중 하나는 그래프 색칠 문제이다.<br/>

  **The graph coloring problem is formulated as follows – for a given graph, it is necessary to color its vertices with some colors to satisfy the specified condition.**  
  그래프 색칠 문제는 다음과 같이 정식화된다 — 주어진 그래프에 대해 특정 조건을 만족하도록 정점들을 몇 가지 색상으로 색칠해야 한다.<br/>
  
  **Let's solve the following graph coloring problem**  
  다음 그래프 색칠 문제를 풀어보자.<br/>
  
  **It is necessary to color the graph vertices from figure 11.1 using three colors, so that there will be no single pair of adjacent vertices with the same color.**  
  그림 11.1의 정점들을 세 가지 색으로 색칠하여 인접한 정점 쌍에 같은 색이 없도록 해야 한다.<br/>

  <img src="https://github.com/user-attachments/assets/2445e199-a8c6-4ba2-bf18-1629384ad00b" width="272" height="300"/> <br/>
  - Graph Coloring Problem Example  
    그래프 색칠 문제 예제.<br/>

  **Well, the solution used in the preceding figure doesn't seem that difficult, does it?**  
  음, 앞 그림에서 사용된 해법은 그다지 어렵지 않아 보인다.<br/>

  **It is relatively easy to solve this problem without using any additional tools**  
  이 문제는 추가 도구 없이 해결하는 것이 비교적 쉽다.<br/>
  
  **Then let's try to examine the graph with 30 vertices in the following figure**  
  그러면 다음 그림의 30개의 정점이 있는 그래프를 살펴보자.<br/>

  <img src="https://github.com/user-attachments/assets/2eed3bc2-9bcb-4450-9cf8-0d6ef41160ab" width="381" height="400"/> <br/>
  - Vertices Graph for Graph Coloring Problem  
    그래프 색칠 문제를 위한 정점 그래프.<br/>

  <img src="https://github.com/user-attachments/assets/b7c2d5c3-c80e-4615-8fc3-78594d417ea8" width="381" height="400"/> <br/> 
  - Random Individual for Gragh Coloring Problem  
    그래프 색칠 문제를 위한 랜덤 개체.<br/>

  **Let’s build a genetic algorithm solving graph coloring problem,**  
  그래프 색칠 문제를 해결하는 유전 알고리즘을 구축해보자.<br/>
  
  **We use rank selection with elite, 2-point fitness driven crossover, and fitness driven random change mutation**  
  우리는 엘리트를 포함한 순위 선택과 2점 적합도 기반 교차, 그리고 적합도 기반 무작위 변경 돌연변이를 사용한다.<br/>
  
  **Random change mutation is a simple random choice of one of three colors**  
  무작위 변경 돌연변이는 세 가지 색 중 하나를 단순히 무작위로 선택하는 것이다.<br/>
  
  **It means that a random gene in the gene list will be changed to a random color**  
  이는 유전자 리스트의 임의의 유전자가 무작위 색상으로 변경된다는 것을 의미한다.<br/>

  <img src="https://github.com/user-attachments/assets/753a83f6-adb7-4ba6-b2fe-a913824745a1" width="397" height="400"/> <br/>
  - Solution of Graph Coloring Problem  
    그래프 색칠 문제의 해답.<br/>









  
  
