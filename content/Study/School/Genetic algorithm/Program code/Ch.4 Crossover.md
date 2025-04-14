---
created: 2025-03-30
updated: 2025-03-30
dg-publish: true
---

- ## One-point
    
    ```python
    import copy
    import random
    
    # 일점 교차 함수 정의
    def crossover_one_point(p1, p2):
        # 교차 지점을 무작위로 선택 (1부터 부모의 길이-1까지)
        point = random.randint(1, len(p1) - 1)
        
        # 부모 개체들을 깊은 복사하여 자식 개체를 생성
        c1, c2 = copy.deepcopy(p1), copy.deepcopy(p2)
        
        # 부모의 유전자 순서를 교환하여 자식 개체 생성
        c1[point:], c2[point:] = p2[point:], p1[point:]
        
        # 자식 개체 두 개 반환
        return [c1, c2]

        # 랜덤 시드를 고정하여 재현성 있는 결과를 얻음
        random.seed(2)
        
        # 부모 개체 1과 부모 개체 2를 무작위로 생성 (길이 5)
        p1 = [random.randint(0, 9) for _ in range(5)]
        p2 = [random.randint(0, 9) for _ in range(5)]
        
        # 교차 연산을 통해 자식 개체 생성
        offspring = crossover_one_point(p1, p2)
        
        # 부모와 자식 개체 출력
        print(f'Parent 1: {p1}')
        print(f'Parent 2: {p2}')
        print(f'Child 1: {offspring[0]}')
        print(f'Child 2: {offspring[1]}')
    ```
    
    - Result<br>
          <img src="https://github.com/user-attachments/assets/99244d75-5d0b-4cb8-93c8-a698e4c1766d" width="411" height="150"/>

<br>
<hr>
<br>
        
