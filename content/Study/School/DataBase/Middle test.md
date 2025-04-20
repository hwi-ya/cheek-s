---
created: 2025-04-20
updated: 2025-04-20
dg-publish: true
---

- ## BASIC
    - user DB명 : 해당 DB의 데이터를 조회 하겠다. - 모든 쿼리는 해당 DB에서 실행해라  
    - create table 테이블명 (조건) : 조건대로 테이블을 생성하겠다다

- ## **SELECT**
    - 기본 형식
        ```sql
        select 열이름 from 데이터 명 where 조건식
        ```
    - 열 이름
        - 전체 열 출력 : member라는 데이터의 모든 열(*)을 출력  
          ```sql
          select * from member  
          ```  
            
        - 특정 열 출력 : member라는 데이터에서 mem_name, height, addr열을 출력  
          ```sql
          select mem_name, height, addr from member;  
          ```  
                

    - 조건식
        - 관계 연산자 : height가 162 이상인 데이터를 출력  
          ```sql
          select * from member where height >= 162;
          ```
            - 관계연산자 : >, <, >=, <=, =
        
        - 논리 연산자 1 : height가 165 이상, mem_number가 6 초과인 데이터를 출력  
          ```sql
          select * from member where height >= 165 or mem_number > 6;
          ```

        - 논리 연산자 2 : height가 163 ~ 165인 데이터를를 출력  
          ```sql
          select * from member where height >= 163 and height <= 165;
  
          select * from member where height between 163 and 165;
          ```

        - IN() : addr이 경기, 전남, 경남인 데이터를 출력  
          ```sql
          select * from member where addr = '경기' or addr = '전남' or addr = '경남';
  
          select * from member where addr in ('경기', '전남', '경남');
          ```

        - LIKE 1 : mem_name이 '엔'으로 시작하는 데이터 출력  
          ```sql
          select * from member where mem_name like '엔%';
          ```
            - 첫글자가 엔, 그 뒤는 무엇이든(%) 허용  

        - LIKE 2 : mem_name이 @@핑크인 데이터 출력  
          ```sql
          select * from member where mem_name like '__핑크';
          ```
            - _ 하나당 한글자

        - Subquery : mem_name이 '에이핑크'보다 height가 큰 데이터 출력  
          ```sql
          select * from member
              where height > (select height from member where mem_name = '에이핑크');
          ```
            - select문 앞에 다른 select문이 들어갈 수 있음  
    
    - 정렬
        - order by : debut_date가 빠른 순서대로 출력  
          ```sql
          select * from member order by debut_date;
          ```
            - 뒤에 desc를 붙일 시 내림차순 ex) order by debut_date desc
        - where과 함께 사용 가능
        - heightrk 164이상인 데이터 내림차순
          ```sql
          select * from member where height >= 164 order by height desc;
          ```

    - 개수 제한
        - limit 형식 - limit 시작 개수 : limit 3 = limit 0, 3 -> 0번째 부터 3개 출력  
        - height가 큰 순으로 정렬, 3번째 큰 사람부터 2개 출력  
          ```sql
          select * from member order by height desc limit 3, 2;
          ```
    
    - 중복 제거
        - distinct : 해당 addr 열에서 중복된 데이터 1개만 남기고 출력  
          ```sql
          select distinct addr from member;
          ```

    - 그룹화
        - group by : mem_id별 물품으 총 개수(amount : 집계함수) 출력  
        - 별칭을 사용해 열 이름 변경 가능 ex)mem_id "회원아이디" etc.  
          ```sql
          select mem_id " 회원 아이디", sum(amount) from buy group by mem_id;
          ```
            - 집계함수의 종류
                |function       |Description    |
                |---------------|---------------|
                |sum()          |합계           |
                |avg()          |평균           |
                |min()          |최소값         |
                |max()          |최대값         |
                |count()        |행의 개수       |
                |count(distinct)|행의 개수(중복X)|
        
        - having : mem_id별 총 구매 금액이 1000 이상인 회원, 구매 금액이 작은 순으로 출력  
          ```sql
          select mem_id, sum(amount * price) from buy 
              group by mem_id having sum(amount * price) >= 1000 order by sum(amount * price) desc;
          ```

