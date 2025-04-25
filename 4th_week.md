# 4주차

## 정적 메쉬 파괴  

### 프렉쳐 모드  
  <img src="https://github.com/sturdyChair/asset/blob/main/fracturemod%20web.gif" width="600" height="400"/>
  <img src="https://github.com/sturdyChair/asset/blob/main/fracturemod%20comb.gif" width="600" height="400"/>
  <img src="https://github.com/sturdyChair/asset/blob/main/fracturemod%20voxel.gif" width="600" height="400"/>
  
### 내부 머터리얼 선택  
  <img src="https://github.com/sturdyChair/asset/blob/main/material.gif" width="600" height="400"/>

### 프렉쳐 옵션  
- 조각 뭉치기  
  <img src="https://github.com/sturdyChair/asset/blob/main/cluster.gif" width="600" height="400"/>
- 크기 비율  
  <img src="https://github.com/sturdyChair/asset/blob/main/fracture%20scale.gif" width="600" height="400"/>
  
### TODO  
- 단계적 조각 파괴

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
  새로 생긴 정점들 간의 단방향 간선 그래프 구성 => cycle 마다 하나의 절단면 생성
  
- 조각 처리





