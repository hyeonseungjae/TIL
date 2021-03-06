
### 정규화
관계형 데이터베이스 설계시 중복을 최소화하여 데이터를 구조화 하는 작업.

데이터의 상태 이상이 있는 관계를 재구성 함으로써 올바른 스키마 구축


#### 1. 제1정규형
- 중복이 있는 항목이 없어야 한다. 

![](/img/db1.png)
- 4번째 전화번호를 넣을수 없음.
- 전화번호의 질의를 3개의 컬럼에 조건절을 해야함
- 중복된 전화번호가 들어갈수 있음

###### 해결
![](/img/db2.png)


- 도메인은 원자값으로만 되어야 한다. (하나의 칼럼에 여러값이 들어가면 안됨, 혹은 같은 정보의 칼럼이 여러개면 안됨)
![](/img/db7.jpeg)



#### 2. 제2정규형
- 부분 종속성 관계를 없앤다.

![](/img/db3.png)
- 종업원과 기술의 관계에서 종업원과 근무지가 종속석을 가진다. (중복되어 들어간다)

##### 해결
![](/img/db4.png)


- 키에 속하지 않은 속성 모두가 키에 완전 함수 종속, (row별로 중복되는 값이 없어야 한다.)
![](/img/db9.jpeg)
![](/img/db10.jpeg)

#### 3. 제3정규형
- 이행 함수적 종속 (x->y->z 관계) 제거

![](/img/db5.png)
- 대회+연도로 유니크키 가능, 대회+연도+우승자로 정규화 가능 , 우승자->우승자생년월일 관계, x->y->z 관계

##### 해결
![](/img/db6.png)

- 속성들이 함수종석이 아닐때, x(학생)->y(지도교수), y(지도교수)->z(학과) 일떄 해당 종속성을 나눔
![](/img/db11.jpeg) 
![](/img/db12.jpeg)


#### 4. BCNF 보이스/코드정규형
- 릴레이션 R이 제3정규형을 만족하고, 모든 결정자가 후보키이어야 한다.

![](/img/db13.jpeg)
![](/img/db14.jpeg)