- ## **INSERT, UPDATE, DELETE**
    - 각각 입력, 수정, 삭제  

    - insert
        ```sql
        insert into 테이블명 (열이름1, 열이름2, ...) values (값1, 값2, ...)
        ```
        - 열이름은 생략 가능 (단, 생략할 경우 값의 순서, 개수는 열 순서 및 개수와 동일 해야함)  
        - 열의 순서를 바꿔서 입력 가능 ex) 열 1, 열 3, 열 2 value 값 1, 값 3, 값 2 etc.  
        
        - auto_increment : 열을 정의할 때 1부터 증가하는 값을 입력  
          - insert into를 사용할 때 해당 열은 없다고 생각하고 입력  
          - 주의사항 : auto_increment열은 Primary_Key여야함  
          ```sql
          insert into toy2 values (null, '우디', 8);
          insert into toy2 values (null, '버즈', 9);
  
          insert into toy2 values (null, '우디' 8), (null, '버즈' 9)
          ```
            입력시 실행결과  
            |toy_id|toy_name|age|
            |------|--------|---|
            |1     |우디     |8  |
            |2     |버즈     |9  |
          - 만약 auto_increment를 100부터 시작하고 싶다면  
            ```sql
            alter table toy2 auto_increment = 100;
            insert into toy2 values (null, '제시', 8)
            ```
            입력시 실행결과  
            |toy_id|toy_name|age|
            |------|--------|---|
            |1     |우디     |8  |
            |2     |버즈     |9  |
            |100   |제시     |8  |
            - 만약 auto_increment를 1000으로 지정하고 3씩 증가하게 하고싶다면  
            ```sql 
            alter table toy2 auto_increment = 1000;
            set @@auto_increment_increment = 3;
            ```

    - update
        ```sql
        update 테이블명 set 열1 = 값1, 열2 = 값2, ... where 조건식
        ```
        - city_name중 Tokyo를 도쿄로 변경  
          ```sql
          update japan set city_name = '도쿄' where city_name 'Tokyo';
          ```

        - city_name중 나고야를 Nagoya로 population을 0으로 변경  
          ```sql
          update japan set city_name = '나고야', population = 0 where city_name = 'Nagoya';
          ```

        - where절은 문법상 생략가능 단, 생략시 모든 행에 적용  
        - city테이블의 popualtion의 단위를 1단위가 아닌 10000단위로 수정  
          ```sql
          update city set population = population/10000;
          ```
    
    - delete
        ```sql
        delete from 테이블명 where 조건식;
        ```

        - country가 new로 시작하는 행 삭제
          ```sql
          delete from city where country like 'new%';
          ```

- ## **데이터 형식**
    - 정수형
      |데이터 형식|바이트 수|숫자 범위        |
      |----------|--------|-----------------|
      |tinyint   |1       |-128 ~ 127       |
      |smallint  |2       |-32768 ~ 32767   |
      |int       |3       |약 -21억 ~ 21억  |
      |bigint    |4       |약 -900경 ~ 900경|
        - unsigned 사용시 값의 범위가 0부터 시작 
        - ex) tinyint unsigned : -128 ~ 127 -> 0 ~ 255

    - 문자형
      |데이터 형식  |바이트 수 |
      |------------|---------|
      |char(max)   |1 ~ 255  |
      |varchar(max)|1 ~ 16383|
        - char : character, 고정 길이 문자형
            - 자릿수가 고정되어 char(10)에 ㄱㄴㄷ 3글자를 저장해도 10자리를 확보해 7자리 낭비
        - varchar : variable character, 가변 길이 문자형
            - varchar(10)에 ㄱㄴㄷ 3글자를 저장한다면 3자리만 사용

    - 대량 데이터 : char, varchar보다 더 큰 데이터를 저장하기 위해 사용용
      | 데이터 형식 |          | 바이트 수             |
      |-------------|----------|----------------------|
      | text 형식   | TEXT     | 1 ~ 65,535           |
      |             | LONGTEXT | 1 ~ 4,294,967,295    |
      | blob 형식   | BLOB     | 1 ~ 65,535           |
      |             | LONGBLOB | 1 ~ 4,294,967,295    |
        - blob은 글자가 아닌 이미지, 동영상 등의 데이터를 저장함

    - 실수형
      |데이터 형식|바이트 수|설명             |
      |----------|--------|-----------------|
      |float     |4       |소수점 아래 7자리 |
      |double    |8       |소수점 아래 15자리|

