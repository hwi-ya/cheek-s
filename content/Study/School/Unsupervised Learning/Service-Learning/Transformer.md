---
created: 2025-04-17
updated: 2025-04-17
dg-publish: true
---

- ## Transformer
  - **Transformer?**  
      - 시퀀스 데이터를 처리하기 위한 딥러닝 모델 아키텍처  
      - 2017년 **"Attention is All You Need"** 라는 논문에서 처음 소개됨<br/>
  <br/>

  - **공부하기 전 알아야 할 내용**     
      | What?                    | Why?                                                                 |
      |--------------------------|----------------------------------------------------------------------|
      | **Self-Attention**       | - 쉽게말하면 Transformer는 Self-Attention의 집합체이기 때문            |
      | Deep Learning            | - MLP, Loss, Optimizer 등의 기본구조는 알고 가는게 좋음                |
      | Linear Algebra           | - Transformer, Self-Attention은 모든 연산이 행렬 기반이기 때문에       |
      | Probability & Statistics | - Self-Attention에서 Attention Score를 확률로 바꿀 때 사용하기 위해    |
<br/>
<br/>

  - **공부하는 이유**  
      **저도 몰라요 하기 싫어요 응!애!**
<br/>
<hr>

- ## Self-Attention
  - **Self-Attention?**  
      - 자신이 시퀀스의 다른 모든 요소들과 **얼마나 관련이 있는지** 를 계산해서 그에 따라 정보를 가중합하여 표현을 갱신하는 방식<br/>
<br/>

  - **Self-Attention의 흐름**  
      - **1. 입력 데이터를 고정된 차원의 벡터 시퀀스로 변환한다**  
         - 입력데이터(문장, 이미지등) 임베딩하거나 패치로 나눠 벡터 형태의 시퀀스 데이터로 변환
         
      - **2. 각 레이어에 가중치 행렬을 곱해 Query, Key, Value값을 만든다**  
         - 각각의 입력 벡터를 서로 다른 3개의 가중치 행렬과 곱해 Query, Key, Value 벡터를 생성한다
         - 여기서 가중치 행렬은 랜덤으로 정해진다.
         
      - **3. query, key의 dot product(유사도)를 통해 attention score를 계산한다**  
         - attention score : 유사도를 수치화한 것
         
      - **4. attention score를 softmax를 사용해 정규화를 한다**  
         - dots가 음수가 나올 수도 있음 - 이 경우에는 지수함수를 곱해줘 양수화 한다
         - 계산된 score들을 softmax 함수를 통해 0~1 사이의 값으로 정규화하여 가중치로 만든다
         - softmax란?
           - 여러 개의 숫자를 확률처럼 해석 가능한 값들로 바꿔주는 함수

      - **5. 이 정규화된 값의 value를 가중합 한다**  
         - 각 Query는 전체 Value들을 해당 가중치만큼 곱해서 문맥을 반영한 새로운 벡터로 만든다
        
      - **6. 가중합 해서 나온 결과 벡터를 출력한다**  
         - 이 가중합 결과가 Self-Attention의 출력이며, 다음 레이어로 넘어가거나 최종 결과로 사용된다
         - Transformer에서는 새로운 Self-Attention으로 넘어가 새로운 결과벡터를 만들어낸다.
  


    
      
      
