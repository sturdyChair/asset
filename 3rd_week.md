# 3주차

## 오류 수정

### 보로노이 테셀레이션 최적화  
- 셀 :
  여러 입자들 중 하나의 입자에 대해 가장 가까운 영역  
- 테셀레이션 구현 :
  하나의 입자를 기준으로 정의된 셀에 대해, 또다른 입자와 해당 입자 사이의 선분을 절반으로 나누는 수직 평면을 기준으로 셀을 계속해서 절단  
- 최적화 : 
  테셀레이션 구현 상, 현재 셀을 절단하는 평면과 입자의 거리는 (두 입자 사이의 거리) / 2
  즉, 절단 이전 셀 내에서 입자로부터 가장 멀리 떨어진 점과의 거리보다 입자와 평면 사이의 거리가 더 길면 해당 평면은 셀에 영향을 줄 수 없음  
  ![img](http://github.com/sturdyChair/asset/blob/main/opt.png)
  
### 중복 정점 제거 알고리즘 - 해쉬 충돌
- 기존 알고리즘 :  
  해쉬 태이블을 이용해 중복 제거 => 해쉬 충돌 문제 있음
- 해결 :
  해쉬 충돌 시 정밀한 값 검사를 하도록 알고리즘 수정


---

## 정적 메쉬 파괴  

### 테셀레이션 + 메쉬 불리언
- 메쉬를 포함하는 바운딩 박스에 대한 보로노이 테셀레이션 + 기존 메쉬와 Intersect 연산 => 다양한 모양의 메쉬를 사전 분할 가능

### 물리연산  
  ![img](https://github.com/sturdyChair/asset/blob/main/dynamic_destroy-ezgif.com-video-to-gif-converter.gif)  
- nvidia physx를 이용, 분할된 각 조각을 시뮬레이트 하고 렌더링에 반영  
- 시뮬레이션 결과를 0.25초 간격으로 KeyFrame화 저장, 이진 파일로 출력  
- 출력 결과를 로딩, 물리 엔진 없이 파괴 애니메이션 재생

### 유사 물리 반응
  ![img](https://github.com/sturdyChair/asset/blob/main/Simul_destroy-ezgif.com-video-to-gif-converter.gif)  
- 물리 반응을 하지 않는 콜라이더 생성
- 충격 발생시 위치, 방향, 법선 벡터 계산  
- 시뮬레이트 결과 중 가장 유사한 것을 재생

### 절단면 텍스쳐링
- tri-planar uv mapping :  
  ![img](https://blog.kakaocdn.net/dn/EC6VO/btrQlIg1eRT/4LGlhQf1DrKUKYiH1tHwL0/img.jpg)
  
### TODO
- 속성 조절 기능  
  x, y, z 크기 배율 :
  ![img](https://github.com/sturdyChair/asset/blob/main/Euclidean_Voronoi_diagram_Long.png)  
  조각 결합 : 조각의 최소/ 최대 결합 수치 조정, 인접 조각들이 결합되도록 구현  
- 다른 조각화 방식 구현  

---

## 동적 메쉬 절단
![img](https://github.com/sturdyChair/asset/blob/main/Blademode-ezgif.com-video-to-gif-converter.gif)


### 간선 - 평면 교차 연산  
- 스키닝 연산이 필요하기 때문에 GPU 가속 필수 -> dx11 compute shader 사용
- 입력 정보 :  
  정점, 인덱스, 본 행렬들, 평면
- 출력 정보 :  
  평면 위 정점의 인덱스, 아래 정점의 인덱스, 새로운 정점 정보

### 메쉬 재구성
- 정점 보간
  ![img](https://github.com/sturdyChair/asset/blob/main/lerpVert.png)  
  보간 후 새로운 정점의 Bone weight는 인접 정점을 통해 계산

- pivot 계산  
  평면 위 메쉬 : 절단면 normal 방향으로 pivot

### TODO
- 절단면 구현  
  새로 생긴 정점들 간의 간선 그래프 구성 => cycle 마다 하나의 절단면 생성
  
- 조각 처리