- ## **TABLE, CONSTRAINTS**
    - 데이터베이스 생성
      ```sql
      create database DB명;
      ```

    - 데이터베이스 삭제
      ```sql
      drop database DB명;
      ```

    - constraints
        - 데이터의 무결성을 지키기 위해 제한하는 조건
          |제약조건의 종류|
          |--------------|
          |Primary Key   |
          |Foreign Key   |
          |Unique        |
          |Check         |
          |Defult        |
          |Null값 허용    |

        - Primary Key(기본키)
            - 테이블은 기본키를 1개만 가질 수 있음, 중복 불가, Null 불가
              ```sql
              mem_id char(8) not null primary key
  
              primary key (mem_id);
              ```

        - Foreign Key(외래키)
            - 두 테이블 사이의 관계 연결 기본키 : 기준 테이블, 외래키 : 참조테이블
            - 참조 테이블이 참조하는 기준 테이블의 열은 반드시 기본키 or 고유키로 설정 되어야 함
              ```sql
              foreign key (mem_id) references member(mem_id);
              ```
        
        - Unique(고유키)
            - 중복되지 않는 유일한 값을 입력해야함, null값 허용, 여러개 설정 가능
              |     |기본키                                        |고유키                                    |
              |-----|---------------------------------------------|------------------------------------------|
              |공통점|테이블 내 레코드를 구분하기 위해 사용됨                                                    |
              |차이점|- 하나의 테이블에 하나의 기본키<br> - null 불가|- 하나의 테이블에 여러 고유키<br> - null 허용|
                ```sql
                alter table member
                    add constraint
                    unique (phone2);
                ```

        - **check(체크)**
            - 입력되는 데이터를 점검
            - height열에 300보다 큰 값이 입력되지 않도록 제약하기
              ```sql
              alter table member
                  add constraint
                  check (height <= 300);
              ```
            - phone1에 02, 031, 063중 하나만 입력되게 제약하기
              ```sql
              alter table member
                  add constraint
                  check (phone1 in ('02', '031', '063'));
              ```

        - Default(기본 값 정의)
            - 값을 입력하지 않았을 때 자동으로 입력될 값 지정
            - 키를 입력하지 않고도 160이라고 입력되게 지정하기
              ```sql
              alter table member
                  alter column phone1 set default '02';
              ```

- ## **JOIN**
    - **내부 조인은 두 테이블 모두 있는 내용만 조인됨 한 테이블에만 내용이 있을 시 외부조인 사용**
    - join이란 두 개의 테이블을 묶어 하나의 결과를 만들어 내는 것
    
    - **inner join**
        - one to many
            ```sql
            select 테이블명.열이름름 from 첫번째 테이블
                inner join 두번째 테이블 on 조인 될 조건
                where 조건식
            ```
            - buy 테이블에서 GRL이라는 mem_id를 가진 사람의 정보를 member에서 조회하여 함께 출력하기
              ```sql
              select * from buy b 
                  inner join member m
                  on b.mem_id = m.mem_id
                  where b.mem_id = 'GRL';
              ```
                - buy b = buy를 b라 칭하겠다(이렇게 테이블 이름에 별칭을 줄 수 있음)
            - mdm_id, mem_name, prod_name, addr을 출력하되 mem_id의 오름차순으로 정렬하기
              ```sql
              select b.mem_id, m.mem_name, b.prod_name, m.addr from buy b 
                  inner join member m
                  on b.mem_id = m.mem_id
                  order by b.mem_id;
              ```

    - **outer join**
        ```sql
        select 테이블명.열이름 from 첫번째 테이블(left테이블)
            <left | right | full> outer join 두번째 테이블(right테이블)
            on 조인 될 조건
            where 조건식
        ```
        - **left outer join**은 왼쪽 테이블의 내용은 모두 출력되어야 한다
            |Left table|Right Table        |
            |----------|-------------------|
            |전부 출력  |조건에 맞는 것만 출력|

            - mem_id, mem_name, prod_name, addr을 출력하되 mem_id의 오름차순으로 정렬하기
              ```sql
              select m.mem_id, m.mem_name, b.prod_name, m.addr from member m
                  left outer join buy b
                  on m.mem_id = b.mem_id
                  order by m.mem_id;
              ```

        - **right outer join**은 오른른쪽 테이블의 내용은 모두 출력되어야 한다
            |Left table         |Right Table|
            |-------------------|-----------|
            |조건에 맞는 것만 출력|전부 출력  |

            - mem_id, mem_name, prod_name, addr을 출력하되 mem_id의 오름차순으로 정렬하기
              ```sql
              select m.mem_id, m.mem_name, b.prod_name, m.addr from member m
                  right outer join buy b
                  on m.mem_id = b.mem_id
                  order by m.mem_id;
              ```

            - 회원 가입만 하고, 한 번도 구매한 적 없는 회원 목록을 추출
              ```sql
              select distinct m.mem_id, m/=.mem_name, b.prod_name, m.addr from member m
                  left outer join buy b
                  on m.mem_id = b.mem_id
                  where b.prod_name is null;
              ```
